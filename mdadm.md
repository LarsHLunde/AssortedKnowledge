# Linux Software RAIDS
## This is a stub

## Recreate raid
```
mdadm --stop /dev/md0
mdadm --assemble --run --force --update=resync /dev/md0 /dev/sda1 /dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sde1 /dev/sdf1 /dev/sdg1 /dev/sdh1 /dev/sdi1 /dev/sdj1
mdadm --detail --scan --verbose | sudo tee -a /etc/mdadm.conf
```  
