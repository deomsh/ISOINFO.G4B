## ISOINFO.G4B v0.7.2 (20240420)

<pre><code>Function 1: Read-out ISO-9660/UDF Descriptors on a device, image-file or blocklist  
Function 2: Read/ find directories/ files or read-out their Directory Records  
Use:        ISOINFO.G4B [SWITCHES] DEVICE|FILE  
Help:       ISOINFO.G4B /?  

SWITCHES  
General:    [--Q] [--HEX] [--BLOCKSIZE=bytes] [--MDBASE=sector] [--INFO]  
ISO 1:      --ISOVDS|--ISOPVD|--BD|--SVD[2]|--VPD|--VDT|--ROOT[2/3]  
ISO 2:      --DIR/RECORD[2/3][RR]=[PATH][name.ext[;n]] [--ATTRIB=DF[-]H] [--CASE] [--DEEP]  
UDF 1:      --VRS|--UDFVDS|--VDS2|--FDS|--AVDP|--PVD|--IUVD|--PD|--LVD|--USD|--LVID|--FSD|--FE|--EFE|--TD|  
              --VAT|--SPT|--MF|--MMF|--MBF|--SBD|--UDFROOT [--MIRROR|--PREVIOUS]  
UDF 2:      --UDFDIR/UDFRECORD=[PATH][filename.ext] [--ATTRIB=DF[-]H[-]0] [--CASE] [--MIRROR|--PREVIOUS]  
              [--MDCOPY|MDMAP=disk_num]  
UDF 3:      --LSN=sector|--LBN=number [--OFFSET=bytes] [--MIRROR|--PREVIOUS]  

REMARKS  
Maximum length of PATH (and FILE) about 510 chars  
All (greyed-out) hex-offsets zero based (ECMA-119 starts at 1, so read '+1')  
ISO-9660 and UDF tested up to 8GB-DVD, UDF up to 465GB-Partition (on Hard Disk)  
On ISO-9660 big-endian values are read-out but only showed if exist and not equal to little-endian value
Joliet is included in ISO-9660!

EXAMPLES  
ISOINFO.G4B (hd0,0)/filename.iso  
ISOINFO.G4B --ISOPVD (0xe0)  
ISOINFO.G4B --UDFVDS (0xe0)  
ISOINFO.G4B --RECORD=FILENAME.EXT;1 (0xe0)  
ISOINFO.G4B --RECORD2=boot.catalog (0xe0)  
ISOINFO.G4B --DIR2=SUBDIR/bo*.c* (0xe0)  
ISOINFO.G4B --UDFRECORD=System\ Volume\ Information (hd0,0)/some.iso  
ISOINFO.G4B --UDFDIR="System Volume Information/" (hd0,0)/some.iso  
ISOINFO.G4B --RECORD=/.. (hd0,0)/some.iso</code></pre>  

### HISTORY

Version 0.7.2  
BUGFIX: ISO-9660 PVD/SVD Root Directory Record always showed with HEX, bug was introduced in v0.7.1 (harmless)  
Version 0.7.1  
BUGFIX: last byte of 'Implementation Use Area' was not displayed (UDF)  
BUGFIX: Output variable 'Rblock' wrong in case of multiple Extents (UDF)  
Small Output-related changes (textual only)  
NEW: view Directory Record of the root of a directory with '--RECORD[2/3][RR]=[PATH].' (ISO-9660)  
NEW: view Directory Record of Parent Directory with '--RECORD[2/3][RR]=[PATH]..' (ISO-9660)  
NEW: view File Identifier Descriptor and (Extended) File Entry of Parent Directory with '--UDFRECORD=[PATH]..' (UDF)  

Version 0.7  
First published version

### ISO-9660

Supported:  
ISO-9660 (all levels), El Torito, Joliet, Rock Ridge  
  
Unsupported:  
PATH length above 510 chars  
Path Table  
UTF-8 characters  
Extended Attributes outside System Use Area  
Multi-Extent files  
Interleave Gap  

### UDF

Supported:  
All UDF-versions (v2.60 untested on optical media)  
  
