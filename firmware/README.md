# Firmware

The ZMK firmware for this keyboard lives in a separate repository to enable GitHub Actions builds:

**[custom-keyboard ZMK config](https://github.com/aidancahill/zmk-config)**

> Replace `YOUR_USERNAME` with your GitHub username.

## Flashing

1. Download `zmk.uf2` from the latest GitHub Actions build artifact
2. Double-tap the reset button on the XIAO BLE — a USB drive appears
3. Drag `zmk.uf2` onto the drive
4. Board reboots with new firmware

## Custom ZMK Modules

The firmware repo includes two custom drivers:

- **`zmk,gpio-165`** — 74HC165 PISO shift register driver for reading matrix rows via SPI
- **`zmk,input-analog-joystick`** — Analog joystick driver for mouse cursor and scroll input

## Modifying the Keymap

Edit `config/custom-keyboard.keymap` in the firmware repo. Push to `main` and GitHub Actions will build a new `.uf2` automatically.

See the [ZMK keymap documentation](https://zmk.dev/docs/keymaps) for available behaviors and keycodes.
