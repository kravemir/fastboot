Just some modifications to Debian Unstable system to make it boot ASAP. It works with UEFI systems.

Results on almost clean Debian install with `gdm3`:

```
Startup finished in 3.285s (firmware) + 69ms (loader) + 1.171s (kernel) + 1.032s (userspace) = 5.558s
graphical.target reached after 1.020s in userspace
```

Installation:

```bash
# TODO: install files in repo

# install systemd-boot (zero delay), but keep grub as different UEFI entry
bootctl --path=/boot/efi install

# regenerate initramfs
update-initramfs -u -k all

# disable this horrible service !!!
systemctl disable NetworkManager-wait-online.service

# check boot entries
bootctl --path=/boot/efi install
```

