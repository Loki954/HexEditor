## Hex Editor 1.2.0 — EEPROM tools

- **Tools ▾** button in each pane:
  - Swap bytes 16-bit (AB CD → BA DC), swap words 32-bit, reverse 32-bit, for the selection or the whole file
  - Fill the selection, block or whole file with any byte (FF, 00…)
  - Resize or pad to a chip size (24Cxx, 93Cxx, 95xxx, 25xx SPI flash). Padding uses FF
  - Split into 2, 4 or 8 parts. De-interleave into even and odd bytes. Interleave or join panes A + B
- **Chip detection**: the file info line shows the matching chips for the dump size (e.g. 24C08 · 93C76 · 95080)
- **Bad-read warnings**: blank dumps (all FF or all 00), and data that repeats, which points to the wrong chip type in the programmer (for example a 24C04 read as 24C08)
