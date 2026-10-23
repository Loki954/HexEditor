## Hex Editor 1.3.0 — Checksums

- **Automatic checksum detection** when a dump is opened. It works out the block size, checksum position and algorithm from the file itself:
  - Sum8 / Sum16 / Sum32, sum of 16-bit words, two's complement, inverted, sum + constant, XOR
  - CRC-8 (incl. SAE-J1850, AUTOSAR), CRC-16 (ARC, MODBUS, CCITT, XMODEM, KERMIT, X-25), CRC-32 (incl. MPEG-2, BZIP2)
  - It is only applied automatically when the match is strong. Blank, repeated and non-matching blocks are ignored
- **Checksum bytes are framed**: green when correct, red when wrong after editing. Broken blocks are also marked in the scrollbar
- **F9 fixes all wrong checksums** in one step (Ctrl+Z undoes it)
- **Before saving**, you are asked to fix wrong checksums. This can also be set to always fix
- **Tools ▾ → Checksum**: Auto-detect (with a list of candidates and confidence), Calculator for any selection, and saving or applying your own **presets** per module
