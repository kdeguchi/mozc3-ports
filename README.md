# mozc3 ports for FreeBSD ports tree

These ports have been incorporated into the ports tree.

https://cgit.freebsd.org/ports/commit/?id=19cbb11ea49150c9c2394566efd127beec65ca0b

The latest version of mozc is available for use on FreeBSD.
Fcitx5 is also supported, so you can get the source code from https://github.com/fcitx/mozc.

I can guarantee that Fcitx5 which I use regularly will work,
but I can't guarantee that the others will work,
only that poudriere will build everything.

You can download these files and overwrite ports tree, or use ports overlays method.
I recommend using ports overlays method.

## ports overlay method

Add in your `/etc/make.conf` as follows:

`OVERLAYS+=/your/download/directory/mozc3-ports`

If you use poudriere, you may need to add to `/etc/make.conf` as follows:

    .ifndef POUDRIERE_BUILD_TYPE
    OVERLAYS+=/your/download/directory/mozc3-ports
    .endif
