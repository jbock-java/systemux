# systemux

This can be used as a starting point to create a bootable liveimage with dracut.
The systemux img can be used as a dracut "stage2" which prints "Hello, World!" in a tmux window.

### create live img

```sh
sudo dnf install dracut-live
sudo dracut -f --no-hostonly --add 'livenet' live-$(uname -r).img
```

### Create systemux img

```sh
sudo ./build -f -i
```

### Testing in qemu

In another terminal, start an http server (still in the same directory):

```sh
python3 -mhttp.server --bind $(hostname -I | sed -E 's/^(\S+).*/\1/') 3000
```

Then start qemu:

```sh
sudo ./run
```

### Network boot

TODO explain ipxe setup
