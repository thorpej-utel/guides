# My notes for ZFS

tags: #zfs #linux

using HP 00239

```console
  ls -lah /dev/disk/by-id/
  
  sudo zpool create -f -o ashift=12 -m /utel utel mirror ata-ST1000DM010-2EP102_Z9ANXRP3 ata-ST1000DX001-1CM162_Z1D8N963 
  zfs set relatime=on utel
  zfs set compression=lz4 utel
  sudo zfs set compression=lz4 utel
  sudo  zfs set relatime=on utel
  sudo zpool add utel cache ata-OCZ-AGILITY3_OCZ-Z2Y0GQ2K4N2MJ4GF
  zpool status
```
