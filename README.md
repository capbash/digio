digio
==============

A bash implementation of the [Digital Ocean API](https://developers.digitalocean.com/documentation/v2/)

# How to Install #

To install from scratch, run

```bash
curl -s https://raw.githubusercontent.com/capbash/do/master/digio-installer | bash
```

This will install capbash into /usr/local/bin/digio.  To install it somewhere else, for example:

```bash
curl -s https://raw.githubusercontent.com/capbash/do/master/digio-installer | bash -s -- --path ~/.bin
```

If you don't trust this project, please don't pipe into bash, and instead download the file,
inspect it and run it directly.

If you already have digio and want to upgrade to the altest, please run

```
digio update-self
```
