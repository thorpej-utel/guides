# My notes for ZFS

using HP 00239

```console
  110  ls -lah /dev/disk/by-id/
  

   sudo zpool create -f -o ashift=12 -m /utel utel mirror ata-ST1000DM010-2EP102_Z9ANXRP3 ata-ST1000DX001-1CM162_Z1D8N963 
  111  zfs set relatime=on utel
  112  zfs set compression=lz4 utel
  113  sudo zfs set compression=lz4 utel
  114  sudo  zfs set relatime=on utel
  115  sudo zpool add utel cache ata-OCZ-AGILITY3_OCZ-Z2Y0GQ2K4N2MJ4GF
  116  zpool status
```

