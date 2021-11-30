<!--
SPDX-FileCopyrightText: © 2021 Open Networking Foundation <support@opennetworking.org>
SPDX-License-Identifier: Apache-2.0
--!>
# dkms

Installs DKMS for dynamic recompilation of kernel modules on update

It will also install one or more modules from the `dkms_modules` list.

## ice module

This driver supports the Intel E810 chipset 100GbE NIC.

The Makefile included with this driver acts differently when run by dkms and at
the command line as root and will self-remove the default `all` target. The
`echo;` in the MAKE= line of the dkms.conf works around this issue.

The `BUILD_KERNEL` env var is to specify which kernel to build for.

Note that this module does not build cleanly on the Ubuntu 18.04 default 4.x
kernels - a HWE 5.x kernel is required.

## Example Playbook

```yaml
- hosts: all
  vars:
  roles:
    - dkms
```

## License and Author

© 2021 Open Networking Foundation <support@opennetworking.org>

License: Apache-2.0
