# RetroAchievements - setup and use

[RetroAchievements](https://retroachievements.org/) are similar to XBox achievements or PlayStation trophies, except that they're created and defined by a volunteer community. Just like other retro consoles, the PSP itself has no native concept of achievement/trophies. However, this can be added with emulation!

Not only achievements are supported, but also global leaderboards in games that have scores or times.

## FAQ

## What versions of PPSSPP support RetroAchievements?

RetroAchievements will be supported in PPSSPP 1.16. It is not supported in 1.15.4 and older.

## What games are supported?

Find the list of PSP games with achievement support [here](https://retroachievements.org/gameList.php?c=41).

Unfortunately, it's often the case that only one or two regions of a game are supported. Click the link "Supported game files" on the game's page on that site to find out.

## My achievement unlocked at the wrong time!

All existing achievements were created for the PPSSPP core in RetroArch. Unfortunately, due to deficiencies in libretro's design, achievement checks don't run at the correct time in RetroArch - so if your achievement works correctly in RetroArch and not in PPSSPP standalone, the achievement is broken.

## Will RAIntegration be added?

Yes, in the future. No time frame has been decided on.

(RAIntegration is a feature that makes development of new achievements much easier).

## Settings documentation

### Challenge Mode

This is also known as Hardcore Mode, but due to the various associations of the word, and how restrictive the Play Store reviewers can be, we've renamed it to Challenge Mode, much like DuckStation or PCSX2.

### Encore Mode

Lets you unlock achievements again. Note that this does not affect the real unlock status - you'll just get the notification again if you fulfill the conditions, such as completing a level or whatever it was.

### Unofficial achievements

These are achievements that have been removed, or are in development, or have simply been considered not really worth having.

Usually, turning on this option is not very useful - if you need it, you know you need it.

## Developing achievements for PPSSPP

Achievements are best developed with emulators supporting so-called RAIntegration. PPSSPP does not yet do that, unfortunately, so your best bet is still RetroArch.

RAIntegration support may arrive in PPSSPP in the future.

## How do I register?

Simply go to the [RetroAchievements website](https://retroachievements.org/) and sign up for an account. You can then sign into that account in PPSSPP.

## Additional resources

[RetroAchievements on YouTube](https://www.youtube.com/@retrocheevos)
[RANews - the digital magazine](https://news.retroachievements.org/)
[RA User Documentation](https://docs.retroachievements.org/)
[RA Developer Documentation](https://docs.retroachievements.org/Developer-Docs/)