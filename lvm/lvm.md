# LVM guide

## Expand harddisk to include a new drive and exten

```console
root@ai:/home/thorpej# pvscan
  PV /dev/sda3   VG ubuntu-vg       lvm2 [<46.95 GiB / 23.47 GiB free]
  Total: 1 [<46.95 GiB] / in use: 1 [<46.95 GiB] / in no VG: 0 [0   ]
```

```console
 root@ai:/dev# pvcreate /dev/sdb
  Physical volume "/dev/sdb" successfully created.
```

```console
root@ai:/dev# pvscan
  PV /dev/sda3   VG ubuntu-vg       lvm2 [<46.95 GiB / 23.47 GiB free]
  PV /dev/sdb                       lvm2 [150.00 GiB]
  Total: 2 [<196.95 GiB] / in use: 1 [<46.95 GiB] / in no VG: 1 [150.00 GiB]

```

```console
root@ai:/dev# vgscan
  Found volume group "ubuntu-vg" using metadata type lvm2
root@ai:/dev# vgs
  VG        #PV #LV #SN Attr   VSize   VFree
  ubuntu-vg   1   1   0 wz--n- <46.95g 23.47g
```

```console
root@ai:/dev# vgextend ubuntu-vg /dev/sdb
  Volume group "ubuntu-vg" successfully extended
root@ai:/dev# vgs
  VG        #PV #LV #SN Attr   VSize   VFree
  ubuntu-vg   2   1   0 wz--n- 196.94g <173.47g
```

```console
root@ai:/dev# lvs
  LV        VG        Attr       LSize  Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  ubuntu-lv ubuntu-vg -wi-ao---- 23.47g

root@ai:/dev# lvscan
  ACTIVE            '/dev/ubuntu-vg/ubuntu-lv' [23.47 GiB] inherit
root@ai:/dev# lvextend -L +100G /dev/mapper/ubuntu--vg-ubuntu--lv
  Size of logical volume ubuntu-vg/ubuntu-lv changed from 23.47 GiB (6009 extents) to 123.47 GiB (31609 extents).
  Logical volume ubuntu-vg/ubuntu-lv successfully resized.

root@ai:/dev# resize2fs /dev/mapper/ubuntu--vg-ubuntu--lv
resize2fs 1.47.0 (5-Feb-2023)
Filesystem at /dev/mapper/ubuntu--vg-ubuntu--lv is mounted on /; on-line resizing required
old_desc_blocks = 3, new_desc_blocks = 16
The filesystem on /dev/mapper/ubuntu--vg-ubuntu--lv is now 32367616 (4k) blocks long.
```