Unsupported:  
PATH length above 510 chars  
More than one Volume/ (real) Partition  
Higher Character set's than OSTA CS0  
Multi-session  
Named Streams (except first System Stream)  
Not-embedded Extended Attributes  
WORM  
Secure-UDF  

#### USED SOURCES ISO-9660

ECMA 119 4th Edition / June 2019: https://ecma-international.org/wp-content/uploads/ECMA-119_4th_edition_june_2019.pdf  
Clayton Summers' Introduction to ISO-9660: https://hwiegman.home.xs4all.nl/fileformats/C/cdrom/iso9660.pdf  
El Torito spec: https://pdos.csail.mit.edu/6.828/2018/readings/boot-cdrom.pdf  
System Use Sharing Protocol 1.12 specs: https://docplayer.net/29621206-Ieee-p1281-system-use-sharing-protocol-draft-standard-version-1-12-adopted.html  
Rock Ridge 1.09 specs: http://web.archive.org/web/20230826015627/http://ftpmirror.your.org/pub/misc/bitsavers/projects/cdrom/Rock_Ridge_CD_Proposal_199108.pdf  
Rock Ridge 1.10 specs: https://archive.org/details/enf_pobox_Rrip  
Rock Ridge 1.12 specs: https://www.nextcomputers.org/NeXTfiles/Projects/CD-ROM/Rock_Ridge_Interchange_Protocol.pdf  
https://wiki.osdev.org/ISO  
https://problemkaputt.de/psxspx-cdrom-iso-volume-descriptors.htm  
https://problemkaputt.de/psxspx-cdrom-iso-file-and-directory-descriptors.htm  
ISO-9660 part (ppt): https://dokumen.tips/download/link/07udf-iso9660-file-system.html  
El Torito info (not free): https://www.scribd.com/document/435188636/food  
https://betterexplained.com/articles/unicode/  
https://ultibo.org/wiki/Unit_CDFS  
Date/ Time format: https://superuser.com/questions/559031/how-to-find-out-when-a-disc-dvd-has-been-written-burned  
https://handwiki.org/wiki/TRANS.TBL  
https://dev.lovelyhq.com/libburnia/web/wikis/Aaip  
SEGA CD-XA specs: https://antime.kapsi.fi/sega/files/ST-040-R4-051795.pdf  

#### USED SOURCES UDF
ECMA 167 3rd edition, June 1997: https://ecma-international.org/wp-content/uploads/ECMA-167_3rd_edition_june_1997.pdf  
ISO-9660/ UDF Bridge: https://ecma-international.org/wp-content/uploads/ECMA_TR-71_1st_edition_february_1998.pdf  
All UDF specs: http://www.osta.org/  
https://wiki.osdev.org/UDF  
https://en.wikipedia.org/wiki/Universal_Disk_Format  
Wenguang's Introduction to Universal Disk Format (UDF): https://web.archive.org/web/20140512230150/https://sites.google.com/site/udfintro/  
About offset of Metadata Partition/ embedded directory: https://stackoverflow.com/questions/8832031/udf-filesystem-reading-bluray-metadata-partition-libdvdread-with-iso-images    
https://www.rodneybeede.com/programming/understanding_the_udf_file_system_specification.html  
ISO-9660/ UDF Bridge (ppt): https://dokumen.tips/download/link/07udf-iso9660-file-system.html  
https://betterexplained.com/articles/unicode/  
https://alt.os.development.narkive.com/PVcJX551/iso-9960-and-udf  
Date/ Time format: https://superuser.com/questions/559031/how-to-find-out-when-a-disc-dvd-has-been-written-burned  
https://docs.huihoo.com/doxygen/linux/kernel/3.7/osta__udf_8h_source.html  
Extended File Entries: https://github.com/clalancette/pycdlib/issues/94  
Stream Directory: https://patentimages.storage.googleapis.com/ae/15/ca/7aa2dca80b7392/US07324740-20080129-D00046.png  
https://bsdio.com/edk2/docs/master/_mde_pkg_2_include_2_industry_standard_2_udf_8h_source.html  
Windows 10 quirks: https://lore.kernel.org/lkml/96e1ea00-ac12-015d-5c54-80a83f08b898@digidescorp.com/T/  
Rare: http://netwinder.osuosl.org/users/a/andrewm/udf/docs/CDUDF190.pdf  


