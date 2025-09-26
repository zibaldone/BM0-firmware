# Fonts (and how to change them)

The Flipper Zero uses **U8g2**(https://github.com/olikraus/u8g2), a library of fonts for monochrome displays. For stock Flipper Zero firmware, it uses a library version from 2016.

BM0-firmware uses the 2025-version of this library not only for a more expansive collection of fonts to choose from, but also to allow the firmware to use a font which didn't exist during the 2016-version:

[Olikraus' wiki list of available fonts as of 2025](https://github.com/olikraus/u8g2/wiki/fntlist8)

## Which files are we targeting

- (Starting from the root directory) **lib** > u8g2 > <code>u8g2.h</code>
- (Starting u8g2_font_squeezed_b7_trfrom the root directory) **lib** > u8g2 > <code>u8g2_font.c</code>
- (Starting from the root directory) **lib** > u8g2 > <code>u8g2_fonts.c</code>
- (Starting from the root directory) **applications** > services > gui > <code>canvas.c</code>

The first three files will be for updating the library with more fonts, while <code>canvas.c</code> will be where we'll change the actual font itself.

## Step 1: Update the library

Honestly this is a lot easier than it sounds. We're simply downloading the latest copies of [u8g2.h](https://github.com/olikraus/u8g2/blob/master/csrc/u8g2.h), [u8g2_font.c](https://github.com/olikraus/u8g2/blob/master/csrc/u8g2_font.c) & [u8g2_fonts.c](https://github.com/olikraus/u8g2/blob/master/csrc/u8g2_fonts.c) and replacing the old files from the stock Flipper Zero's library (again, I've listed where each file's location is above).

## Step 2: Change that font!

Bear with me on this, but go to your code editor of choice, and look up this specific chunk of code:

```shell
void canvas_set_font(Canvas* canvas, Font font) {
    furi_check(canvas);
    u8g2_SetFontMode(&canvas->fb, 1);
    if(font == FontPrimary) {
        u8g2_SetFont(&canvas->fb, u8g2_font_helvB08_tr);
    } else if(font == FontSecondary) {
        u8g2_SetFont(&canvas->fb, u8g2_font_haxrcorp4089_tr);
    } else if(font == FontKeyboard) {
        u8g2_SetFont(&canvas->fb, u8g2_font_profont11_mr);
    } else if(font == FontBigNumbers) {
        u8g2_SetFont(&canvas->fb, u8g2_font_profont22_tn);
    } else {
        furi_crash();
    }
}
```

Got it? Now let's get even more specific, we're going to look at this piece of code:

```shell
    } else if(font == FontSecondary) {
        u8g2_SetFont(&canvas->fb, u8g2_font_haxrcorp4089_tr);
```

**Right here** is where we'll change the font to whatever we want (in this case, to `u8g2_font_squeezed_b7_tr`)

The stock default font Flipper Zero uses is called `u8g2_font_haxrcorp4089_tr`. To change this to our selected font of choice, just simply switch out the name of the old with the new (although just like the default font, choose one that's under the "7 Pixel Height" category under the wiki font list). Like this:

```shell
    } else if(font == FontSecondary) {
        u8g2_SetFont(&canvas->fb, u8g2_font_squeezed_b7_tr); //default font: u8g2_font_haxrcorp4089_tr
```

Commenting what the default font was previous is optional but very helpful incase you ever want to revert any changes.

That's it, now you're a pro at changing fonts for your Flipper Zero!