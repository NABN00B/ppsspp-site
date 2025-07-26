# Creating texture replacement packs

## Dumping your textures

You can create texture replacement packs in PPSSPP to replace textures.

(If you're looking for information on how to use existing texture packs instead of how to create new ones, [click here](/docs/reference/use-texture-replacement).)

Anyway, start by creating a textures.ini file. This can be done automatically: Just load up your game, press ESC and go into settings, tools, developer tools, texture replacement, and choose "Create/Open textures.ini file for your game".

In the ini file, you should probably set hash="xxh64" and ignoreAddress="true" for the best tradeoff between robustness and speed.

Then enable "Save textures" and play the game to get the textures dumped. They'll collect in the "new" subfolder in your texture pack. Then move them out from there into the main texture pack folder, or in subfolders if you create ini file entries for them, see below. Then you can start editing them.

When you restart the game now with texture replacement enabled, they should show up.

## Supported image file formats

When saving textures, they'll be written to disk in png format. While png is okay, it's not the fastest to load, plus it decompresses to full RGBA8888 format in video memory, which is a little wasteful.

From 1.15, PPSSPP supports multiple efficient GPU-native [texture compression formats](https://en.wikipedia.org/wiki/Texture_compression). Here's the current list:

* .KTX2 file format: Basis and UASTC universal compression formats, only!
* .DDS file format: BC1, BC2, BC3, BC7 (BC1-3 is equivalent to DXT1, DXT3, DXT5). These formats don't work on mobile!

Basis and UASTC are "intermediate" formats that can be efficiently transcoded to
commonly supported native formats (BC1 and ETC2 in case of Basis, BC7 and ASTC 4x4 in case of UASTC). The main advantage is of course that the same texture pack can work on both mobile and desktop with this technology.

PPSSPP also has a native ".zim" format which is similar to .png but much faster to load. However given the above, it's no longer very useful. If you do want to use it, see [link](https://github.com/hrydgard/ppsspp/issues/12332#issuecomment-846764577).

If you want to stick with .png for compatibility with very old PPSSPP versions, or just the ease of use, using pngquant / pngyu to reduce the size of PNGs will also make PNG files load faster. See [this ost](https://github.com/hrydgard/ppsspp/issues/12059#issuecomment-1436104606) for reference.

### Texture compression tools and recommendations

I recommend using UASTC files in general. Basis makes sense for RGB-only (no alpha) textures that don't need to be highly detailed - you'll save some additional disk space and VRAM with those.

The tool for creating these files is called basisu. A windows version, basisu.exe, can be downloaded [from here](https://github.com/BinomialLLC/basis_universal/releases).

For other platforms, there might be a package, or you'll have to build the tool on your own. On Mac, for example, `brew install basisu` works.

Recommended command lines to compress two images, one to UASTC and the other to Basis (will result in same-named .ktx2 files next to the originals):

```bash
basisu -uastc -mipmap -ktx2 my_transparent_or_hq_image.png
basisu -mipmap -ktx2 my_solid_lower_quality_image.png
```

Quick Windows command to convert a directory recursively (put `basisu.exe` in your path) by [LunaMoo](https://github.com/hrydgard/ppsspp/issues/12059#issuecomment-1474975884):

```bash
for /r %%v in (*.png) do basisu "%%v" -ktx2 -uastc -mipmap -output_path %%~dpv
pause
```

`basisu` is rather strict when reading png files, see [this issue](https://github.com/BinomialLLC/basis_universal/issues/270). If your png files won't convert, could try to rewrite them using imagemagick, pngopt, XnConvert or any other image processing software.

For textures that are not supposed to wrap around (like title screens, menu pieces and stuff), also pass the flag `-mip_clamp` for optimal results. basisu has a large number of set of parameters that can be experimented with.

Then just refer to the .ktx2 files instead of .png files in the ini. You can delete the png files after compressing to ktx2, or keep them around if you want, but you don't have to ship them in your pack if you ship the ktx2 files. Note that both these formats are somewhat lossy so if you plan further editing, keep the .png files around somewhere.

### Limitations and properties of KTX2/DDS compressed texture formats

* These formats are supported in PPSSPP 1.15 or later only.
* Basis is RGB-only, no alpha (but consumes half the memory - just 0.5 bytes per pixel). It also generally doesn't look very good, so only use on textures where you don't need the best quality.
* UASTC supports full RGBA at excellent quality, not far from native BC7 or ASTC. The data size is bigger than basis though at 1 byte per pixel. Still a huge win over raw RGBA with 4 bytes per pixel...
* DDS will load marginally faster than KTX2 since no transcoding is needed, but these formats are generally not supported on mobile. So there's a tradeoff.
* UASTC is not natively supported on D3D9 or OpenGL ES 2.0, it will be transcoded to raw RGBA, eating up the benefits (still usable though).

#### Thumbnails in Windows Explorer

If you want to see thumbnails for KTX2 textures in Explorer, try the [Kram thumbnailer](https://github.com/alecazam/kram/tree/main/kram-thumb-win). (note: I have not tested this yet)

## Basic structure

```ini title="textures.ini"
[options]
# 1 is the only version, as of writing
version = 1
# 'quick' is the default hash.  Other options: xxh32, xxh64 (better hashes, but slower)
# ALL hashes will change if you change this option, so pick one at the beginning and stick with it.
hash = xxh64
ignoreAddress="true"

# By default, a file with .png at the end of the hash is used.
# Override below to share filenames or use custom filenames.
# To skip a texture (like videos) use a blank filename on the right side.
# Syntax: hash = filename.png
[hashes]
# Ignore the intro video textures.
099bf1c000000909 =
0993698000000909 =
09a47a0000000909 =
09ad024000000909 =
# Water animation.
099c0db096c0500ecd2f3e6e = water/frame1.ktx2
099c2db0d26dc9a7966195cf = water/frame2.ktx2
099c4db0fa2cbcfec0bd3e0f = water/frame3.ktx2
099c6db0d17d9a67c7591d4f = water/frame4.ktx2
# This texture is loaded at two addresses.  The content is the same.
094b89907dcca1a5ee284131 = 094b5a707dcca1a5ee284131.png
# Alias the extra mip level too.
094b89907dcca1a5ee284131_1 = 094b5a707dcca1a5ee284131_1.png

# This allows customizing the range of a texture that is hashed.
# Careful: sometimes the same address is reused later for a texture that needs more hashing.
# Syntax: address,w,h = w,h
[hashranges]
# Force the intro video to hash 480x272.
0x09936980,512,512 = 480,272
0x099bf1c0,512,512 = 480,272
0x09a47a00,512,512 = 480,272
0x09ad0240,512,512 = 480,272
# Clip logos to actual texture size.
0x090056d0,256,256 = 176,160
0x0900c4d0,256,64 = 208,56

[filtering]
# You can enforce specific filtering modes with this. Available modes are linear, nearest, auto. See the docs.
# Example: 08d3961000000909ba70b2af = nearest
```

## Compatibility with Windows, Android, Linux, Mac, etc.

If you're making a texture pack for others to use - that's great.  Otherwise, ignore this section.

Filenames are the tricky part here.  Specifically:

* Always use `/` not `\` for directories.  All platforms (even Windows) support `/`, but `\` doesn't work anywhere but Windows.
* Always use lowercase filenames.  On Windows and Mac, "Hello.png" is the same as "hello.png", but that's not the case everywhere.  Using only lowercase is safest.
* Avoid special characters: Windows doesn't support a bunch, and they can cause problems for others too.

If you follow those guidelines, even more people will be able to appreciate your hard work.

## Texture sizes on the PSP

TL;DR: Some things are hard for robots, and easy for humans.  Unfortunately this makes replacing textures harder and more annoying.

The PSP hardware limited textures to power-of-two sizes, so games always use those sizes (e.g. 512x512 or 512x256.)

When a game wants to show a full screen image (480x272), it has to use a texture that's 512x512, because the PSP hardware just can't process a texture actually 480x272 in size.  And the extra space that isn't used?  The game doesn't care - it usually has garbage.

Unfortunately, this means that hashes may be different even though any human (sorta like a captcha) could obviously tell they are identical.  It's often very difficult for PPSSPP to detect this: sometimes 512x512 images are sprite sheets, fonts, or just scaled down.  And it happens with smaller images (even 32x64) too.

Workaround: you can add `reduceHash = True` under `[options]` (this cannot be used with `hash = quick`.  This will just ASSUME that only the top half of any texture is important.  If a game draws text a letter at a time into a texture or ever changes the bottom half, this will definitely break drawing in those cases.  And if you run into this... your only option will be to start over from scratch (with `reduceHash` off), or live with the brokenness.  You've been warned.

## Parts of the hash

The hash simply uses the same hashing PPSSPP internally uses to tell textures apart.  Aside from a hash of the image data, it also uses the hash of the palette (for palette-swapped images), and the address of image in memory.

Keep in mind that the `quick` hash especially is not perfect.  If you rely only on it, you might find yourself replacing a completely unrelated texture by accident (oops.)  Decide your risk carefully.

It's possible to ignore some of these parts, but if you do, don't use `hash = quick`.  Here are the options (includes mipmap levels, see below):

```ini
[hashes]
# Address + CLUT (palette) + data hash + mipmap level 0.
094b89907dcca1a5ee284131_0 = very/organized/things/texture1.ktx2

# Level defaults to 0.
094b89907dcca1a5ee284131 = very/organized/things/texture2.png

# Ignore the texture with this CLUT regardless of data.
094b89907dcca1a500000000_0 =

# The same CLUT / data at any address:
000000007dcca1a5ee284131 = very/organized/things/texture3.ktx2

# The same address / data with any CLUT:
094b899000000000ee284131 = very/organized/things/texture4.dds

# The same data at any address (collisions might happen):
0000000000000000ee284131 = very/organized/things/texture3.ktx2
```

## Mipmaps

Mipmapping is a technique games use to make faraway (shrunk) textures look better.

Imagine you have a HD (1920x1080) image of a car, but that car is very far away.  It's so far away, that on your screen, it's only 19x11 pixels (1%.)

Because of how GPUs work, they're going to only pick a few random pixels from the 1920x1080 image to draw on screen.  You might get unlikely, and these could all be from the tail-lights.  Then the "car" would just become a red blur when it's far away (even if the actual car is black.)

Mipmapping fixes this by giving the GPU smaller images for farther away.  Some, but not all, PSP games use these.

The "original size" image is "mip level 0", and every size after that must be *exactly* half the width and height.  So, if "mip level 0" is 1920x1080, then "mip level 1" should be 960x540.

```ini
094b89907dcca1a500000000_0 = mip_level_0.png
094b89907dcca1a500000000_1 = mip_level_1.png
094b89907dcca1a500000000_2 = mip_level_2.png
# etc.
```

KTX2 and DDS files can include multiple mipmaps in one file. See the section about texture image formats below. I recommend using KTX2 files as much as possible.

You don't need a full set of mip levels.  Even a few will often help, especially if the player has anisotropic texturing enabled.

## Filter mode override

As documented in the ini file example above, texture filtering can be overridden on a per-hash basis. This works even if you don't actually replace the texture. This can be useful for enforcing nearest filtering on thing that look good pixellated, for example.

## Zipped texture packs

You can install zipped texture packs directly, there's no need to unzip them. This will even improve performance, especially if you zip without compression (images are generally already compressed, compression on top of compression doesn't do much good).

## Thumbnails in Windows

It can be a bit annoying that KTX2 files don't have thumbnails in the Windows Explorer. There now exists a plugin to fix that: https://github.com/alecazam/kram/tree/main/kram-thumb-win . I will try to compile and upload it here soon.

## More info

See [#8715], [#8792], [#4630], and [#9668].