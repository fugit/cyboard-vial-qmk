# Cyboard Imprint — QMK Firmware

## Keyboard

- **Model:** Cyboard Imprint (wired, Vial-QMK)
- **Variant:** `imprint_number_row_2key_bottom_row`
- **UID:** `0x70FC163076B4CCC4`
- **LEDs:** 124 total (62 per split half: 32 keylight + 30 underglow), WS2812 RGB Matrix, `vialrgb` enabled
- **MCU:** RP2040

## Key Paths

| Purpose | Path |
|---------|------|
| Keymap | `keyboards/cyboard/imprint/imprint_number_row_2key_bottom_row/keymaps/vial/keymap.c` |
| Vial config | `keyboards/cyboard/imprint/imprint_number_row_2key_bottom_row/keymaps/vial/vial.json` |
| Keyboard config | `keyboards/cyboard/config.h` |
| Keymap config | `keyboards/cyboard/imprint/imprint_number_row_2key_bottom_row/keymaps/vial/config.h` |
| LED layout | `keyboards/cyboard/imprint/imprint_number_row_2key_bottom_row/info.json` |

## Build & Flash

```bash
# Generate clangd compile database (run once, or after changing keyboard/keymap)
qmk generate-compilation-database -kb cyboard/imprint/imprint_number_row_2key_bottom_row -km vial

# Build
qmk compile -kb cyboard/imprint/imprint_number_row_2key_bottom_row -km vial

# Flash: double-tap reset → then run:
# sudo mount /dev/sdc1 /mnt/rp2040 && cp cyboard_imprint_imprint_number_row_2key_bottom_row_vial.uf2 /mnt/rp2040
# Flash both halves separately (disconnect TRRS, flash each via USB)
```

## Per-Layer RGB Lighting

Blue → Silver → White theme (matches mouse pad). Implemented via
`rgb_matrix_indicators_advanced_user()` in `keymap.c`.

| Layer | Purpose  | Color      | HSV              |
|-------|----------|------------|------------------|
| 0     | Base     | Dark Blue  | (153, 255, 255)  |
| 1     | Sym/Nav  | Light Blue | (148, 150, 255)  |
| 4     | Mouse    | White      | (0, 0, 255)      |

## Vial Layout Files

Saved layouts live in `/home/keith/Documents/keith/Vial/`.
Current layout: `vial-layout-20260330-4.vil`

## Neovim / clangd

Run `qmk generate-compilation-database` first — this creates `compile_commands.json`
in the repo root, which clangd uses to resolve QMK's include paths and defines.
