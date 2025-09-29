# Passport Name (and how to change it)

Passport names are saved under the <code>furi_hal_version.c</code> file.

To get there:
(Starting from the root directory) **targets** > f7 > furi_hal > <code>furi_hal_version.c</code>

**Now go to your code editor of choice, and look up this specific chunk of code:**


```shell
const char* furi_hal_version_get_name_ptr(void) {
    return ""*furi_hal_version.name == 0x00 ? NULL : furi_hal_version.name"";
}
```

We're going to look at this piece of code:

```shell
    return ""*furi_hal_version.name == 0x00 ? NULL : furi_hal_version.name"";
```

Change it to whatever name you want, within <code>""</code>. For example:
```shell
const char* furi_hal_version_get_name_ptr(void) {
    return "CUSTOM_NAME";
}
```

**Now save file, compile firmware and flash it onto your Flipper zero**

