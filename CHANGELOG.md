# Hex Editor — version history

## Version 1.8.7

- **Fixed: clicking the scrollbar no longer clears your selection.** In compare view, clicking a red difference mark on the scrollbar used to jump *and* wipe whatever you had selected. Now it just scrolls to the difference and leaves your selection alone.
- **New: Mark start / Select to here** — select a large range without dragging. Right-click (or the Edit menu) → "Mark selection start", scroll to the end byte, then → "Select to here". Everything between is selected, even across many screens.

## Version 1.8.6

- **Find value**: search for a number as its stored bytes — type a value (decimal, or 0x for hex), choose 1 / 2 / 4-byte size and little- or big-endian, and step through every match. Search menu → "Find value…" (Ctrl+Shift+F)
- **Export selection to file**: save the selected bytes out as their own file — Edit menu or right-click → "Export selection to file…"
- Minor fixes

## Version 1.8.5

- Internal improvements

## Version 1.8.4

- **Smoother scrolling in compare view**: the second file (B) could lag behind, stutter or skip lines while scrolling because it was redrawn only after file A. Both files now move and redraw together on every wheel step, scrollbar drag and PageUp / PageDown
- **The mouse wheel scrolls the file under the mouse pointer**, even if the other file has the keyboard focus
- Fast wheel turns and touchpad swipes are combined instead of piling up, and the scroll distance follows the Windows "lines per notch" setting (also smooth on high-resolution wheels and touchpads)
- Lighter on the CPU: the blinking cursor no longer redraws the whole file view

## Version 1.8.3

- **Fixed: clicking a red difference mark on the scrollbar** didn't always land on that difference (marks near the bottom or top could overshoot, especially with the shorter view in side-by-side mode). Clicking a mark now jumps straight to that difference and selects it in both files
- **The other file now shows where you are**: in compare view, the byte under the cursor in the file you're working in is outlined at the same offset in the other file, and a selection is shown there as a light tint

## Version 1.8.2

- Internal security hardening and small robustness fixes

## Version 1.8.1

- **Fixed: files with long names / in deep folders could not be opened** ("Could not find a part of the path", as if the file were missing) and showed greyed out in Recent files. Programs built like Hex Editor were held to the old Windows 260-character path limit; Hex Editor now opens, saves, backs up and exports files with paths of any length
- Clearer messages when a file can't be opened: a file that was really moved / renamed / deleted says so (and can be removed from Recent files); a path that is still too long for this PC says how to fix it
- Recent files that no longer exist are marked **(missing)**

## Version 1.8.0

**Much better readable-text detection**

- Program names written in CamelCase are now found (`IdentFile`, `CpuAddress`, `Latin1Encoding`, `mapCache`, `XmlReader`), and short names inside a list of texts are kept too (`RxEpk`, `UInt32`)
- **UTF-16 (Windows "wide") text** is now detected — menu texts and messages inside .exe / .dll files — marked **UTF-16**
- **VINs are listed again** (marked **VIN**), once
- Far less junk from random bytes: a word must use letter pairs that real words use, and 4-letter words must be real words (English, German, French, Italian, Spanish, car and programming terms). On a random-data test the junk went from 86 to 1
- Short codes count as part numbers only when they look like one (mostly digits, or an ECU family like **EDC17, MED17, SIMOS18, SID807, MG1**)
- Fill patterns are no longer listed (`5555555555`, `HHHHHHHHHH`, `UUUUUU`, `333333`)
- The length byte in front of .NET / Pascal-style strings is removed
- Big files are scanned to the end (was limited to the first 20,000 texts)
- Double-click editing of a UTF-16 line writes UTF-16 bytes

## Version 1.7.9

- **Zoom on / off switch in Settings**: untick **Settings -> Zoom** to keep the view at a fixed 100% size (no fitting to the window, Ctrl + wheel does nothing). Tick it again to have the view fit the window size

## Version 1.7.8

- **New icon everywhere**: Windows kept showing the old icon from its icon cache because the update replaces the program in place. Hex Editor now tells Windows to refresh it once after updating, so Explorer, the desktop and the taskbar show the new Loki954 icon
- The small icon sizes (title bar, taskbar, file list) were redrawn bolder so the new hexagon is clearly visible at 16-32 px

## Version 1.7.7

- **Fixed: zooming made the app flicker, slow down and crash.** The window kept re-fitting itself in a loop and used up Windows graphics resources. The zoom is now applied once when you finish resizing (not while dragging), the window is frozen while it rescales so there is no flicker, and nothing builds up over time
- Ctrl + / Ctrl - / Ctrl+wheel zoom is smoother (one clean redraw per step)

## Version 1.7.6

