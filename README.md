# ZMK Shield Configuration Documentation

This folder (`board/shields/my_keyboard`) contains the necessary configuration files for a keyboard.

Note: "shield" refers to the actual keyboard PCB or circuit board that connects to your microcontroller board (e.g. nice!nano).

## File Structure (split keyboard example)

```sh
boards/shields/my_keyboard/
├── boards/
│   └── nice_nano_v2.overlay   # Board-specific device tree overlay (SPI, trackball)
├── Kconfig.defconfig          # Default config for shield (names, vars, etc.)
├── Kconfig.shield             # Shield configuration options (minimal?)
├── my_keyboard_left.conf      # [low-power, BLE, pointing devices, display, etc]
├── my_keyboard_left.overlay   # Left half-specific device tree overlay
├── my_keyboard_right.conf     # Mirrors 'left.conf'
├── my_keyboard_right.overlay  # Mirrors 'left.overlay'
├── my_keyboard.dtsi           # Shared device tree configurations: [matrix transform]
└── my_keyboard.keymap         # Keymap
├── my_keyboard.zmk.yml        # Shield metadata
```

`boards/nice_nano_v2.overlay` and `my_keyboard_left.overlay` are combined to create the full device tree overlay.

## Customization

Adjust the CPI setting in the overlay file to change trackball sensitivity.

## Usage

To use this shield configuration:

1. Place these files in your ZMK config repo under `board/shields/my_keyboard/`
2. Update your build.yaml to include your shield:

   ```yaml
   board: nice_nano_v2
   shield: my_keyboard
   ```

3. Build your firmware using the standard ZMK build process.

## Notes

- Keyboard matrix gpios can go in `.dtsi` or `my_keyboard_left.overlay` (see zmk/microdox for example of the second).
