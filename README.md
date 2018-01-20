sphpf
-----
**A PHP environment and FPM version switcher for MacOS**

This repository holds a utility script designed for those who are running MacOS, [Homebrew](https://brew.sh/), [NGINX](https://www.nginx.com/) and multiple versions of PHP (5.6, 7.0, 7.1 etc.).

## Installation:

Copy the `sphpf` file in this repository to a location included in your `PATH` environment variable, you can discover these paths by typing:

```
echo $PATH
``` 

Alternatively, you could create a `bin` directory in your user folder, and add this to your path instead, e.g.:

```
mkdir -p ~/bin
cp sphpf ~/bin
chmod +x ~/bin/sphpf
```

Then if you are using the standard terminal:

```
echo "$PATH" | grep -qv "/Users/$(id -u -n)/bin" && echo "export PATH=\"/Users/$(id -u -n)/bin:$PATH\"" >> ~/.bashrc
```

Or using ZSH:

```
echo "$PATH" | grep -qv "/Users/$(id -u -n)/bin" && echo "export PATH=\"/Users/$(id -u -n)/bin:$PATH\"" >> ~/.zshrc
```

You may need to restart your shell for this to take effect.

## Using it:

The script will switch your environment's active PHP version (e.g. on the command line), and also in turn switch your (or startup, if it's not already running) PHP FPM instance to match the target version.

The version syntax, matches that of the postfix to the PHP versions on brew, e.g. for php56 = 56, php70 = 70, so for example:

```
    #: sphpf 56
    #: sphpf 70
    #: sphpf 71
```

If you want to see what commands will be run, without the script actually taking action, you can also "Dry Run" the process, which will just outout the relevant commands, rather than run them, e.g.:

```
sphpf -t 71
```

## Troubleshooting

You can get more visibility about what is going on by the standardised repeatable verbosity argument, e.g. `-v`,`-vv`,`-vvv`. The most useful are likely to be `-vv` for INFO & above, and `-vvv` for DEBUG and above.

The script also has a self contained reminder of all applicable usage arguments:

```
sphpf -h
```

## Thanks to

A huge thanks to the core inspiration and ideas, originally sourced from the following projects:

* Initial work by [sgotre](https://github.com/sgotre) on [sphp](https://github.com/sgotre/sphp-osx)
* It's FPM focused fork by [esolitos](https://github.com/esolitos) on [sphpf](https://github.com/esolitos/sphp-fpm-osx)