- **Zoom that fits the window**: the hex tables, text, Inspector, readable-text list, buttons and panels get smaller when the window gets smaller and bigger when it gets bigger -- all 16 columns and the text column stay in view
- Fine-tune with **Ctrl +** / **Ctrl -** or **Ctrl + mouse wheel**; **Ctrl+0** resets. Auto-fit can be turned off in **View -> Auto-fit to window size**
- The Inspector and readable-text box share the side panel better on short windows
- **Fixed: the new Loki954 icon** now shows in the title bar

## Version 1.7.5

- **New Loki954 app icon**
- **Everything stays visible at any window size**: the top toolbar and the file buttons (Open / Save / Save as / Tools / Close) shrink to compact labels when the window or a side-by-side pane gets narrow, and expand back to full labels when there is room -- nothing is cut off anymore

## Version 1.7.4

- **Multi-select with Ctrl**: hold **Ctrl** and drag to add more separate blocks to the selection. **Copy (Ctrl+C)** and the **Copy A -> B / B -> A** buttons act on all selected blocks at once
- **Shift + drag** extends the current selection from where it started
- **Copy A -> B / B -> A** buttons show arrows pointing left / right when the files are side by side, up / down when top / bottom
- **Readable text**: press **Ctrl+C** to copy the selected line, and **double-click** a line to edit its text in place (kept the same length)

## Version 1.7.3

- **Side-by-side compare** now puts the Inspector / Readable-text panel **under each file** instead of on the right, so each file gets the full width and the file name is no longer cut off
- The side panel text is **more compact**, and the Inspector lays its values out in columns when it sits under a file
- Removed the duplicate **Light / Dark theme** entry from the **View** menu — it stays in **Settings** (and the ☀ / ☾ button in the status bar)

## Version 1.7.2

- **Readable text filtered more tightly**: random short alphanumeric runs from encrypted / random areas (e.g. RNMr, 8DlC, j2jK, z7yL) are no longer listed. A run is kept only if it contains a real token — a part number, a number, or an actual word. "Show all runs" still reveals everything

## Version 1.7.1

- **Fixed: single-file view** lost the right-hand panel (Inspector / Readable text). It's back
- **Fixed: drag & drop** — you can now drop a file anywhere in the window (not only on the hex grid), and it also works when Hex Editor runs as Administrator
- Drop two files at once to open them in A and B

## Version 1.7.0

- **Compare side by side (left / right)**: a switch in **Settings** (and in the **Compare** menu) arranges the two files left and right instead of top and bottom. The toolbar moves to the top. The choice is remembered

## Version 1.6.1

- **Readable text is now much more accurate**: it keeps only genuine text (part / software numbers, VINs, labels) and no longer lists random 4-character runs from encrypted or random areas. A run must contain a real word or number and be mostly letters / digits
- The **Strings** tab has a **"Show all runs"** tick if you ever want every printable run, including the random ones

## Version 1.6.0

- **Readable text box** always on the right, under the Inspector: it fills in by itself when a file is opened (texts, part / software numbers, VINs, reversed VINs too). It has a title, shows about 6 lines with a scrollbar, and **clicking a line jumps to it** in the file. It refreshes after you edit
- Both the quick box and the full **Strings** tab now have a clear **title**
- **Light theme**: the scrollbar is now clearly visible (it was almost invisible before)

## Version 1.5.3

- **Rectangle bookmarks**: a bookmark made from a rectangle (block) selection keeps exactly that rectangle. Before, it covered whole rows from the first to the last byte
- Bookmarked bytes are **tinted in the bookmark's colour**, with an underline and a left edge on each row, so they're easy to see
- Clicking a rectangle bookmark selects the same rectangle again
- Right-click → Edit / Remove now works on the exact byte you right-clicked
- Checksum auto-detect no longer reports counter-like data (00 01 02 03 …) as a checksum

## Version 1.5.2

- **Bookmarks now cover the whole selection**, including rectangle (block) selections. Before, only one cell was marked
- **Removing bookmarks**: right-click the bookmarked bytes → **Remove bookmark**, press **Ctrl+Shift+B**, use **✕ Remove** or right-click in the Bookmarks tab, or use **Bookmarks → Remove all**
- **More tools on right-click** in the hex view: add / edit / remove bookmark, find these bytes in the file, copy offset, go to offset, fill, swap bytes 16-bit, checksum calculator, fix checksums, strings panel

## Version 1.5.1

- The update window shows the **complete version history in one list**, newest first. New versions are marked **★ NEW** and yours is marked **← installed**

## Version 1.5.0

- **Single file / compare switch**: the **▣ Single** button (or **Ctrl+1**) shows one file at full height and hides the compare tools. **⧉ Compare** (or **Ctrl+2**) brings back both panes. In single view, **F6** switches which file is shown. The choice is remembered
- Dropping two files at once, or opening two from the command line, switches to compare view automatically
- **Help → Version history** shows every version's changes, even offline
- The toolbar is tidier: the light / dark switch (☀ / ☾) is now in the status bar, and ⟳ checks for updates. Help is in the **Help** menu and **F1**

