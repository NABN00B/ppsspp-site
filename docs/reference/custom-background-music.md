# Custom background music

On the PSP, some games have support for playing audio files that you put on the memory stick as background music, replacing the default music that comes with the games.

Usually they require putting the music in a specific folder and then enabling the feature through the ingame sound options menu.

Some games also support selecting between the main folder and its subfolders.
This can be used to organize your songs into playlists or albums.

If you know some details that are missing below, [contact me](/contact).

## List of games that support this feature

I think this list is pretty close to complete:
- ATV Offroad Fury: Blazin' Trails
- Beats
- Boom Beats
- Crazy Taxi: Fare Wars
- Dead or Alive Paradise
- Elminage Original (with patch 1.01)
- Gran Turismo
- Grand Theft Auto: Liberty City Stories
- Grand Theft Auto: Vice City Stories
- Gundam Assault Survive
- Gundam Memories \~Tatakai no Kioku\~
- Hatsune Miku: Project DIVA
- Hatsune Miku: Project DIVA 2nd
- Hatsune Miku: Project DIVA Extend
- Heroes' VS
- MLB 08: The Show
- MotorStorm: Arctic Edge
- NBA Live 09
- NBA Live 10
- Need for Speed Carbon
- Need for Speed Pro Street
- Need for Speed Undercover
- Need for Speed Shift
- Pro Evolution Soccer 2011 / World Soccer: Winning Eleven 2011
- Pro Evolution Soccer 2012 / World Soccer: Winning Eleven 2012
- Pro Evolution Soccer 2013 / World Soccer: Winning Eleven 2013
- Pro Evolution Soccer 2014 / World Soccer: Winning Eleven 2014
- SD Gundam G Generation Overworld
- Surf's Up
- Test Drive Unlimited
- TOCA Race Driver 2 / DTM Race Driver 2 / V8 Supercars Australia 2 / Race Driver 2006
- TOCA Race Driver 3 Challenge / DTM Race Driver 3 Challenge / V8 Supercars Australia 3: Shootout
- Ultimate Board Game Collection
- Untold Legends: The Warrior's Code
- WipEout Pulse

Homebrew are not listed.

## Games that read MP3 files

Note: Several games require you to put the music into `ms:/MUSIC` at the root of the memory stick.
Unfortunately this can't be done on Android if your device uses scoped storage and your memstick folder is named exactly `PSP`, because then `PSP` is the actual root.
In the future, this will be possible by creating a `ROOT` folder in the `PSP` folder to simulate this.

| Game | Folder | Notes |
| --- | --- | --- |
| Beats | `ms:/PSP/MUSIC` | |
| Crazy Taxi: Fare Wars | `ms:/MUSIC` | |
| Gran Turismo | `ms:/MUSIC` | feature must be unlocked first;<br />subfolder selection supported |
| TOCA Race Driver 3 Challenge,<br />DTM Race Driver 3 Challenge,<br />V8 Supercars Australia 3: Shootout | `ms:/PSP/MUSIC` | subfolder selection supported |
| WipEout Pulse | `ms:/MUSIC/WIPEOUT` | |

In Gran Turismo to unlock custom music you must first [clear all Driving Challenges in blocks A and B](https://gran-turismo.fandom.com/wiki/Driving_Challenges_(GTPSP)), the rating doesn't matter.
Then it will be available through the options menu.

Note: games might have trouble reading non-standard MP3 files. If you suspect that your file is impaired, try opening and exporting it with [Audacity](https://www.audacityteam.org/).

## Games that read Atrac3+ files

Some games read Atrac3+ encoded files instead of MP3's for custom music.
For these games you need to convert your songs to the proper format first.

Originally tools such as **[Exact Audio Copy PSP Edition](https://archive.org/details/codemasters-eacsetup)** by Codemasters or **[Rockstar Custom Tracks](https://thegtaplace.com/downloads/f1123-rockstar-custom-tracks)** by Rockstar Games were intended to be used.
However, EAC doesn't work on modern Windows and RCT only supports conversion from audio CD's.

Nowadays we can also use **[ATRACTool Reloaded](https://github.com/XyLe-GBP/ATRACTool-Reloaded)** for this purpose.
It can encode Waveform Audio File Format (`.WAV`) audio into Atrac3+ (`.at3`) and other Sony formats.

Simply download and install the tool, along with the adequate .NET Desktop Runtime version.
You can safely ignore the warning about OpenMG upon starting it.

ATRACTool Reloaded works with both mono and stereo `.WAV` files with most of the common bitrates.
However, the file must be encoded in 16-bit PCM mode with a sample rate of 44,100 Hz (44.1 kHz).

**>insert screenshot here<**

If your file is not in `.WAV` format or is encoded differently, you have to convert it to such, e.g. via [Audacity](https://www.audacityteam.org/).
Simply open your file, and select `File -> Export Audio...` from the menubar.

**>insert screenshot here<**

In case you want to try out the feature first before you commit yourself to encoding your files, I uploaded 2 songs for you, already in Atrac3+:
- **>insert link to file1 here<**
- **>insert link to file2 here<**

### Grand Theft Auto: Liberty City Stories & Vice City Stories

Custom music files go into a special folder next to the save data folders.

The filenames must end with the `.gta` extension!
Make sure to rename your files accordingly, e.g. `We_Wish_You_a_Merry_Christmas.gta`!

The songs must be at least several seconds long (9 is enough).
Short songs are ignored by the game.

Find the custom tracks folder for your Liberty City Stories version here:
| Game Version | Game Serial | Folder |
| --- | --- | --- |
| American,<br />Korean | ULUS10041 |  |
| European,<br />German | ULES00151,<br />ULES00182 |  |
| Japanese CAPCOM,<br />Japanese Rockstar Classics | ULJM05255,<br />ULJM05885 |  |
| Sindacco Chronicles (romhack) | ULUS01826 | `ms:/PSP/SAVEDATA/ULUS01826CUSTOMTRACKS` |

Find the custom tracks folder for your Vice City Stories version here:
| Game Version | Game Serial | Folder |
| --- | --- | --- |
| American | ULUS10160 | `ms:/PSP/SAVEDATA/ULUS10160CUSTOMTRACKS` |
| European,<br />German | ULES00502,<br />ULES00503 |  |
| Japanese CAPCOM,<br />Japanese Rockstar Classics | ULJM05297,<br />ULJM05884 |  |

### TOCA Race Driver 2

Custom music files go into the folder of save data and its subfolders.
It is recommended to organize your songs into subfolders so as not to mix them with the actual save files.
The game supports subfolder selection.

The filenames must end with the `.toc` extension!
Make sure to rename your files accordingly, e.g. `We_Wish_You_a_Merry_Christmas.toc`!

The game ignores songs that are shorter than 2 seconds.

Find the save folder for your game version here:
| Game Title | Region | Serial | Folder |
| --- | --- | --- | --- |
| Race Driver 2006 | America | ULUS10096 | `ms:/PSP/SAVEDATA/ULUS100960000` |
| TOCA Race Driver 2 | Europe | ULES00040 | `ms:/PSP/SAVEDATA/ULES000400000` |
| DTM Race Driver 2 | Germany | ULES00041 | `ms:/PSP/SAVEDATA/ULES000410000` |
| V8 Supercars Australia 2 | Australia | ULES00042 | `ms:/PSP/SAVEDATA/ULES000420000` |

The following versions of the game **DO NOT** support custom music:
| Game Title | Region | Serial |
| --- | --- | --- |
| TOCA Race Driver 2 | Japan | ULJM05160 |

The European and Japanese versions of the game are also known as TOCA Race Driver 2: Ultimate Racing Simulator.
