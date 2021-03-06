# Windows 10 repairs

## Restore the `EFI/Microsoft` directory

Open a command prompt with an installation media:

1. Boot on a Windows 10 installation media.
2. Choose a language and click "Next".
3. "Repair your computer"
4. "Command Prompt"

Restore the `EFI/Microsoft` directory:

```
diskpart
> list disk
> select disk [0-9]      # the EFI partition is usually on disk 0
> list partition
> sel partition [0-9]    # the EFI partition is usually the first
> assign letter=Z:
> exit

bcdboot C:\windows /s Z: /f UEFI /v  # /s for mountpoint
                                     # /f for firmwaretype
                                     # /v for verbose

exit
```

## Restore the MBR

For example after a Linux uninstall.

```
bootrec /fixmbr
```

[https://fr.wikipedia.org/wiki/Master_boot_record#Microsoft_Windows]()

## Surface Laptop 3 configuration

[How to Disable Adaptive Contrast on Surface Laptop 3 (AMD)](https://www.reddit.com/r/Amd/comments/dw3fyp/how_to_disable_adaptive_contrast_on_surface/)
