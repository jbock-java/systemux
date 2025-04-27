# systemux

This can be used as a starting point to create a bootable liveimage with dracut.
The resulting file `systemux.img` can be used as a dracut "stage2" which prints "Hello, World!" in a tmux window.

### Preparation: create the initrd

```sh
sudo dnf install dracut-live
sudo dracut -f --no-hostonly --add 'livenet' live.initrd
```

### Create the squashfs

```sh
sudo ./build -f
```

### Running in qemu

First create the ipxe binary.

```sh
make bin-x86_64-efi/ipxe.efi
```

Then run qemu.

```sh
sudo qemu-system-x86_64 \
  -drive if=pflash,format=raw,readonly=on,file=/usr/share/edk2/ovmf/OVMF_CODE.fd \
  -drive file=fat:rw:/boot/efi,format=raw \
  -nographic
```
