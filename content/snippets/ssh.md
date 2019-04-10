---
title: "SSH"
draft: true
tags: ['BASH', 'SSH']
---

SSH (Secure Shell) is a tool for secure network connections. It is most commonly used for launching a shell on a remote machine.

## Creating a SSH Keypair

You'll need to have a SSH keypair. This keypair consists of two keys (hence "pair"):

- a public key which you are free to share with anybody and anywhere; and
- a private key (which should be kept *private*).

```bash
$ ssh-keygen
```

- Accept the default location.
- Always a good idea to specify a passphrase. This will make you just a little more secure since somebody would need to know this passphrase to use your private key should it ever be compromised.

```bash
$ ls .ssh/
authorized_keys  id_rsa  id_rsa.pub
```

The two pertinent files are:

- `id_rsa` - private key
- `id_rsa.pub` - public key.

This is what the contents of the public key looks like (obviously the details will vary):

```bash
$ fold -w 80 .ssh/id_rsa.pub 
ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDEgjjCs3Z9oo9ByyPDkShvM4q/9iSDp6R8837ywg5N
MpfBYI/fg5pgGZUjhwVi14ZUkgfX0dFLkRfS1dczd3FfG6ykXHwoNyC7D8F6rIAnbE9pwF1fIMsTGaue
2ZaJ/OxrsiCuwVOv7ChjPxN5Wg7g6bAn+cogPsrbwucx6Kv7Tpz71bMZR5E2DRUeZiX9J61U8rDrxVoV
JyvFxWRUBx1zZbrmV3RW5IH8cdlhCxjfU//xmoeVRYriQ/m6FNRbFMWYqJskpan8vp/XpGR22x+o5nDD
0TZ0iM+YCO+je82nnWbMikFjQqZsYXutdaYvVC3jnfuMz3ZwfwhEDtl9Rwl3 ubuntu
```

*Note:* When copying your public key onto websites you'll need to remove any linebreaks (it should be just a single long string).