# Borne Keyboard ZMK Configuration

This repository contains the ZMK (Zephyr Mechanical Keyboard) firmware configuration for the Borne split keyboard, including Swedish character support.

## Overview

The Borne is a split keyboard that uses ZMK firmware. This configuration includes:

- Custom keymap layouts for both left and right halves
- Swedish character macros (ö, ä, å)
- Bluetooth connectivity support
- Combo key definitions

## Files Structure

- [`build.yaml`](build.yaml) - Build configuration for both keyboard halves
- [`config/borne.keymap`](config/borne.keymap) - Main keymap configuration
- [`config/keys_se.h`](config/keys_se.h) - Swedish keyboard layout definitions
- [`config/west.yml`](config/west.yml) - West build system configuration
- [`special-characters.keymap`](special-characters.keymap) - Swedish character macros

## Building the Firmware

This repository uses GitHub Actions to automatically build the firmware. The build process is triggered on:

- Push to any branch
- Pull requests
- Manual workflow dispatch

The built firmware files will be available as artifacts in the GitHub Actions workflow runs.

### Manual Build

If you want to build locally, you'll need to set up the ZMK development environment. Refer to the [ZMK documentation](https://zmk.dev/docs/development/setup) for detailed setup instructions.

## Swedish Character Support

The configuration includes macros for Swedish characters:

```c
// ö = U+00D6
diaeresis_o: diaeresis_o {
    label = "diaeresis_o";
    compatible = "zmk,behavior-macro";
    tap-ms = <0>;
    #binding-cells = <0>;
    bindings = <&macro_tap &kp RA(DOUBLE_QUOTES) &kp O>;
};
```

The supported characters are:
- **ö** (diaeresis o)
- **ä** (diaeresis a) 
- **å** (ring a)

## Customization

To customize the keymap:

1. Fork this repository
2. Edit the [`config/borne.keymap`](config/borne.keymap) file
3. Commit and push your changes
4. Download the built firmware from the GitHub Actions artifacts

## Flashing the Firmware

1. Download the firmware files from the GitHub Actions build artifacts
2. Put your keyboard into bootloader mode
3. Copy the appropriate `.uf2` file to the keyboard's mass storage device
4. The keyboard will automatically reboot with the new firmware

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Contributing

Feel free to submit issues and pull requests to improve this configuration!