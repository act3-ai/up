# ACT3 Login

## Overview

ACT3 Login is designed to:

- Authenticate users to ACT3 services
- Promote secure credential management
- Simplify system setup

ACT3 Login does the following:

- Enables secure credential storage using your system's keychain
- Adds the [ACT3 Homebrew Tap](https://github.com/act3-ai/homebrew-tap) for easy access to ACT3 software
- Enables commit signing with your SSH key
- Authentication for the following:
  - ACT3 GitLab Git access over SSH and HTTPS
  - ACT3 GitLab Container Registry
  - ACT3 Project Tool (`act3-pt`)
  - Optional: ACT3 Kubernetes cluster access
  - ACE Hub
    - Creates Kubernetes secrets in your namespace on the Lion cluster

## Prerequisites

- Linux, macOS, or WSL2 running Ubuntu 22.04 (**Windows is only supported through WSL2**)
- ACT3 Active Directory account
- User account with sudo privileges on your system
  - List your sudo privileges with `sudo -l`
- [curl](https://everything.curl.dev/) installed
  - Check your system for curl with `which curl`
  - If missing, follow system-specific instructions from *Everything curl*: [Install curl](https://everything.curl.dev/get)
- [Git](https://git-scm.com) installed
  - Check your system for Git with `which git`
  - If missing, follow system-specific instructions from Git: [Installing Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)
- [Homebrew](https://brew.sh/) installed
  - Check your system for Homebrew with `which brew`
  - If missing, install with [Homebrew's installation script](https://brew.sh/) (*be sure to complete tasks under **Next Steps***)
  - Check your installation of Homebrew by running `brew doctor`

## Run ACT3 Login

```sh
/usr/bin/env bash -c "$(curl -fsSL https://gitlab.com/act3-ai/asce/up/-/raw/main/act3-login/act3-login)"
```

> Check the [prerequisites](#prerequisites) before running.

## New User Setup

After running the login script above, new users should also consider installing common ASCE Tools by running the `asce-tools` command:

```sh
brew asce-tools
```

## Features

ACT3 Login uses your entered credentials to do the following:

- Enable secure credential storage for Git and container registry authentication
- Authenticate Git for SSH and HTTPS access to the ACT3 GitLab
- Enable Git commit signing with your SSH key
- Store credentials for the ACT3 GitLab Container Registry to be used by tools like ACE Data Tool, Podman, and Docker
- Add the ACT3 Homebrew Tap
  - ACT3's package catalog that includes tools like ACE Data Tool and ACT3 Project Tool
- Authenticate ACT3 Project Tool and `glab` for the ACT3 GitLab
- Configure ACE Data Tool to use the ACT3 Telemetry server
- **OPTIONAL:** Set up ACT3 Kubernetes cluster access
- Creates Kubernetes secrets for ACE Hub in your namespace on the Lion cluster:
  - Image pull secret "act3"
  - Envfile secret "hub-envfile"
  - Env secret "hub-env"

## Caveats

- ACT3 Login configures tools installed by Homebrew. Using alternate installations of the same tools configured by ACT3 Login may produce unexpected behavior after running the script.
- Existing configuration for some affected applications can override ACT3 Login's changes.
  - If Podman is configured with an `auth.json` file for credentials, those credentials will be used rather than the keychain storage set up by ACT3 Login. Delete entries in `auth.json` corresponding to "reg.git.act3-ace.com" to fix this.
  - ACE Data Tool configuration is never overwritten by ACT3 Login. Back up your existing ACE Data Tool config file and rerun ACT3 Login to see the config file it creates.

## Support

- **[Troubleshooting FAQ](docs/troubleshooting-faq.md)**: consult list of frequently asked questions and their answers.
- **[Create a support ticket](https://gitlab.com/act3-ai/asce/up/issues/new)**: create a support ticket issue on the ASCEup GitLab project.
- **[Mattermost channel](https://chat.git.act3-ace.com/act3/channels/devops)**: create a post in the DevOps channel for assistance.
