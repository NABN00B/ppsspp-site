# Custom background music

On the PSP, some games have support for playing audio files that you put on the memory stick as background music, replacing the default music that comes with the games.

Usually they require putting the music in a specific folder and then enabling the feature in sound settings.

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
- Grand Theft Auto: Liberty City Stories (Atrac3+)
- Grand Theft Auto: Vice City Stories (Atrac3+)
- Gundam Assault Survive
- Gundam Memories \~Tatakai no Kioku\~
- Hatsune Miku: Project DIVA
- Hatsune Miku: Project DIVA 2nd
- Hatsune Miku: Project DIVA Extend
- Heroes' VS ([#5866]?)
- MLB 08: The Show
- MotorStorm: Arctic Edge
- NBA Live 09
- NBA Live 10
- Need for Speed Carbon
- Need for Speed Pro Street
- Need for Speed Undercover
- Need for Speed Shift
- Pro Evolution Soccer 2011
- Pro Evolution Soccer 2012
- Pro Evolution Soccer 2013
- Pro Evolution Soccer 2014
- SD Gundam G Generation Overworld
- Test Drive Unlimited
- TOCA Race Driver 2 (Atrac3+)
- TOCA Race Driver 3 Challenge
- Ultimate Board Game Collection
- Untold Legends II
- WipEout Pulse
- WipEout Pure
- World Soccer Winning Eleven 2014: Aoki Samurai no Chousen

Homebrew are not listed.

## Games that read MP3 files

Some games support selecting between the main folder and its subfolders.
This can be used to simulate playlists or albums.

Note: Several games require you to put the music into `ms:/MUSIC` at the root of the memory stick.
Unfortunately this can't be done on Android if your device uses scoped storage and your memstick folder is named exactly `PSP`, because then `PSP` is the actual root.
In the future, this will be possible by creating a `ROOT` folder in the `PSP` folder to simulate this.

| Game | Folder | Notes |
| --- | --- | --- |
| Beats | `ms:/PSP/MUSIC` | |
| Crazy Taxi: Fare Wars | `ms:/MUSIC` | |
| Gran Turismo | `ms:/MUSIC` | feature must be unlocked first;<br />subfolder selection supported |
| TOCA Race Driver 3 Challenge | `ms:/PSP/MUSIC` | subfolder selection supported |
| WipEout Pulse | `ms:/MUSIC/WIPEOUT` | |

In Gran Turismo you must first clear all [Driving Challenges](https://gran-turismo.fandom.com/wiki/Driving_Challenges_(GTPSP)) in blocks A and B to unlock this feature, then it will be available through the options menu.

Note: Games might have trouble reading non-standard MP3 files. If you suspect that your file is impaired, try opening and exporting it with [Audacity](https://www.audacityteam.org/).

## Games that read Atrac3+ files



### Grand Theft Auto: Liberty City Stories

### Grand Theft Auto: Vice City Stories

| Game Version | Game Serial | Folder |
| --- | --- | --- |
| American |  |  |
| European,<br />German | <br /> |  |
| Japanese CAPCOM,<br /> Japanese Rockstar Classics | <br /> |  |

### TOCA Race Driver 2
