# Star-Ocean-2
An attempt to create an English patch for Star Ocean Second Evolution (Vita).

# Extracting Files
1. Download the following tools (as needed):
   - [pkg2zip](https://github.com/mmozeiko/pkg2zip/releases)
   - [_decrypt.exe and psvpfsparser-win64.exe](https://gbatemp.net/threads/release-decrypt-and-launch-psn-store-vita-games-without-plugins.548878/)
   - [Total Commander](https://totalcmd.net/plugring/totalcmd.html)
   - [PSARC plugin for Total Commander](https://totalcmd.net/plugring/PSARC.html)
   - [wxMEdit](https://wxmedit.github.io/downloads.html)
   - [quickbms](http://aluigi.altervista.org/quickbms.htm) to unpack `APAC` files
1. Run this command `pkg2zip.exe so2.pkg` to get `STAR OCEAN Second Evolution [PCSG00714] [JPN].zip`
  ![screenshot](img/so2_01.png)
1. Extract the `zip` file.  The contents should look like this
   ```
    \---app
        \---PCSG00714
            |   eboot.bin
            |   so2psv.psarc
            |
            +---GXM
            |   \---save
            |           ClearIcon.png
            |           EmptyIcon.png
            |           SaveIcon.png
            |
            +---sce_module
            |       libc.suprx
            |       libfios2.suprx
            |       libult.suprx
            |
            +---sce_pfs
            |       files.db
            |       pflist
            |       unicv.db
            |
            \---sce_sys
                |   clearsign
                |   icon0.png
                |   keystone
                |   param.sfo
                |   pic0.png
                |
                +---about
                |       right.suprx
                |
                +---livearea
                |   \---contents
                |           bg.png
                |           button.png
                |           template.xml
                |
                +---package
                |       body.bin
                |       head.bin
                |       stat.bin
                |       tail.bin
                |       temp.bin
                |
                \---trophy
                    \---NPWR09638_00
                            TROPHY.TRP
   ```

1. Copy `work.bin` into `PCSG00714\sce_sys\package` and run this command to decrypt files: `_decrypt.exe PCSG00714`
  ![screenshot2](img/so2_decrypt.gif)

1. Unpack `PCSG00714_dec\so2psv.psarc` with [Total Commander](https://totalcmd.net/) and [PSARC Plugin](https://totalcmd.net/plugring/PSARC.html)
  ![screenshot2](img/so2_psarc01.png)

1. Unpacking `PCSG00714_dec\so2psv.psarc` should get you a folder called `GMX`, see contents here: [so2psv.psarc.txt](so2psv.psarc.txt)

1. Use [`QuickBMS`](http://aluigi.altervista.org/papers/quickbms.zip) with [`star_ocean_kcpa.bms`](http://aluigi.altervista.org/bms/star_ocean_kcpa.bms) to extract `APAC` files.  Sample command to extract a single file: `quickbms.exe -d star_ocean_kcpa.bms 017_ArliaW_20_branch001.apac`
  ![screenshot3](img/so2_quickbms01.png)

1. A hex editor like `wxMEdit` can be used to look at the contents.

## Hacker Note 1
> Note for anyone trying to patch ENG text. Entire game is one `psarc` file. It's easily extracted and reencrypted. Structure appears same as PSP ver, so, ~~I think it is possibly easy to patch official PSP ENG translation~~.
