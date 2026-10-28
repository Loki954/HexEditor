# Hex Editor

A fast, dark-themed, dual-pane **hex editor for Windows** with built-in file comparison.
Open two files, see every differing byte at a glance, and copy bytes from one file to the other with one click.

![Hex Editor](docs/screenshot.png)

## Download

**[⬇ HexEditor.exe — latest release](https://github.com/Loki954/HexEditor/releases/latest/download/HexEditor.exe)**

It is a single ~100 KB file with no installer. It runs on Windows 10/11 using the built-in .NET Framework 4.
The program checks for new versions on its own and can update itself.

> On first launch, Windows SmartScreen may warn that the app is unrecognised. Click **More info → Run anyway**.

## Features

- **Menu bar** with every command and setting, and the shortcut shown next to each item
- **Single file or compare view**: switch with Ctrl+1 / Ctrl+2 or the ▣ / ⧉ button

- **Two panes (A / B)**: differences are shown in red, and bytes past the end of the shorter file in brown
- **Compare top / bottom or side by side** (left / right) — switch in Settings or the Compare menu
- **Copy A → B / B → A** copies the selection (or the difference under the cursor) at the same offset
- **Next / previous difference** (F8 / Shift+F8), with a difference map in the scrollbar
- **Synchronised scrolling** of both panes
- **Block (rectangular) selection** by mouse drag; Alt+drag gives a linear selection
- **Direct editing**: type hex (works with any keyboard layout) or text, in insert or overwrite mode
- **Inspector** shows Int8–Int64, Float and Double in LE/BE. Double-click a value to edit it
- **Clipboard**: copy/paste as hex or text, including block copy/paste
- **Find** (Ctrl+F, hex or text), **Go to offset** (Ctrl+G), **Undo/Redo**
- **Open / Save / Save as / Close** for each pane, plus drag & drop
- **Search highlights every match**, with a count, F3 / Shift+F3 for next / previous, and marks in the scrollbar
- **Bookmarks with notes** (Ctrl+B) on any selection, saved per file and restored automatically. Remove one with right-click or Ctrl+Shift+B; export / import
- **Right-click tools** in the hex view: bookmarks, find these bytes, copy offset, go to, fill, swap, checksum calculator
- **Readable text box** under the Inspector, filled automatically; click a line to jump, Ctrl+C to copy, double-click to edit. Finds normal and CamelCase text, **UTF-16 (wide) text**, part numbers and ECU types, and VINs even when reversed — random data and fill patterns are filtered out. Full list in the **Strings** tab (Ctrl+T)
- **Recent files** (▾ next to Open), and the window size and position are remembered
- **Light / dark theme**
- **Backup on save**: the original is kept as `name.orig.bin` the first time you save
- **Auto-update** from GitHub Releases, verified with SHA-256

### Checksums

- **Auto-detected** when a dump is opened: Sum8/16/32, word sums, two's complement, inverted, XOR, CRC-8/16/32 variants, plus block size and checksum position
- Checksum bytes are **framed green / red**, and **F9** fixes every wrong checksum in one step
- You are **asked before saving** if checksums are wrong
- **Calculator** for any selection, and your own **presets** per module

### EEPROM tools (Tools ▾ in each pane)

- **Byte swap 16-bit**, **word swap 32-bit** and **reverse 32-bit** for the selection or the whole file
- **Fill** with FF / 00 / any byte, and **resize / pad** to a chip size
- **Split** into 2, 4 or 8 parts, **de-interleave** into even and odd bytes, **interleave** or **join** A + B
- **Chip detection** from the dump size: 24Cxx, 93Cxx, 95xxx and 25xx SPI flash
- **Bad-read warnings**: blank dumps (all FF or all 00), and repeating or mirrored data, which points to the wrong chip type in the programmer

See the full **[version history](CHANGELOG.md)**.

## Keyboard shortcuts

| Keys | Action |
|---|---|
| Ctrl+O / Ctrl+S / Ctrl+Shift+S / Ctrl+W | Open / Save / Save as / Close (active pane) |
| Ctrl+1 / Ctrl+2 | Single file / compare two files |
| F6 | Switch pane A ⇄ B (single view: show the other file) |
| Tab | Switch hex ⇄ text column |
| F8 / Shift+F8 | Next / previous difference |
| Ctrl+Shift+↓ / Ctrl+Shift+↑ | Copy selection A → B / B → A |
| Ctrl+C / Ctrl+X / Ctrl+V | Copy / cut / paste |
| Insert | Toggle insert / overwrite |
| Ctrl+Z / Ctrl+Y | Undo / redo |
| Ctrl+F / F3 / Shift+F3 | Find / next / previous match (Esc clears highlights) |
| Ctrl+B / Ctrl+Shift+B | Add bookmark / remove bookmark at cursor |
| Ctrl+T | Strings panel |
| Ctrl+G | Go to offset |
| F1 | Help |

Command line: `HexEditor.exe file1 file2`

## Support

Found a problem? Click **⚑ Report bug** in the status bar of the app.

If Hex Editor saves you time, you can support it here: **[♥ Donate via PayPal](https://www.paypal.com/donate/?hosted_button_id=7AJ4UGND5D3DC)**

---

© 2026 **Loki954** · [www.loki954.com](https://www.loki954.com) · All rights reserved.
