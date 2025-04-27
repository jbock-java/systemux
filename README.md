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
