---
position: 6
---
# Save data and storage on Android

PSP save data storage on Android 11+ with PPSSPP 1.12+ is a bit more complicated than it used to be, due to the new Android restrictions that we have to abide by.

[Jump directly to setup instructions](#setup)

## Background - how the PSP stores data

The real PSP stores savedata and downloaded game demos and similar on something called a "Memory Stick", basically a micro-SD, though a bit bigger physically. To simulate this storage, PPSSPP uses a regular folder on your file system. In the case of Android, traditionally PPSSPP has simply used the root of what's called "External storage", the storage you can [access directly via USB](docs/getting-started/installing-games-android).

In Android 11, 12 and later, PPSSPP (like other apps) is no longer able to just ask for wide permission to read/write to your device external storage. Instead, it has to ask for your permission to write to a folder on a per-folder basis. The exception is if you upgraded from an earlier version, or if you're on Android 11 and use PPSSPP 1.11 or earlier and are on Android 11 (since older versions of PPSSPP didn't target Android 12, it's excepted from the rules on Android 11, for complicated reasons).

To this end, on startup, PPSSPP will ask you to choose or create a folder for PSP data storage. If you don't, PPSSPP will have to resort to storing PSP savedata and similar in what's called the app's "External Files" folder, which is located in /Android/Data/org.ppsspp.ppsspp, or /Android/Data/org.ppsspp.ppssppgold.

## <a name="setup"></a>Recommended setup

The setup I recommend is to simply create a PSP folder at the root of your storage. Note that this doesn't mean you have to store your ISO/CSO files here, they can be anywhere or in multiple locations - not a problem.

Here's a step by step guide for how to create the folder:

First, when PPSSPP starts (or later in Settings/System/Memory Stick Location), choose "Create or use existing folder". You'll get the below folder picker. (If you don't, and instead get a red error message, [click here](/docs/troubleshooting/cant-pick-folder)).

Make sure you're in the root of storage - you can see this since it'll say "Can't use this folder".

If you already have a PSP folder from an older installation of PPSSPP, just pick it, and tap on "Use this folder". You're done.

If not, follow the red markings in the below pictures.

![Tap on Create new folder.](/static/img/guide_folder/step1.png)

![Enter a name for the new folder. PSP suggested.](/static/img/guide_folder/step2.png)

![Tap on Use this folder.](/static/img/guide_folder/step3.png)

## Pitfalls

If your folder is named PSP, PPSSPP will not create a subdirectory called PSP inside it, and instead use the folder directly as the PSP directory in the root of the virtual memstick.

As a result, if you rename your folder from PSP to say PSP2 and then pick it again in PPSSPP, you won't see anything that's inside it. Instead, it will create a new subfolder inside it called PSP and use that. This can be really confusing!

To fix it, either rename the folder back, or move all the contents into the PSP subfolder.