# GarlicOS ChangeLog

Original information from https://www.patreon.com/posts/76561333

## 7. March 2023:

- Fixed the dinothawr libretro core
- GarlicOS' recent game menu screenshot renderer now respects the global retroarch.cfg aspect ratio setting
- Changed the boot_cap_threshold from 3% to 0% (this should allow the device to boot when the broken battery meter reports the battery as 0%)
- Savestates now get synced to disk before poweroff
- Partitions now get error-checked on system start
- Added external gamepad support to the GarlicOS UI (tested with 8bitdo XInput controllers, we'll probably need a vendor + product ID keylayout database of sorts so we can support a larger variety of gamepads OOB, still debating on how to best share gamepad mappings between RetroArch & the GarlicOS UI...)
- External controllers now control the RetroArch player 1 slot by default (if present)
- Brightness controls are now ignored while HDMI is in use
- The built-in monitor now gets disabled while HDMI is in use
- The HDMI overlay flicker issue in GarlicOS' recent game menu has been fixed
- Set the GarlicOS version number to 1.2.0

## 3. March 2023:

- Fixed a speaker malfunction that occured on some (not all) V6.0 PCBs
- Set the GarlicOS version number to 1.1.9

## 2. March 2023:

- Fixed a integer scale regression that snuck in with build 1.1.2
- Fixed a button spam issue caused by the recently added V6C PCB support
- Set the GarlicOS version number to 1.1.8

## 28. February 2023 (Part 3)

- Added IPF support for PUAE
- Changed the default mount flags to errors=continue to keep the bad stock MicroSD cards at least somewhat functional when they start dying on you (this won't fix them, but the OS won't freeze immediately on the first I/O error they report)
- Set the GarlicOS version number to 1.1.7

## 28. February 2023 (Part 2)

- Fixed the mednafen_supergrafx libretro core
- Set the GarlicOS version number to 1.1.6

## 28. February 2023 (Part 1)

- Added support for the new V6C PCB revision (this point includes a new bootloader, u-boot and several driver changes to ensure both pre- and post-V6C models can run off the same kernel)
- Added some additional checks to the scaler code to ensure width & height don't scale beyond 1280x1280 (this fixes Virtual Boy emulation)
- Fixed the 2048 libretro core (this is a single-game core and as such has no folder mapping associated with it, to play it, load and start the core within RetroArch)
- Fixed the reminiscence libretro core (this is a single-game core and as such has no folder mapping associated with it, to play it, load and start the core within RetroArch)
- Fixed the virtualjaguar libretro core (but its still way too slow to be considered playable)
- Set the GarlicOS version number to 1.1.5

## 25. February 2023 (Part 3)

- Added the atari800 libretro core
- Set the GarlicOS version number to 1.1.4

## 25. February 2023 (Part 2)

- Fixed the tic80 libretro core
- Fixed HDMI (it regressed in version 1.0.9)
- Fixed FPS display flicker
- Made the notification text gradient less extreme
- Removed useless progress percentage indicator from near-instant tasks
- Made all parts of the notification system configurable (RetroArch -> Settings -> On-Screen Display -> On-Screen Notifications) which means you can use a custom font, font size, font color and change the text's alignment as needed (0 is left / top, 0.5 is center, 1 is right / bottom)
- Set the GarlicOS version number to 1.1.3

## 25. February 2023 (Part 1)

- Added support for hw-accelerated alpha-blended overlays (these are now being used for RetroArch notifications, but will, in future builds, also be used to provide system-frames and in-game battery / clock display)
- Reverted the PS1 gamepad type to digital as the DualShock type rendered too many games unplayable (if updating via CopyPasteOnTopOfStock please make sure to delete the "CFW/retroarch/.retroarch/config/remaps/PCSX-ReARMed" directory before updating)
- Set the GarlicOS version number to 1.1.2

## 24. February 2023

- Fixed a menu scaling issue that affected PS1 games (and any other system that rendered at exactly 320x240)
- Set the GarlicOS version number to 1.1.1

## 23. February 2023 (Part 2)

- Fixed a scaler resolution issue that occured when manually booting a core
- Set the GarlicOS version number to 1.1.0

## 23. February 2023 (Part 1)

- Added new notification renderer
- Re-enabled notifications
- Fixed filter screen flicker
- Fixed fast forward screen notification flicker
- Absorbed the fb1 framebuffer (original HDMI framebuffer) into fb0 to ensure we have enough memory to triple buffer for flicker-free fast forwarding
- Fast forward top-clocks the CPU now (so we can fast-forward faster)
- Saving and loading states top-clocks the CPU now (so we can save or load states faster)
- Adjusted <= 1GHz voltages to account for lemon unit (less crashes)
- Set the GarlicOS version number to 1.0.9

## 17. February 2023

- Removed some debug code
- Fixed a memory leak in the recent game menu
- Removed a rogue file that snuck into the bundle
- We're now using the sinc audio resampler by default (I messed this setting up on the previous build by accident)
- ScummVM games should now start properly (if you used the workaround that's been making the rounds on Discord, please make sure to delete Saves/CurrentProfile/lists/content_history.lpl first before reporting issues)
- Cores that don't support savestates will now display a message indicating so in the recent game menu (do we need this for anything other than ScummVM?)
- The GarlicOS menu now runs at 500MHz when idle and increases the CPU clock as needed while scrolling (to increase fluidity AND save battery where possible)
- Added a core mapping for QUAKE support (tyrquake libretro core)
- Added rumble motor support (built-in gamepad only, mostly for PS1 games)
- Changed the PS1 gamepad type to DualShock (so we can make use of the rumble motor)
- Added a OnionOS artefact filter to prevent otherwise empty console directories from being listed
- One can now press the reset button to escape auto-resume boot-loops caused by broken cores or games
- The provided download files are now -mx9 compressed (which shaves off about 20mb or so...)
- Set the GarlicOS version number to 1.0.8

## 14. February 2023

- Changed the default audio resampler to sinc (makes audio feel less tinny)
- Disabled R2 (hold) fast-forwarding in Gambatte & gpSP (as its broken)
- The emulation can now be paused via Menu + Start
- The FPS overlay can now be toggled via Menu + Select (this requires font  overlays to be enabled which is currently disabled by default because the IPU scaler has issues sizing it)
- Screenshots can now be created via Menu + DPad Up
- The savestate slot can now be changed via Menu + DPad Left / Right
- The audio can now be muted via Menu + DPad Down
- Set the GarlicOS version number to 1.0.7

## 13. February 2023:

- Fixed a typo in skin/settings.json
- Arcade cores are now configured to skip savestate auto-loading (as they cause audio glitches, graphical issues and crashes on these cores)
- Added video playback support (put them in the VIDEOS folder, encode them  with "ffmpeg -i input.mkv -vf scale=640x480 -vcodec libx264 -profile:v main -level 3.1 -preset medium -crf 23 -x264-params ref=4 -acodec libvorbis - - movflags +faststart output.mkv" and hard-sub your videos if necessary, don't encode to mp4 files as they confuse ffmpeg when seeking, add additional core-mapping folders and system icons as needed to sort your shows)
- Set the GarlicOS version number to 1.0.6

## 10. February 2023

- Added support for APPS / PORTS (but someone needs to code some first)
- Added support for UTF8 encoded filenames / strings
- Skins can now swap every text in the menu (see skin/settings.json)
- HDMI can now be hot-plugged without crashing the system (let me know if any of you still encounter issues with it)
- The minimum menu CPU clock has been raised to make up for HDMI mirroring overhead (it couldn't quite keep up in the recent game menu)
- Fixed the pixel budget calculator (this should fix some fringe-case games that previously overflowed the 1228800 pixel budget and low resolution games that refused to properly scale with the bilinear multiply scalers)
- Set the GarlicOS version number to 1.0.5

## 4. February 2023

- Fixed a glitch that occured when entering the RetroArch menu while fast forward was active
- Set the GarlicOS version number to 1.0.4
-
## 3. February 2023

- Fixed fast forward framebuffer freezes
- Fixed freeintv_libretro core (Intellivision)
- Fixed bogus keyboard inputs (should make games like Nebulus, Monkey Island, etc. playable)
- Set the GarlicOS version number to 1.0.3

## 1. February 2023 (Part 3)

- Fast-forward no longer freezes the screen on same-thread rendered cores
- Set the GarlicOS version number to 1.0.2

## 1. February 2023 (Part 2)

- fake08 core (pico-8) now runs on the threaded renderer by default (we need the speed boost)
- fake08 core is now excluded from loading savestates automatically (as the core tends to crash while loading savestates)
- fake08 core is now excluded from sleep-resume (as many pico-8 games freeze RetroArch, which means we need to keep the reset button functional as a emergency exit of sorts for when that happens)
- Set the GarlicOS version number to 1.0.1

## 1. February 2023 (Part 1)

- Threaded rendering is now disabled by default to further reduce input latency where possible (except for PS1 & arcade cores which need threaded rendering to reach full speed)
- Bilinear has been set as the default scaler for arcade cores (to give these CPU heavy cores more room to breathe)
- Updated the gpSP (GBA) core
- The iosched queue manager has been changed from cfb to noop (speeds up file access)
- MAME name resolution is now done via hash tables for an additional speed boost (~3000 files in ~2 seconds)
- The FBA2012 folder now has the right icon set
- Pressing start instead of the A-button when selecting a game will now skip the savestate auto-load function
- Audio volume no longer gets saved in manually created core overrides (prevents unexpected volume changes on game load)
- History & BIOS paths no longer get saved in manually created core overrides (prevents unbootable games on TF2 card pull)
- Added a prboom_libretro (DOOM) core-mapping & system icon
- Added a meridian time clock style (AM/PM)
- GarlicOS now memorizes your menu cursor (to the best of its abilities) and restores it on game exit / system boot
- Tapping the menu key inside GarlicOS' menu will now take you to your recent games
- Long pressing the menu key inside GarlicOS' menu (> 1000ms without pressing any other keys) will now take you to the main menu
- The "Main Menu" text has been replaced with a version number display
- Set the GarlicOS version number to 1.0.0

## 28. January 2023

- Added bilinear-multiply scalers (based on eggs' amazing NEON scaler code)
- Set the Bilinear4x NEON scaler as the new default (this reduces CPU consumption by about 50% and increases graphical fidelity)
- Fixed keep aspect ratio on all bilinear scalers
- The integer scaler got a sizeable speed boost
- Bilinear-multiply scalers now drop down to their next lower tier if a framebuffer overflow is likely
- Improved the rendering quality of recent game screenshots in the GarlicOS UI
- Adjusted default settings and core overrides to make use of the new scalers where possible
- Brought back the overclock select toggle as the conservative governor made too many wrong assumptions during extended testing (the toggle now controls the in-game CPU frequency, the GarlicOS menu always runs at 700MHz regardless of the setting to save on battery)
- Hidden Linux / MacOS files are now no longer listed in the game browser
- Added real-time-clock (RTC) support (press start to configure the clock and B or start again to save your clock changes)
- Fixed a R<->B channel flip bug in the MAME2003-Xtreme core

## 26. January 2023

- Fixed the XRGB8888 color converter in the MAME2003-Xtreme core (fixes Captain America and The Avengers amongst others)

## 25. January 2023

- Added HDMI audio support (requires you to plug in the HDMI cable before starting the game, also, never unplug the HDMI cable while playing, it will freeze the system so exit your game first and unplug it once you're back in the GarlicOS menu)
- Added downscaling support to the hardware accelerated bilinear scaler (this should fix the cut-off screen issues the bilinear scaler had)
- Normal4x filter now runs 25% faster (its a viable option for some cores now)
- Normal2x is now the default filter for most cores (sharpest looking pixels we can afford while still using most of the screen real estate)
- Fixed a backlight related regression that snuck in when I first added HDMI audio support earlier today
- Added a core override for gambatte & gpSP to force nearest scaling (as display mode changes cause noticeable flickering on the gambatte core, making it difficult to use the hardware scaler there and gpSP simply looking better on the nearest scaler)
- Optimized the savestate screenshot loader (they load a bit faster now)
- Reduced input latency
- Fixed the O1555RGB color converter in the MAME2003-Xtreme core (fixes Captain Commando amongst others)
- Created an overlay for the MAME2003-Xtreme core to disable the Normal2x filter (it doesn't really handle it well)

## 24. January 2023

- Fixed a crash that occured after removing the last favorite from the list while being inside the favorites menu
- Fixed a bug in the recent game list where unsorted lists resulted in duplicate entries
- Fixed a typo in the game art paths (pre-populated OnionOS cards in TF2 should now load their artwork properly)
- Game art and screenshots are now scaled bilinear to fit the rest of the OS's default settings
- Settled for a 1.5GHz overclock because a lot of units out there couldn't reliable handle 1.6GHz
- Switched to the conservative governor and applied a few governor related tweaks to ensure the CPU will scale smoothly between CPU states as needed (this will improve battery life as well as reduce potential stutter)
- Removed the select CPU frequency toggle because the new governor does a good enough job at picking the right frequency automatically
- Corrected a typo in yesterday's changelog's artwork path
- Fixed a game launch error caused by single quotes in filenames (revised to deal with some shell quirks)

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
