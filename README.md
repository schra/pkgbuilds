# PKGBUILDs for Arch Linux

This repository contains packages for Arch Linux.
These packages are also published in the [AUR](https://wiki.archlinux.org/index.php/Arch_User_Repository).

## Installation

I'm using [aurpublish](https://github.com/eli-schwartz/aurpublish) to maintain this repository.

```
git clone git@github.com:schra/pkgbuilds.git
cd pkgbuilds
aurpublish setup
```

## Adding new packages

1. Write the `PKGBUILD`
2. Commit the `PKGBUILD`. `aurpublish` will prefill the commit message. In most cases you can just leave the commit message like that.

    ```
    cd PACKAGE/
    git add PKGBUILD
    git commit
    ```
3. Push the package to both the AUR and this repository

    ```
    aurpublish PACKAGE
    git push
    ```