#### VARIOUS TEST ISO'S
ISO-9660 with various extensions: https://github.com/vdechenaux/iso-9660/tree/master/tests/fixtures  
ISO-9660 with UTF8 characters: https://github.com/barneygale/isoparser/tree/master/isoparser/test  
ISO-9660 with many extensions (including Apple): https://github.com/KBNLresearch/isolyzer/tree/main/testFiles  
UDF 1.50-2.60 test iso's: https://sourceforge.net/p/sevenzip/patches/389/  
UDF 1.02 with single file: https://sourceforge.net/p/sevenzip/bugs/964/  
UDF on bluray: http://www.av-info.eu/download_dvd+bluray.html  
UDF 2.01 filesystem with ISO 9660 UDFONLY.TXT: https://github.com/clalancette/pycdlib/issues/94  
UDF with mounttab (absolute link): https://bugs.freebsd.org/bugzilla//show_bug.cgi?id=163065  
Test-iso from DVD+R with true UDF Multi-Session: https://drive.google.com/drive/folders/1qbQghX-uem0xR3Y1yx94sy-HT5Q8gRs9?usp=sharing  

### SCREENSHOTS

ISO-9660/ UDF Descriptors on Windows 10 iso

![ISOINFO G4B (0xe0) ISO-9660 UDF-Bridge Windows_10 iso attached in VBOX 7 ISO PVD I](https://github.com/deomsh/ISOINFO.G4B/assets/67714723/d500b58c-3c30-4dc1-ab6b-7fd7f9f25ff2)
![ISOINFO G4B (0xe0) ISO-9660 UDF-Bridge Windows_10 iso attached in VBOX 7 ISO BD+Booting Catalog II](https://github.com/deomsh/ISOINFO.G4B/assets/67714723/148a0742-0b4c-4ffd-8ab9-18c86f3e8ae9)
![ISOINFO G4B (0xe0) ISO-9660 UDF-Bridge Windows_10 iso attached in VBOX 7 ISOVDT + UDF Extended Descriptors + UDFAVDP III](https://github.com/deomsh/ISOINFO.G4B/assets/67714723/9fabf3b8-4dad-4ba4-bb08-00c614594649)
![ISOINFO G4B (0xe0) ISO-9660 UDF-Bridge Windows_10 iso attached in VBOX 7 UDFPVD IV](https://github.com/deomsh/ISOINFO.G4B/assets/67714723/37d5baea-aebe-4a7a-96cd-16d7c4d55aec)
![ISOINFO G4B (0xe0) ISO-9660 UDF-Bridge Windows_10 iso attached in VBOX 7 UDFIUVD V](https://github.com/deomsh/ISOINFO.G4B/assets/67714723/329f7f81-ae30-40d7-b626-c8ee9b44d1e9)
![ISOINFO G4B (0xe0) ISO-9660 UDF-Bridge Windows_10 iso attached in VBOX 7 UDFLVD part 1 VI](https://github.com/deomsh/ISOINFO.G4B/assets/67714723/a4e607dd-7054-4770-abe2-d46464fe6a10)
![ISOINFO G4B (0xe0) ISO-9660 UDF-Bridge Windows_10 iso attached in VBOX 7 UDFLVD partition map UDFPD VII](https://github.com/deomsh/ISOINFO.G4B/assets/67714723/3b9ee9af-4d06-4b38-9ffa-48ff0f6aa470)
![ISOINFO G4B (0xe0) ISO-9660 UDF-Bridge Windows_10 iso attached in VBOX 7 UDFUSD UDFTD UDFLVID VIII](https://github.com/deomsh/ISOINFO.G4B/assets/67714723/da0c7d5d-71d9-4d72-8011-7e294d4f370b)
![ISOINFO G4B (0xe0) ISO-9660 UDF-Bridge Windows_10 iso attached in VBOX 7 UDFLVID UDFTD + UDFFSD (part) IX](https://github.com/deomsh/ISOINFO.G4B/assets/67714723/8f47dbe5-6600-421d-b1ae-4980be1f7624)
![ISOINFO G4B (0xe0) ISO-9660 UDF-Bridge Windows_10 iso attached in VBOX 7 UDFFSD + UDFFD (part) X](https://github.com/deomsh/ISOINFO.G4B/assets/67714723/4eac71b7-3584-4179-9ca6-9073ad89c237)
![ISOINFO G4B (0xe0) ISO-9660 UDF-Bridge Windows_10 iso attached in VBOX 7 UDFFD (part 2) XI](https://github.com/deomsh/ISOINFO.G4B/assets/67714723/0a24aa33-3e74-4cbd-84cc-d1c06a08751c)
![ISOINFO G4B (0xe0) ISO-9660 UDF-Bridge Windows_10 iso attached in VBOX 7 UDFFD (part 3) UDFFID (parent) XII](https://github.com/deomsh/ISOINFO.G4B/assets/67714723/1692f59a-8633-48b1-a600-c93406dab55b)
![ISOINFO G4B (0xe0) ISO-9660 UDF-Bridge Windows_10 iso attached in VBOX 7 UDFFID (first file) XIII](https://github.com/deomsh/ISOINFO.G4B/assets/67714723/7befa7d3-6f1e-4504-a03c-2dd07c0a14b9)
Examples of read-out of Booting Catalog to get access to FAT efi-floppy on Windows 10 iso:
![Use read-out of Bootctalog on (0xe0) ISO-9660 UDF-Bridge Windows_10 iso attached in VBOX 7 to get access to FAT EFI-bootfloppy XIV](https://github.com/deomsh/ISOINFO.G4B/assets/67714723/b8e39b32-5a1d-4fa6-b510-1d35dd0c499c)

DIR-function on UDF v2.50

![GRUB4DOS 20160118 45c ISOINFO --UDFDIR=FIL16K37 000- (hd3,0) on 8GB UDF v2 50 37000 files 2m 17s with Lsession II](https://github.com/deomsh/ISOINFO.G4B/assets/67714723/470b0fe5-cce4-42d6-b84f-fbc5f286e939)

ISO-9660: DIR functions and Directory Record with Rock Ridge Extensions

![ISOINFO ls (0xe0)- --DIR (0xe0) --recordR=NULLA-(asterisk) (0xe0) --DIR2 (0xe0) on withRockRidgeAndJoliet iso  With SUSP CE Continuation Area  I](https://github.com/deomsh/ISOINFO.G4B/assets/67714723/2cbda5e3-7a2d-49c0-8f92-40c6c24a4b63)

DVD+R: using previous UDF v1.50 Virtual Allocation Tables

![GRUB4DOS 20160118 45c ISOINFO --UDFDIR  --PREVIOUS  (0xe0) on DVDR1SES ISO until 'No previous VAT found' (1MB ONE AVDP) I](https://github.com/deomsh/ISOINFO.G4B/assets/67714723/c2b55fec-94ea-45d4-95f2-1855a1a0c12e)  

DVD+R: using previous UDF v2.01 formatting

![ISOINFO G4B --UDFDIR   set L   --AVDP   --AVDP --PREVIOUS   --UDFDIR + set L on (0xe00) DVD+R after the second format shown finding the first format](https://github.com/deomsh/ISOINFO.G4B/assets/67714723/fa4d9acb-778b-468f-aa16-9fefd8ff4e40)


Using ISOINFO.G4B on GRUB4DOS for UEFI with CD (0xa0) to get access to small file (embedded in File Entry)
![Using ISOINFO G4B on GRUB4EFI and CD (0xa0) to get access to small file embedded in File Entry I](https://github.com/deomsh/ISOINFO.G4B/assets/67714723/89e78d94-917e-425b-b42b-2d84f735aa5b)

CD-RW: small empty UDF v2.01 Sparing Table with HEX

![ISOINFO --SPT --HEX (0xe0) UDF v2 01 Sparing Table on old fillud up CD-RW still empty](https://github.com/deomsh/ISOINFO.G4B/assets/67714723/c0bf3cc1-6616-4cdf-bb84-04a2b1266ae5)

