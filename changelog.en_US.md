# GarlicOS ChangeLog

Original information from https://www.patreon.com/posts/76561333

## January 2023:

- Added HDMI audio support (requires you to plug in the HDMI cable before starting the game, also, never unplug the HDMI cable while playing, it will freeze the system so exit your game first and unplug it once you're back in the GarlicOS menu)

## 24. January 2023

- Fixed a crash that occured after removing the last favorite from the list while being inside the favorites menu
- Fixed a bug in the recent game list where unsorted lists resulted in duplicate entries
- Settled for a 1.5GHz overclock because a lot of units out there couldn't reliable handle 1.6GHz (select will now toggle from 1.0GHz to 1.3GHz (+) to 1.5GHz (++) to 700MHz (-) to 500MHz (--) and back to 1.0GHz)
- Fixed a typo in the game art paths (pre-populated OnionOS cards in TF2 should now load their artwork properly)
- Game art and screenshots are now scaled bilinear to fit the rest of the OS's default settings

## 23. January 2023

- The battery calculation formula has been altered to (hopefully) return more accurate results (its unlikely we'll ever get a 100% accurate battery reading out of this device though)
- Files containing $ or ! in their name will now load properly (Wario Ware)
- Artwork is now loaded from Roms/Imgs/SystemName/GameFileNameWithoutExtension.png (the old path CFW/skin/games/SystemName/GameFileNameWithExtension.png is still  supported though)
- Added a 1.6GHz overclock option (+300MHz compared to the last build)
- Added UC/OC profiles (toggle between them with the SELECT button, -- equals 500MHz, - equals 700MHz, nothing equals the 1GHz default, + equals 1.3GHz and ++ equals 1.6GHz)
- CPU hot-plug has been disabled to ensure in-use cores don't get disabled mid-gameplay (this should reduce thread-relocation-related stutters)
- Fixed the screen timing (from 56Hz to 60Hz)

## 22. January 2023

- Fixed a bug in the recent game list that (sometimes) required you to delete a game twice for it to disappear
- The linear scaler is now hardware-accelerated (using the LCD panel's hardware-scaler plus some glue-code to ensure "Keep aspect ratio" doesn't break, using this new scaler also solves all the remainder tearing issues people reported in games like Super Mario Bros)
- The hardware-accelerated linear scaler is now set as the default scaler for every core (this translates to a free 20% performance boost & universal tearing fix pretty much)
- The LQ2x filter is now enabled by default for all cores except those that have known compatibility issues with it (so we can benefit from the hardware scaler's tearing-resistance on as many systems as possible, let me know if you find cores that are incompatible with it)
- Added a core override for PCSX-ReARMed & DOSBox Pure to fall back to the software based nearest scaler instead of the LQ2x filter + hardware based bilinear scaler as it produces what I consider better visuals)
- Disabled RA notifications as the mix of hardware and software based scaling across cores produces inconsistently sized font glyphs)
- Disabled savestate compression to accelerate savestate creation

## 21. January 2023

- Overclocked the CPU to 1.3GHz (+300MHz)
- Upped the < 800MHz CPU voltage by 0.025V (fixes random freezes)
- Upped the Menu button hotkey hold time from 150ms to 250ms (should fix the need for double-tapping the Menu key)
- Upped the scroll animation inhibition time (should make single d-pad  taps more in the game lists more precise / less likely to skip an entry due to repeats)
- Optimized the main menu renderer (60%+ CPU use reduction when idle)
- Added a dosbox_pure libretro core setting override to auto-enable max CPU cycles (this should help a few tricky games run fullspeed OOB)
- Re-enabled audio synchronization (we previously disabled it because it  helped MD frame pacing but it completely destroyed audio output across  the board by introducing noticeable stutters)
- The main menu is now rendered in 32bit colors (a future update will bring 32bit color support for RetroArch as well)
- Fixed a bug that could cause duplicated items in the recent game list
- Fixed a regression that broke sleep/resume for games stored on TF2

## 19. January 2023
- Fixed a crash related to file names starting with `(`, `[` or `.`
- Fixed a paging issue in the game system menu that produced empty pages
- Changed the key repeat code in the main menu to better handle VSync
- Added the `puae_2021` libretro core and made it the `AMIGA` & `AMIGACD` default core (pretty much a free speed boost, still not full speed though)
- Added a 100ms wind-up time to scroll animations (this should prevent accidental item skips on single d-pad presses)
- Game lists now load WAY faster
- Added support for game art overlays (`CFW/skin/game-overlay.png`, please use alpha-blending sparingly as it is a very CPU intensive operation)
- Added a hide guide button text option (`CFW/skin/settings.json`)

## 18. January 2023

- Fixed GarlicOS main menu frame limiter
- Fixed dosbox_pure libretro core (DOS games)
- Tapping the menu key inside a game now takes you back to the recent game screen
- Exiting the RetroArch main screen now properly restores your GarlicOS cursor location
- RetroArch now remembers your volume setting

## 17. January 2023

- Set block_sram_overwrite = "true" to increase savestate stability
- Changing the savestate slot in the quick menu no longer crashes RetroArch
- Fixed transparent game art (for real now)
- The GarlicOS main menu is now double-buffered (less tearing on fast scroll)
- Recompiled dosbox_pure libretro core in the hopes of addressing a color space issue (need further feedback on this one, let me know if this did it)
- Reduced the minimum screen brightness (added two additional levels)
- Themes can now disable the "Main Menu" text (for those that prefer logos)

## 16. January 2023

- Nearest-point scaler is now dual-threaded (pinned to core 3 & 4)
- Semi-linear (Bresenham) scaler is now dual-threaded (pinned to core 3 & 4)
- Audio synchronization was disabled (this helps with stuttering on some cores)

## 14. January 2023

- Transparent game art should now render properly
- The Commodore 64 system icon should now render properly
- Game art now loads properly after a L1/R1 letter jump
- The UI now waits for the scroll operation to finish before loading game art (this should help with slower MicroSD cards)
- Resume now works properly for games stored on the second MicroSD card (TF2/EXT)
- The recent game list now takes the last used MicroSD card into account when sorting items
- The mednafen_vb libretro core (Virtual Boy) should now work properly
- Themes can now configure the game list text alignment and margin

## 13. January 2023

- Arcade games should now display their actual name (it uses a optimized LUT stored in config/mame.csv)
- Several memory leaks in GarlicOS have been fixed
- The navigation code has been altered to allow for Left / Right to scroll faster and L1/R1 to skip between starting letters
- The X button can now be used to remove unwanted games from the recent games menu
- Enabled fast-forward frame skipping
- Fixed the battery gauge icon padding (it was off by 4 pixel, I knew something felt off about it...)
- Fixed a typo in the coremapping.json file

## 12. January 2023

- Fixed a typo in the core mapping code (fixes PS game loading)
- Redesigned the recent game screen (modeled after OnionOS' GameSwitcher)
- Added support for game art (put 640x480 pixel resolution GameFileName.png files into the skin/games or skin/games/systemname folder, these will replace the default background image while hovering the game in the menu)
- Moved the recent game history file location to Saves/CurrentProfile/lists (which allows us to load OnionOS history files from the TF2 card slot)
- The recent game menu now shows recent games from both MicroSD cards (it merges the lists)
- The left & right dpad button can now be used for navigating the game lists
- Fixed the crocods libretro core (Amstrad emulator, keep in mind this one doesn't support zipped games)
- Fixed a regression that affected sleep / resume
- Fixed a crash in the RetroArch quick menu
- The default libretro core for CPS1, CPS2 and CPS3 was set to fba2012
- The recent menu now only shows the last 10 games played OOB (to prevent choice paralysis, 20 if two MicroSD cards are used, 10 per card, this setting can be adjusted in retroarch.cfg)

## 11. January 2023

- Added vemulator libretro core (Dreamcast VMU emulator)
- Fixed a line render bug in mednafen_supafaust (SNES emulator)
- Fixed all fbalpha2012 libretro cores (Neo Geo, CPS1, CPS2, CPS3, Arcade)
- Added mame2003_extreme libretro core (faster than mame2003_plus, slower than fbneo & fbalpha2012, new default for ARCADE folder as its binary-compatible with the mame2003_plus romset)
- Added mame2000 libretro core (so MAME2000 folder gets the core it expects)
- All default folder to core mappings now match that of OnionOS on the Miyoo Mini
- The default folder to core mapping can now be changed by editing the config/coremapping.json file
- The folder structure now reflects that of a OnionOS Miyoo Mini MicroSD card (Roms, BIOS and Saves folder)
- BIOS files now get loaded off the same MicroSD card the game ROM is located on (for compatibility reasons: different cards might have been prepared with different BIOS files, which can make a difference in arcade emulation)
- Saves are now stored on the same MicroSD card the game ROM is located on
- As a result of all of the mentioned above changes, it is now possible to stick a fully prepared OnionOS MicroSD card into the TF2 slot and load / resume games you previously played on your Miyoo Mini allowing for easy swapping of savegames between a RG35XX and a Miyoo Mini
- Removed the pre-bundled cheat files again because they made first-time setups "too bulky" (you can always download them from the RetroArch GitHub page)

## 9. January 2023

- Skins now feature a settings.json file that allow for font color changes
- VSYNC should now work better (less tearing once again)
- Dropped triple-buffering as its no longer required after today's changes
- PCSX-ReArmed is now pre-configured to run at 100% clock speed (57% before)
- Fixed the RetroArch HUD notifications when using integer scaling
- The RetroArch cheat database is now bundled by default
- The battery icon display has been changed to better reflect actual battery life
- Neo Geo Pocket games are now associated with the race libretro core (which fixes them, finally)

## 4. January 2023

- The built-in panel now waits for VSYNC properly (OWLFB_WAITFORVSYNC)
- The SNES default-core was set to snes9x_2005 (better overall performance)
- The favorites menu is now alphabetically sorted

## 3. January 2023

- Added the libretro game system icons

## 2. January 2023

- Added cap32 libretro core (Amstrad)
- Added fake08 libretro core (replaces retro8 for pico-8)
- Added Amiga CD32 binding (emulated by puae libretro core)
- Added o2em libretro core (Odyssey 2 & Videopac+ G7400)
- Added dosbox_pure libretro core (DOS games, duh.)
- Added virtualjaguar libretro core (seems to not work though)
- Added mednafen_supergrafx libretro core (SuperGrafx)
- Added nekop2 libretro core (PC-98)
- Added mednafen_pcfx libretro core (PC-FX)
- Added mednafen_vb libretro core (Virtual Boy)
- Added opera libretro core (Panasonic 3DO)
- Added px68k libretro core (Sharp X68000)
- Added NeoGeo CD support (emulated by fbneo libretro core)
- Added uzebox libretro core (UZEBOX, duh.)
- Added mednafen_ngp libretro core (Neo Geo Pocket)
- Added sameduck libretro core (Mega Duck)
- Added mednafen_pce_fast libretro core (TurboGrafx CD)
- Added support for game system icons (put them in skin/system/FOLDERNAME.png)
- Fixed integer scaling support
- Enabled multi-threaded rendering OOB (benefits PS1, fixes FF)
- Enabled stretched point scaling by default (the screen is small and my eyes are bad...)

## 1. January 2023

- Added puae libretro core (Amiga)
- Added fbneo libretro core (MAME, CPS1, CPS2, CPS3 & Neo Geo)
- Fixed a bunch of previously broken cores (pico-8 for example)
- Empty ROM folders are now pre-created
- Removed a PS1 BIOS file that snuck in by accident
- SNES now scales pixel-perfect OOB
- Disabled per-core screen refresh rate adjustment (fixes some more tearing issues we were having)
- Disabled per-core screen color mode adjustment (fixes several more previously broken cores that forced non-RGB565 color modes)

## 31. December 2022

- Disabled rewind support (it messes with PS1 emulation)
- Disabled multi-threaded rendering (it caused visible tearing)
- Menu + L1 now toggles slow-motion

## 30. December 2022

- Initial GarlicOS release
- Fixed sleep mode
- Fixed the RetroArch on-screen keyboard
- Added a brand new user interface
- Added OnionOS styled hotkeys
- Paused games now resume automatically after waking from sleep
- Added support for the OnionOS MicroSD card folder structure
- Moved the brightness controls to Menu + Volume Up / Down
- Added a new garlic-themed boot logo
