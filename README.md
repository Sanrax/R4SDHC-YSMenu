Repacked (and fixed) version of YSMenu 7.06, meant for Original R4SDHC flashcarts from r4sdhc.com. Fixed YSMenu auto-boot, DLDI, and soft-reset.

## Notes About Fixes

On R4SDHC carts, you would normally get stuck after "Creating TTMenu.sys" with a white screen when booting into YSMenu from the official RGF YSMenu download, because there's a configuration error in the R4SDHC-YSMenu kernel shipped in RGF's 7.06 7z. RGF set up YSMenu to auto-chainload from the stock R4SDHC kernel, by naming it `default.nds`. this is all well and good, but YSMenu *also* autoboots any file named `default.nds`, just like the stock r4sdhc 1.34 kernel.

That's right - what happens is after the stock kernel chainloads YSMenu by booting `default.nds`, YSMenu then proceeds to autoboot itself in a loop infinitely, and crashes to a white screen.

The fix is to edit the YSMenu.ini and change the autoboot file's name to something other than default.nds. In the download I provided above, I edited it to `noboot.nds`.

A working DLDI file for this cart was also missing, causing homebrew to be broken. This has been resolved.

Soft-reset was also broken due to a missing TTMenu.dat on SD root. This has also been fixed.

## Setup Instructions

Grab a 4GB or smaller SD and format the SD card you are using by following this guide: https://wiki.hacks.guide/wiki/Formatting_an_SD_card

Download the fixed YSMenu 7.06 for R4SDHC carts: https://github.com/Sanrax/R4SDHC-YSMenu/releases/download/v7.06/R4SDHC-YSMenu-7.06_R2.zip

Next, extract *the contents* of the downloaded kernel zip to your SD card.

Place any .nds game ROMs you'd like to play into the `Games` folder

Insert the SD back into the cart, plug the cart into the DS, and see if it boots into the menu.

---

Note: This cart's SD I/O implementation is wonky since its SDHC I/O code is closely based off of the original R4's I/O, meant for SD class cards rather than SDHC ones. This causes the cart to be unstable with SD cards bigger than 4GB.
