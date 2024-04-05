# ISOINFO.G4B

ISOINFO.G4B v0.7 (20240406), by deomsh

Function 1:	Read-out ISO-9660/UDF Descriptors on a device, image-file or blocklist

Function 2:	Read/ find directories/ files or read-out their Directory Records
          
Use:				ISOINFO.G4B [SWITCHES] DEVICE|FILE

Help:				ISOINFO.G4B /?

SWITCHES

General:		[--Q] [--HEX] [--BLOCKSIZE=bytes] [--MDBASE=sector] [--INFO]

ISO 1:			--ISOVDS|--ISOPVD|--BD|--SVD[2]|--VPD|--VDT|--ROOT[2/3]

ISO 2:			--DIR|RECORD[2/3][RR]=[PATH][name.ext[;n]] [--ATTRIB=DF[-]H] [--CASE] [--DEEP]

UDF 1:			--VRS|--UDFVDS|--VDS2|--FDS|--AVDP|--PVD|--IUVD|--PD|--LVD|--USD|--LVID|--FSD|--FE|--EFE|--TD|--VAT|--SPT|--MF|--MMF|--MBF|--SBD|--UDFROOT [--MIRROR|--PREVIOUS]

UDF 2:			--UDFDIR|UDFRECORD=[PATH][filename.ext] [--ATTRIB=DF[-]H0] [--CASE] [--MIRROR|--PREVIOUS] [--MDCOPY|MDMAP=disk_num]

UDF 3:			--LSN=sector|--LBN=number [--OFFSET=bytes] [--MIRROR|--PREVIOUS]

Example:		ISOINFO.G4B (hd0,0)/filename.iso

Example:		ISOINFO.G4B --ISOPVD (0xe0)

Example:		ISOINFO.G4B --UDFVDS (0xe0)

Example:		ISOINFO.G4B --RECORD=FILENAME.EXT;1 (0xe0)

Example:		ISOINFO.G4B --RECORD2=boot.catalog (0xe0)

Example:		ISOINFO.G4B --DIR2=SUBDIR/bo*.c* (0xe0)

Example:		ISOINFO.G4B --UDFRECORD=System\ Volume\ Information (hd0,0)/some.iso

Example:		ISOINFO.G4B --UDFDIR="System Volume Information/" (hd0,0)/some.iso

History

Version 0.7: First published version

ISO-9660

Supported: ISO-9660 (all levels), El Torito, Joliet, Rock Ridge. 
Unupported: Multi-Extent files. 

Used sources:

UDF

Supported: all versions (v2.60 untested on optical media). 
Unsupported: Multi Session (except UDF CD-R/DVD+/-R), Named Streams (except first System Stream). 

General Limitations:
Maximum length of PATH (and FILE) about 510 chars. 
Only embedded Extended Attributes supported. 

Used sources:


SCREENSHOTS:

ISO-9660/ UDF Descriptors on Windows 10 iso

![ISOINFO G4B (0xe0) ISO-9660 UDF-Bridge Windows_10 iso attached in VBOX 7 ISO PVD I](https://github.com/deomsh/ISOINFO.G4B/assets/67714723/cdc1342a-e20b-44ab-82e2-43020a832748)
![ISOINFO G4B (0xe0) ISO-9660 UDF-Bridge Windows_10 iso attached in VBOX 7 ISO BD+Booting Catalog II](https://github.com/deomsh/ISOINFO.G4B/assets/67714723/c4b50df8-4bb2-4c63-a8ed-45ed4be85c62)
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
![ISOINFO G4B (0xe0) ISO-9660 UDF-Bridge Windows_10 iso attached in VBOX 7 UDFFID (first file) XIII](https://github.com/deomsh/ISOINFO.G4B/assets/67714723/7942b15f-07b1-47bf-8b25-bbc223bd9cdc
Example of read-out of Booting Catalog to get access to FAT efi-floppy on Windows 10 iso:
![Use read-out of Bootctalog on (0xe0) ISO-9660 UDF-Bridge Windows_10 iso attached in VBOX 7 to get access to FAT EFI-bootfloppy XIV](https://github.com/deomsh/ISOINFO.G4B/assets/67714723/b8e39b32-5a1d-4fa6-b510-1d35dd0c499c)

DIR-function on UDF v2.50

![GRUB4DOS 20160118 45c ISOINFO --UDFDIR=FIL16K37 000- (hd3,0) on 8GB UDF v2 50 37000 files 2m 17s with Lsession II](https://github.com/deomsh/ISOINFO.G4B/assets/67714723/470b0fe5-cce4-42d6-b84f-fbc5f286e939)

ISO-9660: DIR functions and Directory Record with Rock Ridge Extensions

![ISOINFO ls (0xe0)- --DIR (0xe0) --recordR=NULLA-(asterisk) (0xe0) --DIR2 (0xe0) on withRockRidgeAndJoliet iso  With SUSP CE Continuation Area  I](https://github.com/deomsh/ISOINFO.G4B/assets/67714723/da900864-18cd-4215-8286-83b0295787de)

DVD+R: using previous UDF v1.50 Virtual Allocation Tables

![GRUB4DOS 20160118 45c ISOINFO --UDFDIR  --PREVIOUS  (0xe0) on DVDR1SES ISO until 'No previous VAT found' (1MB ONE AVDP) I](https://github.com/deomsh/ISOINFO.G4B/assets/67714723/c2b55fec-94ea-45d4-95f2-1855a1a0c12e)

CD-RW: small empty UDF v2.01 Sparing Table with HEX

![ISOINFO --SPT --HEX (0xe0) UDF v2 01 Sparing Table on old fillud up CD-RW still empty](https://github.com/deomsh/ISOINFO.G4B/assets/67714723/c0bf3cc1-6616-4cdf-bb84-04a2b1266ae5)






















