# ASCEup

## Overview

The ASCEup repository is a collection of script-based tools and resources to bootstrap access to ACT3 services. The following tools are contained in this repo:

- [ACT3 Login script](./act3-login/README.md)
- [DoD Certs script](./dod-certs/README.md)
- [ASCE Tools installers](./asce-tools/README.md)
- [Smart Card Reader script](./smart-card-reader/README.md)

This repository is intended for users who need to authenticate and configure their macOS, Ubuntu 22.04, or WSL2 (running Ubuntu 22.04) machines for work in the ACT3 environment.

## Usage

### ACT3 Login

It is recommended users run the [ACT3 Login script](./act3-login/README.md) to authenticate to ACT3's services.

ACT3 Login will automatically:

- Authenticate users to ACT3 services
- Ask to run the DoD Certs script
- Add ACT3 Homebrew tap (enabling access to ACT3 software packages)

Run the [ACT3 Login script](./act3-login/README.md):

<!-- act3-pt ignore -->
<!-- act3-pt ./act3-login/README.md section:run-act3-login -->
<!-- timestamp:2024-02-23,17:03:13 -->
```sh
/usr/bin/env bash -c "$(curl -fsSL https://gitlab.com/act3-ai/asce/up/-/raw/main/act3-login/act3-login)"
```

> [!IMPORTANT]
>
> Check the [prerequisites](./act3-login/README.md#prerequisites) before running.
<!-- act3-pt end -->

### New User Setup

<!-- act3-pt ignore -->
<!-- act3-pt ./act3-login/README.md section:new-user-setup -->
After running the login script above, new users should also consider installing common ASCE Tools by running the `asce-tools` command:

```sh
# Install common ASCE tools
brew asce-tools
```
<!-- act3-pt end -->

### Smart Card Reader Setup

<!-- act3-pt ./smart-card-reader/README.md section:recommended-usage -->
<!-- timestamp:2024-10-01,10:26:09 -->
Ubuntu users who need to install and configure their system to work with a smart card reader should complete the following:

Run the [`enable-smart-card-reader` script](./smart-card-reader/enable-smart-card-reader).

```sh
/usr/bin/env bash -c "$(curl -fsSL https://gitlab.com/act3-ai/asce/up/-/raw/main/smart-card-reader/enable-smart-card-reader)"
```
<!-- act3-pt end -->

> Read more about smart card usage on Linux: [smart-card-reader/README.md](./smart-card-reader/README.md)

## Optional Usage: Clone Repo and Run

Clone the [ASCEup](https://gitlab.com/act3-ai/asce/up) repository to your system:

```sh
git clone https://gitlab.com/act3-ai/asce/up.git
```

Then, run the desired script:

```sh
./up/<path to script>
```

## Support

- **[Troubleshooting FAQ](docs/troubleshooting-faq.md)**: consult list of frequently asked questions and their answers
- **[Create a Support Ticket issue](https://gitlab.com/act3-ai/asce/up/issues/new)**: create a support ticket issue on the ASCEup GitLab project
- **[Mattermost channel](https://chat.git.act3-ace.com/act3/channels/devops)**: create a post in the DevOps channel for assistance

---

Approved for public release: distribution unlimited. Case Numbers: AFRL-2024-1007
