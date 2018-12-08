# Install win98 from qemu
## prepare the image
Create the win98_install.iso from a legal win98 installation CD. For non-commercial use, here is a valid source https://archive.org/details/win98se_201607

## create virtual disk image
```bash
ruixif@ubuntu: qemu-img create -f qcow2 win98.img 5G
```
## boot from the installation disk
```bash
ruixif@ubuntu: qemu-system-i386 -hda win98.img -cdrom win98_install.iso -boot d -cpu core2duo -m 1024 -vga cirrus -net nic,model=pcnet -net user -localtime
```
## run the installed system
```bash
ruixif@ubuntu: qemu-system-i386 -hda win98.img -boot c -cpu core2duo -m 1024 -vga cirrus -net nic,model=pcnet -net user -localtime
```

