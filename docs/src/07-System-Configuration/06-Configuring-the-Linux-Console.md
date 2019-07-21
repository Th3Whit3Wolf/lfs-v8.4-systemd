# Configuring the Linux Console

This section discusses how to configure the **systemd-vconsole-setup** system service, which configures the virtual console font and console keymap.

The **systemd-vconsole-setup** service reads the `/etc/vconsole.conf` file for configuration information. Decide which keymap and screen font will be used. Various language-specific HOWTOs can also help with this, see [http://www.tldp.org/HOWTO/HOWTO-INDEX/other-lang.html](http://www.tldp.org/HOWTO/HOWTO-INDEX/other-lang.html). Examine **localectl list-keymaps** output for a list of valid console keymaps. Look in `/usr/share/consolefonts` directory for valid screen fonts.

The `/etc/vconsole.conf` file should contain lines of the form: VARIABLE="value". The following variables are recognized:

<dl class="variablelist">
    <dt>
    <span class="term"><b>KEYMAP</b></span>
    </dt>
    <dd>
    <p>
        This variable specifies the key mapping table for the keyboard.
        If unset, it defaults to <code class="literal">us</code>.
    </p>
    </dd>
    <dt>
    <span class="term"><b>KEYMAP_TOGGLE</b></span>
    </dt>
    <dd>
    <p>
        This variable can be used to configure a second toggle keymap
        and is unset by default.
    </p>
    </dd>
    <dt>
    <span class="term"><b>FONT</b></span>
    </dt>
    <dd>
    <p>
        This variable specifies the font used by the virtual console.
    </p>
    </dd>
    <dt>
    <span class="term"><b>FONT_MAP</b></span>
    </dt>
    <dd>
    <p>
        This variable specifies the console map to be used.
    </p>
    </dd>
    <dt>
    <span class="term"><b>FONT_UNIMAP</b></span>
    </dt>
    <dd>
    <p>
        This variable specifies the Unicode font map.
    </p>
    </dd>
</dl>

An example for a German keyboard and console is given below:

```sh
cat > /etc/vconsole.conf << "EOF"
KEYMAP=de-latin1
FONT=Lat2-Terminus16
EOF
```

You can change KEYMAP value at runtime by using the **localectl** utility:

```sh
localectl set-keymap MAP
```

> **Note**
>
> > Please note that the **localectl** command can be used only on a system booted with systemd.

You can also use **localectl** utility with the corresponding parameters to change X11 keyboard layout, model, variant and options:

```sh
localectl set-x11-keymap LAYOUT [MODEL] [VARIANT] [OPTIONS]
```

To list possible values for localectl set-x11-keymap parameters, run localectl with parameters listed below:

<dl class="variablelist">
    <dt>
    <span class="term"><b>list-x11-keymap-models</b></span>
    </dt>
    <dd>
    <p>
        Show known X11 keyboard mapping models.
    </p>
    </dd>
    <dt>
    <span class="term"><b>list-x11-keymap-layouts</b></span>
    </dt>
    <dd>
    <p>
        Show known X11 keyboard mapping layouts.
    </p>
    </dd>
    <dt>
    <span class="term"><b>list-x11-keymap-variants</b></span>
    </dt>
    <dd>
    <p>
        Show known X11 keyboard mapping variants.
    </p>
    </dd>
    <dt>
    <span class="term"><b>list-x11-keymap-options</b></span>
    </dt>
    <dd>
    <p>
        Show known X11 keyboard mapping options.
    </p>
    </dd>
</dl>

> **Note**
>
> > Using any of the parameters listed above requires the XKeyboard Config package from BLFS.
