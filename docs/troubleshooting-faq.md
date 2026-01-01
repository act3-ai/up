# Up Troubleshooting & FAQ

<!--This document is a place to capture questions that have come up repeatedly by existing users and that can be answered in a helpful manner through written documentation. The contents included here should be generalizable enough to apply to all users with the same or similar questions. This is not an appropriate place to document issues or questions that are individualized to a particular environment or use case.-->

## Overview

This document presents troubleshooting options and frequently asked questions (FAQs) for scripts in the Up repository.

## Troubleshooting

### ACT3 Login

**ACT3 Login produces a log file with detailed logs from its execution. This is the first place to check when troubleshooting an issue with the script.**

If you are not able to identify the problem, first consult the FAQs below. Then, complete the following troubleshooting steps:

1. Read the log file created by ACT3 Login
   - [How to find the log file](#how-do-i-find-act3-login-script-logs)
2. Run `brew doctor` to check your installation of Homebrew for issues
   - Address any issues
   - Repeat process until `brew doctor` states `Your system is ready to brew.`
3. Check your Docker config: `~/.docker/config.json`
   - Remove all references to the GitLab instance you are logging into
   - Remove all references to `credsStore` and `credHelpers`
   - Re-run ACT3 Login

If you are still not able to resolve the issue, [create a support ticket](https://github.com/act3-ai/up/issues).

### Homebrew

>[!NOTE]
> Frequently needed steps for troubleshooting Homebrew issues are provided here for convenience. Consult [Homebrew's Troubleshooting documentation ↗](https://docs.brew.sh/Troubleshooting) for other issues.

Run the following command to check for issues with your installation of Homebrew:

```sh
brew doctor
```

Address any issues identified by `brew doctor` and repeat the command until `brew doctor` states that `Your system is ready to brew.`

#### Homebrew Installation Issues

The Homebrew installation script prompts the user with tasks to complete to finish installing Homebrew. If you did not complete these tasks, you may have an incomplete installation of Homebrew. If you recently installed Homebrew and are unsure if you completed Homebrew's finishing tasks, use [Homebrew's uninstall script ↗](https://github.com/homebrew/install#uninstall-homebrew), then [reinstall ↗](https://brew.sh/).

Run the following command to check if Homebrew's bin directories are on your PATH:

```sh
[[ ":$PATH:" == *":$(brew --prefix)/bin:"* ]] && [[ ":$PATH:" == *":$(brew --prefix)/sbin:"* ]] && echo "PASS" || echo "FAIL"
```

Add the following line to your `~/.bashrc` file to add Homebrew's bin directories to your PATH:

```sh
eval "$(brew shellenv)"
```

<!-- Source: https://github.com/Homebrew/install/blob/master/install.sh#L1021 -->

Your terminal will need to be sourced or restarted for these changes to take effect.

### ssh-agent

Check if the ssh-agent is running on your system:

```sh
ssh-add -l; echo "Exit code: $?"
```

If the command fails with an exit code of 2, the ssh-agent is not running on your system, which may affect SSH authentication.

Start ssh-agent:

```sh
eval "$(ssh-agent -s)"
```

> [!TIP]
> You can update your .bashrc file for persistence.

## FAQs

### I received a warning from running the ACT3 Login script indicating that ssh-agent is not running on my system. How do I correct this?

See the [ssh-agent troubleshooting](#ssh-agent) section above.

### How do I find ACT3 Login script logs?

ACT3 Login produces a log file at the location `$XDG_CACHE_HOME/up/act3-login/logs.txt`. If `$XDG_CACHE_HOME` unset or empty on your system, its default value is used. ACT3 Login prints the path to the log file on your system after the welcome message, in the format `Created log file <log file>`. If the script aborts, the path to the log file will be printed to your terminal before exiting.

Note: WSL2 users can open File Explorer from the Ubuntu terminal by running `explorer.exe <path>`

> `$XDG_CACHE_HOME` is defined by the [XDG Base Directory specification](https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html).
>
> | System | Default `$XDG_CACHE_HOME` | Default log file                           |
> | ------ | ------------------------- | ------------------------------------------ |
> | Linux  | `$HOME/.cache`            | `$HOME/.cache/up/act3-login/logs.txt`         |
> | macOS  | `$HOME/Library/Caches`    | `$HOME/Library/Caches/up/act3-login/logs.txt` |

### How do I find the DoD certs on my machine?

Navigate to `/usr/local/share/ca-certificates/DoD`.

### What is OpenSC?

<!-- act3-pt ignore -->
<!-- act3-pt https://github.com/OpenSC/OpenSC.wiki.git file:Home.textile lines:1 -->
<!-- ref:a4055e4 -->
OpenSC provides a set of libraries and utilities to work with smart cards. Its main focus is on cards that support cryptographic operations, and facilitate their use in security applications such as authentication, mail encryption and digital signatures. OpenSC implements the standard APIs to smart cards, e.g. ["PKCS#11 API" ↗](https://www.oasis-open.org/committees/pkcs11/), ["Windows' Smart Card Minidriver" ↗](https://learn.microsoft.com/en-us/previous-versions/windows/hardware/design/dn631754(v=vs.85)) and macOS CryptoTokenKit.

<!-- act3-pt end -->

### Why am I being prompted for a smart card and PIN on the login screen after installing OpenSC?

Installing OpenSC causes Ubuntu installations to ask for a smart card and PIN on the login screen, but only when a smart card is plugged in. Unplugging the smart card brings the normal username/password prompt back.

> Note: A YubiKey is recognized as a smart card and therefore must also be unplugged at the login screen.

This is an issue with the GDM3 display manager for the GNOME Desktop. The LightDM display manager does not have this problem. To fix the display manager issue by using the LightDM display manager, run:

```sh
sudo apt install lightdm
```

### Why does my AFRL Google Cloud Authentication fail if my CAC is working?

There is a known issue when attempting to authenticate to the [AFRL Google Cloud Portal](http://internal.afresearchlab.com/) that results in authentication failure if a YubiKey and CAC are both plugged in.

The resolution to this issue is to unplug the YubiKey before attempting to log in to an AFRL GSuite account.

### I am running Snap Firefox on Ubuntu. What should I do if I need to authenticate to a web site using a CAC?

The Snap install of Firefox is not CAC compatible. Ensure that Snap version of Firefox is uninstalled and that APT version of Firefox is being used.

> [!TIP]
> Follow the [official Firefox documentation ↗](https://support.mozilla.org/en-US/kb/install-firefox-linux?utm_source=www.mozilla.org&utm_medium=referral&utm_campaign=firefox-download-thanks#w_install-firefox-deb-package-for-debian-based-distributions-recommended) ↗.

Reboot your machine after switching to the APT install.

The `pcscd` daemon is used to manage connections to smart card readers. Uninstalling the Snap version of Firefox may cause the `pcscd` daemon to stop running and/or not be initiated after reboot.

To check that the card slot is still recognized at the system level:

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

To check that `pcscd` is still running:

```sh
systemctl status pcscd
```

To restart `pcscd`:

```sh
systemctl restart pcscd
```

Ensure that `pcscd` is set to start on boot:

```sh
systemctl enable pcscd.socket
```

### My GitLab Personal Access Token expired. How do I update it for ACT3 Login?

1. Run the [ACT3 Login script](https://github.com/act3-ai/up/blob/main/README.md#act3-login). You will be prompted to create a new Personal Access Token.
2. Create a token with the scope of `api` selected.
3. Provide the value of the new token when prompted.

### I updated my GitLab Personal Access Token but my previous token is still stored when I check the keyring. How do I update it?

Try relaunching the keyring GUI, it might not have updated yet.

### Why am I getting this error during ACT3 Login's Git credential setup? git: credential-osxkeychain' is not a git command

You may be using an alternate installation of Git.

1. Check what Git executable you are using: `which -a git`
2. If there are multiple entries, run `brew uninstall git` and then rerun ACT3 Login

If the problem persists, run `git --help`
