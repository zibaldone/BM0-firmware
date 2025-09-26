<picture>
    <img
        alt="A pixel art of BMO from Adventure Time"
        src="/.github/assets/BMO-Passport.png">
</picture>

# BM0 Firmware
Basically a reskin of the official Flipper Zero Firmware with BMO assets & some minor add-ons.

## Changes
- Redrew all assets containing the Flipper mascot with BMO.
- Added RGB Backlighting mode (Choose a static backlight color or go with an animated rainbow transition)
- Changed default font 'u8g2_font_haxrcorp4089_tr' to 'u8g2_font_squeezed_b7_tr' for something more bold.

* **Note for font**: <code>u8g2</code> directory has been updated with more fonts in order for BM0 to operate with a typography originally unavailable within the default library. Specifically, <code>u8g2_font.c</code>, <code>u8g2_fonts.c</code> & <code>u8g2h.h</code> have been changed to reflect this.

If you want to know how to change your Flipper Zero's font (and upgrade the font libary while you're at it): [Font doc](/documentation/Fonts.md)

If you want to add BMO-themed animations onto your Flipper Zero, I have some here!: https://github.com/zibaldone/BM0-Animations

## Cloning source code
Make sure you have enough space and clone the source code:

```shell
git clone --recursive https://github.com/zibaldone/BM0-firmware.git
```

## Building

Build firmware using Flipper Build Tool:

```shell
./fbt
```

Next, we're going to flash this firmware onto your Flipper Zero:

## Option 1: Flashing firmware using an in-circuit debugger

Connect your in-circuit debugger to your Flipper and flash firmware using Flipper Build Tool:

```shell
./fbt flash
```

## Option 2: Flashing firmware using USB (aka connecting your Flipper Zero to your computer via a USB cable)

Make sure your Flipper is on, and your firmware is functioning. Connect your Flipper with a USB cable and flash firmware using Flipper Build Tool:

```shell
./fbt flash_usb_full
```
# Project structure

- `applications`        - Applications and services used in firmware
- `applications_users`  - Place for your additional applications and services
- `assets`              - Assets used by applications and services
- `documentation`       - Documentation generation system configs and input files
- `furi`                - Furi Core: OS-level primitives and helpers
- `lib`                 - Our and 3rd party libraries, drivers, tools and etc...
- `site_scons`          - Build system configuration and modules
- `scripts`             - Supplementary scripts and various python libraries
- `targets`             - Firmware targets: platform specific code

Also, see `ReadMe.md` files inside those directories for further details.

If you thought this was all neat and wanted to donate some dabloons: [Ko-fi](https://ko-fi.com/zackarysanchez)