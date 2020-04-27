PKGBUILDs for Arch Linux
========================

This repository contains packages for Arch Linux.
These packages are also published in the [AUR](https://wiki.archlinux.org/index.php/Arch_User_Repository).

Installation
------------

I'm using [aurpublish](https://github.com/eli-schwartz/aurpublish) to maintain this repository.

```
git clone git@github.com:schra/pkgbuilds.git
cd pkgbuilds
aurpublish setup
```

Updating packages
-----------------

1. Adjust the `PKGBUILD`
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

Some remarks
------------

* If possible, I always provide both the Git and non-Git packages.

* All Git packages need to:

  * Have `conflicts` and `provides` entries that point to the non-Git package equivalent.
  * Have a `pkgver` function, so that the `pkgver` variable gets updated automatically.

* I try to keep the diff between the Git and non-Git PKGBUILDs as small as possible.
  That's why I always define the `_name` and `_mainfolder` variables:

    * `_name` is the package name without the `-git` suffix (if there is any).
      It is used to install files in the file system in `package()`.
      Never use `pkgname` in `package()`, only use it in `source`.
    * `_mainfolder` is the folder that contains the source code.
      For Git packages this is the repository name.
      For non-Git packages it is the name of the folder inside the tar ball (normally tar balls contain exactly one directory which then contains the actual content).
      Use `_mainfolder` when using `cd`.
