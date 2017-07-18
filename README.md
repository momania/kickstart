## Kickstart Notes


### Modification Instructions

Based on [CentOS Minimal ISO](http://isoredirect.centos.org/centos/7/isos/x86_64/CentOS-7-x86_64-Minimal-1611.iso)

On OS X follow following procedure (assuming `/dev/disk2` is the next available device):

```dtd
mkdir /tmp/centos_iso /tmp/centos_ks
hdiutil attach -nomount CentOS-7-x86_64-Minimal-1611.iso
mount /dev/disk2 /tmp/centos_iso
rsync -arv /tmp/centos_iso /tmp/centos_ks
```

Using `/tmp/centos_ks` as the working folder:
 - overwrite `/isolinux/isolinux.cfg` with the one in this repo.
 - copy the `ks.cfg` to the root
 - run `mkpasswd -m sha-512` on any linux machine to generate a crypted password (haven't found a nice way to do this on OS X that doesn't involve Python)
 - replace `rootpw --iscrypted ########` with your own crypted password 
 - then run the command to make the iso
 
#### Make ISO

` sudo mkisofs -R -J -v -T -no-emul-boot -boot-load-size 4 -boot-info-table -joliet-long -o ~/centos/CentOS-7-custom.iso -b isolinux/isolinux.bin -c isolinux/boot.cat -V "CentOS 7 x86_64" .`

**N.B.** Volume label needs to be equal to what's used in `isolinux.cfg`