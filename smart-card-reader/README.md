# Smart Card Reader Script

## Intended Audience

The **Smart Card Reader script** is designed for Ubuntu 22.04 (or higher) users who need to install and configure their system to work with a smart card reader (e.g. a CAC reader).

> macOS and Windows have built-in support for smart card readers so those users do not need to run this script

## Overview

The **Smart Card Reader script** will automatically:

- Install:
  - OpenSC
  - Middleware libraries and tools required to read the CAC
  - CACKey
- Enable pcscd

## Usage

> [! TIP]
> The smart card reader configuration can be checked with the [Verification Process](#verification-process).

### Recommended Usage

```sh
curl -fsSL https://raw.githubusercontent.com/act3-ai/up/refs/heads/main/smart-card-reader/enable-smart-card-reader | bash -c -
```

### Optional Usage

Clone the [Up](https://github.com/act3-ai/up) repository to your system:

```sh
git clone git@github.com:act3-ai/up.git
```

Then, run the [`enable-smart-card-reader` script](./enable-smart-card-reader):

```sh
./up/smart-card-reader/enable-smart-card-reader
```

### Verification Process

After running the script, connect the card reader and insert the card. Then, check the slot:

```sh
pkcs11-tool -L
```

Example of output showing the slot is active:

```sh
Available slots:
Slot 0 (0x0): Broadcom Corp 5880 [Contacted SmartCard] (0123456789ABCD) 00 00
  token label        : LASTNAME.FIRSTNAME.0123456789
  token manufacturer : piv_II
  token model        : PKCS#15 emulated
  token flags        : login required, token initialized, PIN initialized
  hardware version   : 0.0
  firmware version   : 0.0
  serial num         : 380aa1857810d7f3
  pin min/max        : 4/8
```

> [!TIP]
> Uninstalling the Snap version of Firefox may cause the `pcscd` daemon to stop running and/or not be initiated after reboot. Consult the [Troubleshooting FAQ](../docs/troubleshooting-faq.md), as needed.

## Support
<!-- act3-pt ignore -->
<!-- act3-pt ../docs/support.md section:support -->
<!-- timestamp:2025-10-29,09:24:22 -->
- **[Troubleshooting FAQ](../docs/troubleshooting-faq.md)**: consult a list of troubleshooting options and frequently asked questions
- **[Create a Support Ticket issue](https://github.com/act3-ai/up/issues)**: create a support ticket issue on the Up GitHub project

<!-- act3-pt end -->
