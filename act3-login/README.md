# ACT3 Login

## Intended Audience

**ACT3 Login** simplifies authentication, credential storage, and setup steps for ACT3 team members.

## Overview

**ACT3 Login** is designed to:

- Authenticate users to ACT3 services
- Promote secure credential management
- Simplify system setup

## Features

The **ACT3 Login script** will automatically:

- Authenticate to a user-defined GitLab instance including:
  - Prompt for and validating your GitLab Personal Access Token
  - Create an SSH key and add it to GitLab
  - Enable secure credential storage for Git and container registry authentication
  - Enable Git commit signing with your SSH key
- Add Homebrew taps for public resources ACT3 teams use
- Add the ACT3 Homebrew tap (for access to public ACT3 software packages)
- Prompt to run the DoD Certs script

## Prerequisites

- Linux, macOS, or WSL2 running Ubuntu 22.04 or higher (**Windows is only supported through WSL2**)
- User account with sudo privileges on your system
  - List your sudo privileges with `sudo -l`
- [curl ↗](https://everything.curl.dev/) installed
  - Check your system for curl with `which curl`
  - If missing, follow system-specific instructions from *Everything curl*: [Install curl ↗](https://everything.curl.dev/get)
- [Git ↗](https://git-scm.com) installed
  - Check your system for Git with `which git`
  - If missing, follow system-specific instructions from Git: [Install Git ↗](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)
- [Homebrew ↗](https://brew.sh/) installed
  - Check your system for Homebrew with `which brew`
  - If missing, install with [Homebrew's installation script ↗](https://brew.sh/) (*be sure to complete tasks under **Next Steps***)
  - Check your installation of Homebrew by running `brew doctor`
- `ssh-agent` running
  - Check your system for the agent status with `ssh-add -l; echo "Exit code: $?"`
  - If the command fails with an exit code of 2, the ssh-agent is not running on your system.
  - If not running, start the agent with `eval "$(ssh-agent -s)"`
- [OpenSSL ↗](https://github.com/openssl/openssl/) 3.2 or higher (if running DoD Certs portion of ACT3 Login)
  - Check your system for OpenSSL v3.2 or greater with `openssl version`
  - If missing, install with Homebrew `brew install openssl` or consult the [OpenSSL documentation ↗](https://github.com/openssl/openssl/?tab=readme-ov-file#build-and-install) for alternatives
  - Your terminal will need to be sourced or restarted for these changes to take effect.

## Caveats

- ACT3 Login configures tools installed by Homebrew. Using alternate installations of the same tools configured by ACT3 Login may produce unexpected behavior after running the script.
- Existing configuration for some affected applications can override ACT3 Login's changes.
- If Podman is configured with an `auth.json` file for credentials, those credentials will be used rather than the keychain storage set up by ACT3 Login.

## Usage

> [!IMPORTANT]
> Check the [prerequisites](#prerequisites) before running.

### Recommended Usage

#### Run ACT3 Login

```sh
curl -fsSL https://raw.githubusercontent.com/act3-ai/up/refs/heads/main/act3-login/act3-login | bash -c -
```

### Optional Usage

#### Clone Repo and Run

Clone the [Up](https://github.com/act3-ai/up) repository to your system:

```sh
git clone git@github.com:act3-ai/up.git
```

Then, run the [`act3-login` script](./act3-login):

```sh
./up/act3-login/act3-login
```

## Support
<!-- act3-pt ignore -->
<!-- act3-pt ../docs/support.md section:support -->
<!-- timestamp:2025-10-29,09:24:22 -->
- **[Troubleshooting FAQ](../docs/troubleshooting-faq.md)**: consult a list of troubleshooting options and frequently asked questions
- **[Create a Support Ticket issue](https://github.com/act3-ai/up/issues)**: create a support ticket issue on the Up GitHub project

<!-- act3-pt end -->
