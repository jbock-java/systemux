# systemux

This can be used as a starting point to create a bootable liveimage with dracut.
The resulting file `systemux.img` can be used as a dracut "stage2" which prints "Hello, World!" in a tmux window.

### Preparation: create the initrd

```sh
sudo dnf install dracut-live
sudo dracut -f --no-hostonly --add 'livenet' live.img
```

### Create the squashfs

```sh
sudo ./build -f -i
```

### Testing in qemu

In another terminal, start an http server (in the directory that contains `systemux.img`):

```sh
python3 -mhttp.server --bind $(hostname -I) 3000
```

Then start qemu:

```sh
sudo ./run -q
```

### Network boot

TODO explain ipxe setup
