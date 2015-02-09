aml-imgpack
===========

Resource packer/unpacker for Amlogic Logo image files

Help
----

```
$ ./aml-imgpack.py --help
usage: aml-imgpack.py [-h] [--unpack] [--pack PACK] file [file ...]

Pack and unpack amlogic uboot images

positional arguments:
  file         an integer for the accumulator

optional arguments:
  -h, --help   show this help message and exit
  --unpack     Unpack logo.img file
  --pack PACK  Unpack logo.img file
```

Listing assets in an image
--------------------------

```
$ ./aml-imgpack.py logo.img
Listing assets in logo.img
AmlResImgHead(crc=0x952fde3b version=2 imgSz=1160640 imgItemNum=8 alignSz=16)
    AmlResItem(name=upgrade_unfocus start=0x240 size=184)
    AmlResItem(name=upgrade_success start=0x300 size=180072)
    AmlResItem(name=upgrade_error start=0x2c270 size=180072)
    AmlResItem(name=upgrade_fail start=0x581e0 size=180072)
    AmlResItem(name=bootup start=0x84150 size=259272)
    AmlResItem(name=upgrade_bar start=0xc3620 size=184)
    AmlResItem(name=upgrade_logo start=0xc36e0 size=180072)
    AmlResItem(name=upgrade_upgrading start=0xef650 size=180072)
```

Unpacking an image
------------------

Note that the assets name are appended with a `.bmp` extension to make edition easier.

```
$ ./aml-imgpack.py --unpack logo.img
Unpacking assets in logo.img
  Unpacking upgrade_unfocus
  Unpacking upgrade_success
  Unpacking upgrade_error
  Unpacking upgrade_fail
  Unpacking bootup
  Unpacking upgrade_bar
  Unpacking upgrade_logo
  Unpacking upgrade_upgrading
```

Packing an image
----------------

Note that any `.bmp` will be stripped from the asset name.

```
$ python aml-imgpack.py --pack out.img *.bmp
Packing files in out.img:
  bootup (259272 bytes)
  upgrade_bar (184 bytes)
  upgrade_error (180072 bytes)
  upgrade_fail (180072 bytes)
  upgrade_logo (180072 bytes)
  upgrade_success (180072 bytes)
  upgrade_unfocus (184 bytes)
  upgrade_upgrading (180072 bytes)
```
