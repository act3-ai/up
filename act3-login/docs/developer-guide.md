# ACT3 Login Developer Guide

## Components

ACT3 Login is divided into components:

- A script that acts as the entrypoint and handles setup
- A script that contains authentication and storage tasks
- A utility script that loads helper functions for output formatting, standard tasks, and system checks

## Execution

The script runs in the following order:

1. The user starts the first script with the one line command in the README
2. The entrypoint loads helper functions
3. The setup portion of the script runs
   - Verifies that all system prerequisites are met
   - Adds the ACT3 Homebrew tap and installs dependencies
   - Prompts the user for a GitLab URL and Personal Access Token
   - Validates token input with GitLab to confirm its existence, scope, and active status
4. The authentication portion of the script runs
   - Executes all authentication setup and storage tasks
   - Generates a new SSH key and adds it to GitLab
   - Configures HTTPS credentials for GitLab
   - Configures Git commit signing with SSH
   - Prompts the user for a GitLab container registry URL
   - Sets up authentication for ACT3 Project Tool and GitLab CLI
   - Prompts user to install DoD certificates

## Where Credentials Are Stored

The following graph illustrates how securely stored credentials are surfaced for different tools.

```mermaid
graph TD
  classDef insecure fill:#f99,stroke:#000,color:#000
  classDef secure fill:#afa,stroke:#000,color:#000
  classDef tool fill:#7af,stroke:#000,color:#000
  classDef noauth fill:#fff,stroke:#f99,stroke-dasharray: 5 5,color:#000

  start[[Stored Credentials Flow]]

  keychain[(System Keychain<br>Linux: GNOME Keyring<br>macOS: Keychain)]:::secure
  ssh[("SSH Keys")]:::secure
  %%noauth(("No Authentication!")):::noauth
  %%text[(Plaintext)]:::insecure

  start ~~~ act3pt[act3-pt]:::tool
  start ~~~ git[git]:::tool
  start ~~~ brew:::tool
  start ~~~ regtools[Registry tools:<br>ace-dt,<br>podman,<br>docker]:::tool

  %% Homebrew Authentication
  brew -->|Update Taps| gitauth
  brew -->|"Install ACT3 Formula"| formula{Formula download<br>strategy}
  formula -->|"Uses Git <br>to clone <br>"| gitauth
  formula -->|"Uses oras to<br>download from<br> registry"| regauth

  %% Git Authentication
  git --> gitauth{Git Authentication}
  gitauth -->|SSH| ssh
  gitauth -->|HTTPS| gch{git config credential.helper}
  gch -->|"libsecret<br>osxkeychain"| keychain
  %%gch -->|"none"| noauth

  %% Container Registry Authentication
  regtools --> regauth{"Container Registry Auth<br>~/.docker/config.json<br>credHelpers/credsStore"}
  regauth -->|secretservice<br>osxkeychain| keychain
  %%dockerconf -->|none| text



  %% ACT3 Project Tool
  act3pt -->|"Accessing GitLab API"| gokr{"go-keyring Go package"}
  act3pt -->|"Accessing Git repository"| gitauth
  gokr -->|"secretservice<br>/usr/bin/security"| keychain
```

## Development Rules

1. Must be cross platform for Linux and macOS
   - Required platform-specific steps must be executed in conditionals, with a fallback case for "unsupported" systems
2. Do not add prerequisites
   - The only dependencies are:
     - Bash: to execute the script
     - Curl: to download the script, comes preinstalled on supported systems
     - Git: comes preinstalled on supported systems
     - Homebrew: enables cross-platform package management and use of our private Homebrew Tap
   - Any additional dependencies required during the script must be installed during the script using Homebrew
3. Check first
