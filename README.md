# dmplan
Disk migration mapping planner

Environment:
There are x number of datastores(DS). 
Each datastore(DS) hosts y number of VMs. 
Each VM contains z numbers of virtual disks(VD) which belongs 
to x number of datastores(DS). Each virtual disk(VD) lives in an arbitrary datastore(DS).

Some virtual disk(VD) image file do not need to part of a VM ( a disk image without a VM ).

DS1 - 5TB
- VD1 - 100G -> VM1
- VD2 - 200G -> VM2
    
DS2 - 6TB
- VD3 - 100G -> VM1
- VD4 - 100G -> VM3
- VD5 - 100G -> VM3
- VM6 - 200G -> VM2

The Disk migration mapping planner aims to digest environmental settings in csv or yaml format, and produce migration steps for VM disk images to be moved for migration.

The goal is to calculate and discover a plan of action to have each VM and its' associated Virtual disk be to the same datastore.

E.g.
DS1 - 1TB
- VD1 - 100G -> VM1
- VD2 - 200G -> VM2

DS2 - 1TB
- VD3 - 100G -> VM1
- VD4 - 100G -> VM3
- VD5 - 100G -> VM3
- VD6 - 200G -> VM2

DS3 - 1TB
- No VM disks

Plan:
Move disk image VD6 of VM2 from DS2 to DS1
and
Move disk image VD1 of VM1 from DS1 to DS2 
Hence
No action for VM3 as DS2 has enough space to acommendate VM1 and VM3 disks.
All VM2 disks are under the same datastore(DS1) 
All VM1 disks are under the same datastore(DS2)

DS1 - 1TB
- VD2 - 200G -> VM2
- VD6 - 200G -> VM2

DS2 - 1TB
- VD1 - 100G -> VM1
- VD3 - 100G -> VM1
- VD4 - 100G -> VM3
- VD5 - 100G -> VM3

DS3 - 1TB
- No VM disks

