# ISOINFO.G4B

ISOINFO.G4B v0.7 (20240404), by deomsh

Function 1:	Read-out ISO-9660/UDF Descriptors on a device, imagefile or blocklist

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

Version 0.7
First published version
