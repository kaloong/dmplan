# dmplan
Disk migration planner

Environment:
There are x number of datastores. Each datastore hosts y number of VMs. Each VM contains z numbers of virtual disks which belongs 
to x number of datastores. Each virtual disk lives in an arbitrary datastore.

Some virtual disk does not need to belong to a VM.

DS1 - 5TB
- VD1 - 100G -> VM1
- VD2 - 200G -> VM2
    
DS2 - 6TB
- VD3 - 100G -> VM1
- VD4 - 100G -> VM3
- VD5 - 100G -> VM3
- VM6 - 200G -> VM2

The Disk migration planner is aiming to digest an environment settings and produce migration plan for VM disks data store migration.

The goal is to calculate and discover the best action plan to have each VM and its' associated Virtual disk be moved under
the same datastore.

E.g.
DS1 - 5TB
- VD1 - 100G -> VM1
- VD2 - 200G -> VM2

Move DS2 > VM6 to DS1 so that DS1 will look like this.

DS1 - 5TB
- VD1 - 100G -> VM1
- VD2 - 200G -> VM2
- VD3 - 100G -> VM1