## Version 1.4.1

- **Menu bar** with every command and setting: **File · Edit · Search · Compare · Bookmarks · View · Tools · Checksum · Settings · Help**
- Each menu item shows its **keyboard shortcut** (Ctrl+O, Ctrl+S, F3, F8, F9, Ctrl+B, Ctrl+T…)
- Settings are in one place: auto-update check, .orig backup, fix checksums on save, synced scrolling, block selection, light / dark theme
- Help menu: shortcuts, check for updates, report a bug, donate, website, about
- The theme button in the toolbar is now a compact **☀ / ☾**

## Version 1.4.0

- **Recent files**: the **▾** button next to Open shows your last 12 files, and one click opens one
- **Window position and size are remembered**, including maximised and which monitor
- **Bookmarks with notes** (**Ctrl+B**): coloured underline on the bytes, the note appears when you hover, and the **Bookmarks** tab lists them so you can jump, edit, delete, export or import. They're saved per file and come back the next time you open it
- **Search highlights every match**, with a count ("12 found" · "Match 3 / 12"), **F3 / Shift+F3** for next and previous, marks in the scrollbar, and **Esc** to clear
- **Light / dark theme**: the **☀ Light / ☾ Dark** button switches instantly and the choice is remembered
- **Strings panel** (**Ctrl+T**): every readable text in the dump, with **VINs** detected even when reversed, a filter box, and click to jump
- **Backup on save**: the first save keeps the original as **name.orig.bin**. It can be turned off in Tools ▾
- The side panel now has tabs: **Inspector · Bookmarks · Strings**

## Version 1.3.2

- The window now opens **centred on the screen** and always fits the screen, including laptops and high-DPI displays
- **Report bug** and **Donate** are now bright pill buttons that gently blink, so they're easy to see
- The bug report window opens in the centre of the screen

## Version 1.3.1

- **⚑ Report bug** in the status bar sends a description, an optional contact, the app and Windows version, the error log and optionally the open dumps straight to the developer
- After a crash, the error window offers to send a bug report
- **♥ Donate** in the status bar opens PayPal to support Hex Editor

## Version 1.3.0 — Checksums

- **Automatic checksum detection** when a dump is opened. It works out the block size, checksum position and algorithm from the file itself:
  - Sum8 / Sum16 / Sum32, sum of 16-bit words, two's complement, inverted, sum + constant, XOR
  - CRC-8 (incl. SAE-J1850, AUTOSAR), CRC-16 (ARC, MODBUS, CCITT, XMODEM, KERMIT, X-25), CRC-32 (incl. MPEG-2, BZIP2)
  - It is only applied automatically when the match is strong. Blank, repeated and non-matching blocks are ignored
- **Checksum bytes are framed**: green when correct, red when wrong after editing. Broken blocks are also marked in the scrollbar
- **F9 fixes all wrong checksums** in one step (Ctrl+Z undoes it)
- **Before saving**, you are asked to fix wrong checksums. This can also be set to always fix
- **Tools ▾ → Checksum**: Auto-detect (with a list of candidates and confidence), Calculator for any selection, and saving or applying your own **presets** per module

## Version 1.2.0 — EEPROM tools

- **Tools ▾** button in each pane:
  - Swap bytes 16-bit (AB CD → BA DC), swap words 32-bit, reverse 32-bit, for the selection or the whole file
  - Fill the selection, block or whole file with any byte (FF, 00…)
  - Resize or pad to a chip size (24Cxx, 93Cxx, 95xxx, 25xx SPI flash). Padding uses FF
  - Split into 2, 4 or 8 parts. De-interleave into even and odd bytes. Interleave or join panes A + B
- **Chip detection**: the file info line shows the matching chips for the dump size (e.g. 24C08 · 93C76 · 95080)
- **Bad-read warnings**: blank dumps (all FF or all 00), and data that repeats, which points to the wrong chip type in the programmer (for example a 24C04 read as 24C08)

## Version 1.1.2

- Text search (Ctrl+F) now ignores letter case, including Cyrillic and accented letters

## Version 1.1.1

- Release notes in the update window are now shown as clean text
- Nicer "drop a file" hint in empty panes

## Version 1.1.0

- **Update check**: looks for a new version on GitHub at startup (can be turned off) and through the **⟳ Updates** button
- **One-click update**: downloads the new version, checks its SHA-256, replaces the program and restarts with your files reopened
- **Close** button for each pane (Ctrl+W)
- Rectangular (block) selection, editable Inspector values, and direct typing in the hex and text columns
