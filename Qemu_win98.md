# Install win98 on qemu
## prepare the image
Create the win98_install.iso from a legal win98 installation CD. For non-commercial use, here is a valid source https://archive.org/details/win98se_201607

## create virtual disk image
"qcow2" saves space efficiently when you actual disk usage of the guest system is not large. However, you might want to use "raw" to make it easier to mount the image on your host system.
```bash
ruixif@ubuntu: qemu-img create -f qcow2 win98.img 5G
```
## boot from the installation disk
```bash
ruixif@ubuntu: qemu-system-i386 -hda win98.img -cdrom win98_install.iso -boot d -cpu pentium2 -m 256 -vga cirrus -net nic,model=pcnet -net user -localtime
```
## run the installed system
You can transfer you files easily by packing them in "myiso.iso".
```bash
ruixif@ubuntu: qemu-system-i386 -hda win98.img -cdrom myiso.iso -boot d -cpu pentium3 -m 1024 -vga cirrus -net nic,model=rtl8139 -smb $HOME/sambashare -soundhw gus
```
## TODO
* Samba
* Network access

