# Up

## Overview

The Up repository is a collection of script-based tools and resources to bootstrap access to ACT3 resources. This repository is intended for users who need to authenticate and configure their macOS, Ubuntu 22.04 or higher, or WSL2 (running Ubuntu 22.04 or higher) machines for ACT3 work.

The following are contained in this repo:

- [ACT3 Login script](./act3-login/README.md)
- [DoD Certs script](./dod-certs/README.md)
- [ASCE Tools installers](./asce-tools/README.md)
- [Smart Card Reader script](./smart-card-reader/README.md)

## Usage

### ACT3 Login
<!-- act3-pt ignore -->
<!-- act3-pt ./act3-login/README.md section:features  -->
<!-- timestamp:2025-10-30,11:24:32 -->
The **ACT3 Login script** will automatically:

- Authenticate to a user-defined GitLab instance including:
  - Prompt for and validating your GitLab Personal Access Token
  - Create an SSH key and add it to GitLab
  - Enable secure credential storage for Git and container registry authentication
  - Enable Git commit signing with your SSH key
- Add Homebrew taps for public resources ACT3 teams use
- Add the ACT3 Homebrew tap (for access to public ACT3 software packages)
- Prompt to run the DoD Certs script

<!-- act3-pt end -->

> [!IMPORTANT]
> Check the [prerequisites](./act3-login/README.md#prerequisites) before running.

Run the **ACT3 Login script**:

<!-- act3-pt ./act3-login/README.md section:run-act3-login -->
<!-- timestamp:2026-02-05,07:19:44 -->
```sh
bash <(curl -fsSL https://raw.githubusercontent.com/act3-ai/up/refs/heads/main/act3-login/act3-login)
```
<!-- act3-pt end -->

### DoD Certs

> [!TIP]
> Running the ACT3 Login script will prompt you to install DoD certs.
<!-- Maintenance note: update the relative link to FAQ after running act3-pt docs render -->
<!-- act3-pt ignore -->
<!-- act3-pt ./dod-certs/README.md section:overview -->
<!-- timestamp:2025-10-31,11:37:10 -->
The **DoD Certs script** will automatically:

- Download the latest DoD certs from [DoD Cyber Exchange ↗](https://public.cyber.mil/pki-pke/)
- Verify the downloaded certs' integrity with a checksum
- Install DoD certs

After the **DoD Certs script** has run, you can access the certs in `/usr/local/share/ca-certificates/DoD`.

> [!NOTE]
> Additional steps may be required to configure your browser with the DoD certs. After browser configuration, users should be able to access DoD Public Key Infrastructure (PKI)-protected information or applications for web sites that require a CAC for authentication. The Snap install of Firefox is not CAC compatible ([see FAQ](./docs/troubleshooting-faq.md)).
<!-- act3-pt end -->

Run the **DoD Certs script**:
<!-- act3-pt ignore -->
<!-- act3-pt ./dod-certs/README.md section:curl-and-run -->
<!-- timestamp:2026-01-01,13:22:55 -->
```sh
curl -fsSL https://raw.githubusercontent.com/act3-ai/up/refs/heads/main/dod-certs/dod-certs | bash
```
<!-- act3-pt end -->

### Get ASCE Tools
<!-- act3-pt ignore -->
<!-- act3-pt ./asce-tools/README.md section:overview -->
<!-- timestamp:2025-10-30,11:21:09 -->
**ASCE tools** uses the ACT3 Homebrew tap and other public taps for public software packages ACT3 team members use.
<!-- act3-pt end -->

<!-- act3-pt ignore -->
<!-- act3-pt ./asce-tools/README.md section:recommended-usage -->
<!-- timestamp:2025-11-04,07:31:48 -->
Add the ACT3 Homebrew Tap:

> [!TIP]
> Running the ACT3 Login script will add the ACT3 Homebrew Tap.

```sh
brew tap act3-ai/tap
```

Then, select one of the following options for installing ASCE Tools.

Install ASCE Tools:

```sh
brew asce-tools
```

Install ASCE Tools and VS Code extensions:

```sh
brew asce-tools --vscode
```
<!-- act3-pt end -->

### Smart Card Reader Setup
<!-- act3-pt ignore -->
<!-- act3-pt ./smart-card-reader/README.md section:overview -->
<!-- timestamp:2025-10-31,11:37:10 -->
The **Smart Card Reader script** will automatically:

- Install:
  - OpenSC
  - Middleware libraries and tools required to read the CAC
  - CACKey
- Enable pcscd
<!-- act3-pt end -->

Run the **Enable Smart Card Reader script**:
<!-- act3-pt ignore -->
<!-- act3-pt ./smart-card-reader/README.md section:recommended-usage -->
<!-- timestamp:2026-01-01,13:22:55 -->
```sh
curl -fsSL https://raw.githubusercontent.com/act3-ai/up/refs/heads/main/smart-card-reader/enable-smart-card-reader | bash
```
<!-- act3-pt end -->

## Support
<!-- act3-pt ignore -->
<!-- update local path after act3-pt docs render -->
<!-- act3-pt ./docs/support.md section:support -->
<!-- timestamp:2025-10-29,10:55:35 -->
- **[Troubleshooting FAQ](./docs/troubleshooting-faq.md)**: consult a list of troubleshooting options and frequently asked questions
- **[Create a Support Ticket issue](https://github.com/act3-ai/up/issues)**: create a support ticket issue on the Up GitHub project
<!-- act3-pt end -->

## Distribution Statement

Approved for public release: distribution unlimited.

### Case Number

| Date | Release Number | Description     |
|------|----------------|-----------------|
| 2024 | AFRL-2024-1007 | Initial release |

<!-- For subsequent releases
| DD MMM YYYY | AFRL-YYYY-NNNN | Second release | -->
