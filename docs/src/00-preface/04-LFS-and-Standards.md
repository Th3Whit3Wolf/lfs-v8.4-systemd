# LFS and Standards

The structure of LFS follows Linux standards as closely as possible. The primary standards are:

- [POSIX.1-2008](http://pubs.opengroup.org/onlinepubs/9699919799/)
- [Filesystem Hierarchy Standard (FHS) Version 3.0](http://refspecs.linuxfoundation.org/FHS_3.0/fhs/index.html)
- [Linux Standard Base (LSB) Version 5.0 (2015)](http://refspecs.linuxfoundation.org/lsb.shtml)

The LSB has four separate standards: Core, Desktop, Runtime Languages, and Imaging. In addition to generic requirements there are also architecture specific requirements. There are also two areas for trial use: Gtk3 and Graphics. LFS attempts to conform to the architectures discussed in the previous section.

> **Note**
>
> > Many people do not agree with the requirements of the LSB. The main purpose of defining it is to ensure that proprietary software will be able to be installed and run properly on a compliant system. Since LFS is source based, the user has complete control over what packages are desired and many choose not to install some packages that are specified by the LSB.

### Packages supplied by LFS needed to satisfy the LSB Requirements

<table border="0" class="variablelist">
    <colgroup>
    <col align="left" valign="top" />
    <col />
    </colgroup>
    <tbody>
    <tr>
        <td>
        <p>
            <span class="term"><span class="emphasis"><em>LSB
            Core:</em></span></span>
        </p>
        </td>
        <td>
        <p>
            Bash, Bc, Binutils, Coreutils, Diffutils, File, Findutils,
            Gawk, Grep, Gzip, M4, Man-DB, Ncurses, Procps, Psmisc, Sed,
            Shadow, Tar, Util-linux, Zlib
        </p>
        </td>
    </tr>
    <tr>
        <td>
        <p>
            <span class="term"><span class="emphasis"><em>LSB
            Desktop:</em></span></span>
        </p>
        </td>
        <td>
        <p>
            None
        </p>
        </td>
    </tr>
    <tr>
        <td>
        <p>
            <span class="term"><span class="emphasis"><em>LSB Runtime
            Languages:</em></span></span>
        </p>
        </td>
        <td>
        <p>
            Perl
        </p>
        </td>
    </tr>
    <tr>
        <td>
        <p>
            <span class="term"><span class="emphasis"><em>LSB
            Imaging:</em></span></span>
        </p>
        </td>
        <td>
        <p>
            None
        </p>
        </td>
    </tr>
    <tr>
        <td>
        <p>
            <span class="term"><span class="emphasis"><em>LSB Gtk3 and
            LSB Graphics (Trial Use):</em></span></span>
        </p>
        </td>
        <td>
        <p>
            None
        </p>
        </td>
    </tr>
    </tbody>
</table>

### Packages supplied by BLFS needed to satisfy the LSB Requirements

<table border="0" class="variablelist">
    <colgroup>
    <col align="left" valign="top" />
    <col />
    </colgroup>
    <tbody>
    <tr>
        <td>
        <p>
            <span class="term"><span class="emphasis"><em>LSB
            Core:</em></span></span>
        </p>
        </td>
        <td>
        <p>
            At, Batch (a part of At), Cpio, Ed, Fcrontab, Initd-tools,
            Lsb_release, NSPR, NSS, PAM, Pax, Sendmail (or Postfix or
            Exim), time
        </p>
        </td>
    </tr>
    <tr>
        <td>
        <p>
            <span class="term"><span class="emphasis"><em>LSB
            Desktop:</em></span></span>
        </p>
        </td>
        <td>
        <p>
            Alsa, ATK, Cairo, Desktop-file-utils, Freetype, Fontconfig,
            Gdk-pixbuf, Glib2, GTK+2, Icon-naming-utils, Libjpeg-turbo,
            Libpng, Libtiff, Libxml2, MesaLib, Pango, Xdg-utils, Xorg
        </p>
        </td>
    </tr>
    <tr>
        <td>
        <p>
            <span class="term"><span class="emphasis"><em>LSB Runtime
            Languages:</em></span></span>
        </p>
        </td>
        <td>
        <p>
            Python, Libxml2, Libxslt
        </p>
        </td>
    </tr>
    <tr>
        <td>
        <p>
            <span class="term"><span class="emphasis"><em>LSB
            Imaging:</em></span></span>
        </p>
        </td>
        <td>
        <p>
            CUPS, Cups-filters, Ghostscript, SANE
        </p>
        </td>
    </tr>
    <tr>
        <td>
        <p>
            <span class="term"><span class="emphasis"><em>LSB Gtk3 and
            LSB Graphics (Trial Use):</em></span></span>
        </p>
        </td>
        <td>
        <p>
            GTK+3
        </p>
        </td>
    </tr>
    </tbody>
</table>

### Packages not supplied by LFS or BLFS needed to satisfy the LSB Requirements

<table border="0" class="variablelist">
    <colgroup>
    <col align="left" valign="top" />
    <col />
    </colgroup>
    <tbody>
    <tr>
        <td>
        <p>
            <span class="term"><span class="emphasis"><em>LSB
            Core:</em></span></span>
        </p>
        </td>
        <td>
        <p>
            None
        </p>
        </td>
    </tr>
    <tr>
        <td>
        <p>
            <span class="term"><span class="emphasis"><em>LSB
            Desktop:</em></span></span>
        </p>
        </td>
        <td>
        <p>
            Qt4 (but Qt5 is provided)
        </p>
        </td>
    </tr>
    <tr>
        <td>
        <p>
            <span class="term"><span class="emphasis"><em>LSB Runtime
            Languages:</em></span></span>
        </p>
        </td>
        <td>
        <p>
            None
        </p>
        </td>
    </tr>
    <tr>
        <td>
        <p>
            <span class="term"><span class="emphasis"><em>LSB
            Imaging:</em></span></span>
        </p>
        </td>
        <td>
        <p>
            None
        </p>
        </td>
    </tr>
    <tr>
        <td>
        <p>
            <span class="term"><span class="emphasis"><em>LSB Gtk3 and
            LSB Graphics (Trial Use):</em></span></span>
        </p>
        </td>
        <td>
        <p>
            None
        </p>
        </td>
    </tr>
    </tbody>
</table>
