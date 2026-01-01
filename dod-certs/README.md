# DoD Certs Script

## Intended Audience

The **DoD Certs script** is designed for users running macOS, Ubuntu 22.04 or higher, or WSL2 (running Ubuntu 22.04 or higher) who need to download, install, repair, or update their DoD certificates.

## Overview

The **DoD Certs script** will automatically:

- Download the latest DoD certs from [DoD Cyber Exchange ↗](https://public.cyber.mil/pki-pke/)
- Verify the downloaded certs' integrity with a checksum
- Install DoD certs

After the **DoD Certs script** has run, you can access the certs in `/usr/local/share/ca-certificates/DoD`.

> [!NOTE]
> Additional steps may be required to configure your browser with the DoD certs. After browser configuration, users should be able to access DoD Public Key Infrastructure (PKI)-protected information or applications for web sites that require a CAC for authentication. The Snap install of Firefox is not CAC compatible ([see FAQ](../docs/troubleshooting-faq.md#i-am-running-snap-firefox-on-ubuntu-what-should-i-do-if-i-need-to-authenticate-to-a-web-site-using-a-cac)).

## Prerequisites

- [OpenSSL ↗](https://github.com/openssl/openssl/) 3.2 or higher
  - Check your system for OpenSSL v3.2 or greater: `openssl version`
  - If missing, install with Homebrew `brew install openssl` or consult the [OpenSSL documentation ↗](https://github.com/openssl/openssl/?tab=readme-ov-file#build-and-install) for alternatives

## Usage

### Recommended Usage

Use the [ACT3 Login script](../act3-login/README.md) to install the DoD certs. Reply **Yes** when asked to install the DoD certs.

> [!IMPORTANT]
> Check the [prerequisites for the ACT3 Login script](../act3-login/README.md#prerequisites).

<!-- act3-pt ignore-->
<!-- act3-pt ../act3-login/README.md section:run-act3-login -->
<!-- timestamp:2025-10-31,11:06:08 -->
```sh
curl -fsSL https://raw.githubusercontent.com/act3-ai/up/refs/heads/main/act3-login/act3-login | bash
```

<!-- act3-pt end -->

To run the `dod-certs` script by itself, follow the [optional usage instructions](#optional-usage) below.

### Optional Usage

Optionally, you can either curl the script or clone the repo and run the script.

#### Curl and Run

```sh
curl -fsSL https://raw.githubusercontent.com/act3-ai/up/refs/heads/main/dod-certs/dod-certs | bash
```

#### Clone Repo and Run

Clone the [Up](https://github.com/act3-ai/up) repository to your system:

```sh
git clone git@github.com:act3-ai/up.git
```

Then, run the [`dod-certs` script](./dod-certs):

```sh
.up/dod-certs/dod-certs
```

## Support
<!-- act3-pt ignore -->
<!-- act3-pt ../docs/support.md section:support -->
<!-- timestamp:2025-10-29,09:24:22 -->
- **[Troubleshooting FAQ](../docs/troubleshooting-faq.md)**: consult a list of troubleshooting options and frequently asked questions
- **[Create a Support Ticket issue](https://github.com/act3-ai/up/issues)**: create a support ticket issue on the Up GitHub project

<!-- act3-pt end -->
