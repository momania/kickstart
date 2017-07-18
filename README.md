## Kickstart Notes

####

**N.B.** Volume label needs to be equal to what's used in `isolinux.cfg`

` sudo mkisofs -R -J -v -T -no-emul-boot -boot-load-size 4 -boot-info-table -joliet-long -o ~/centos/CentOS-7-custom.iso -b isolinux/isolinux.bin -c isolinux/boot.cat -V "CentOS 7 x86_64" .`
