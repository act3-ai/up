# ASCE Tools

## Intended Audience

**ASCE Tools** provides resources for ACT3 team members.

## Overview

**ASCE tools** uses the ACT3 Homebrew tap and other public taps for public software packages ACT3 team members use.

## Usage

### Recommended Usage

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

### Optional Usage

ASCE Tools can be installed without the use of the ACT3 Homebrew Tap using Homebrew's [`brew bundle` command ↗](https://github.com/Homebrew/homebrew-bundle).

Clone the [Up](https://github.com/act3-ai/up/) repository to your system:

```sh
git clone https://github.com/act3-ai/up.git
```

Then, run `brew bundle` on the [ASCE Tools Brewfile](./Brewfile) of your choosing.

> [!TIP]
> The `-v`/`--verbose` flag is used to output formula caveats, which can contain important post-installation instructions.

Install Homebrew tools:

```sh
brew bundle -v --file ./up/asce-tools/Brewfile
```

Or, install Homebrew tools and VS Code extensions:

```sh
brew bundle -v --file ./up/asce-tools/Brewfile-vscode --formula
```

Install Kubectl plugins:

```sh
./up/asce-tools/kubectl-plugins
```

Install Helm plugins:

```sh
./up/asce-tools/helm-plugins
```

## Updates

Update software installed by the ASCE Tools command:

```sh
brew upgrade
```

## Packages

### Homebrew Formulae

The following ACT3 Homebrew Formulae are included in ASCE Tools:

- [`ace-dt`](https://github.com/act3-ai/data-tool): ASCE Data Tool
- [`act3-pt`](https://gitlab.com/act3-ai/asce/pt): ACT3 Project Tool
<!-- update link to act3-pt after it moves to GitHub -->

The following third-party ↗ Homebrew Formulae are included in ASCE Tools:

- [`container-structure-test`](https://github.com/GoogleContainerTools/container-structure-test)
- [`crane`](https://github.com/google/go-containerregistry/blob/main/cmd/crane/README.md)
- [`direnv`](https://github.com/direnv/direnv)
- [`fluxcd/tap/flux`](https://github.com/fluxcd/flux2) (`flux`)
- [`git-lfs`](https://github.com/git-lfs/git-lfs)
- [`glab`](https://gitlab.com/gitlab-org/cli)
- [`helm`](https://github.com/helm/helm)
- [`helmfile`](https://github.com/helmfile/helmfile)
- [`k9s`](https://github.com/derailed/k9s)
- [`kind`](https://github.com/kubernetes-sigs/kind)
- [`krew`](https://github.com/kubernetes-sigs/krew)
- [`kubectx`](https://github.com/ahmetb/kubectx)
- [`kubernetes-cli`](https://github.com/kubernetes/kubectl) (`kubectl`)
- [`kustomize`](https://github.com/kubernetes-sigs/kustomize)
- [`norwoodj/tap/helm-docs`](https://github.com/norwoodj/helm-docs) (`helm-docs`)
- [`oras`](https://github.com/oras-project/oras)
- [`podman`](https://github.com/containers/podman)
- [`skaffold`](https://github.com/GoogleContainerTools/skaffold)
- [`websocat`](https://github.com/vi/websocat)
- [`yq`](https://github.com/mikefarah/yq)

### Kubectl Plugins

The following third-party [`kubectl` plugins](https://kubernetes.io/docs/tasks/extend-kubectl/kubectl-plugins) are included in ASCE Tools:

- [`kubectl view-secret`](https://artifacthub.io/packages/krew/krew-index/view-secret)
- [`kubectl view-allocations`](https://github.com/elsesiy/kubectl-view-secret)
- [`kubectl konfig`](https://github.com/corneliusweig/konfig)
- [`crossplane`](https://docs.crossplane.io/latest/cli) (not a kubectl plugin)

### Helm Plugins

The following third-party ↗[`helm` plugins] are included in ASCE Tools:

- [`helm diff`](https://github.com/databus23/helm-diff)

### VS Code Extensions

The following third-party ↗ VS Code extensions are included in ASCE Tools:

- [`bierner.markdown-mermaid`](https://marketplace.visualstudio.com/items?itemName=bierner.markdown-mermaid)
- [`DavidAnson.vscode-markdownlint`](https://marketplace.visualstudio.com/items?itemName=DavidAnson.vscode-markdownlint)
- [`eamodio.gitlens`](https://marketplace.visualstudio.com/items?itemName=eamodio.gitlens)
- [`ecmel.vscode-html-css`](https://marketplace.visualstudio.com/items?itemName=ecmel.vscode-html-css)
- [`esbenp.prettier-vscode`](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode)
- [`exiasr.hadolint`](https://marketplace.visualstudio.com/items?itemName=exiasr.hadolint)
- [`foxundermoon.shell-format`](https://marketplace.visualstudio.com/items?itemName=foxundermoon.shell-format)
- [`GitHub.remotehub`](https://marketplace.visualstudio.com/items?itemName=GitHub.remotehub)
- [`GitHub.vscode-pull-request-github`](https://marketplace.visualstudio.com/items?itemName=GitHub.vscode-pull-request-github)
- [`GitLab.gitlab-workflow`](https://marketplace.visualstudio.com/items?itemName=GitLab.gitlab-workflow)
- [`Gruntfuggly.todo-tree`](https://marketplace.visualstudio.com/items?itemName=Gruntfuggly.todo-tree)
- [`hediet.vscode-drawio`](https://marketplace.visualstudio.com/items?itemName=hediet.vscode-drawio)
- [`James-Yu.latex-workshop`](https://marketplace.visualstudio.com/items?itemName=James-Yu.latex-workshop)
- [`jeff-hykin.better-dockerfile-syntax`](https://marketplace.visualstudio.com/items?itemName=jeff-hykin.better-dockerfile-syntax)
- [`jinliming2.vscode-go-template`](https://marketplace.visualstudio.com/items?itemName=jinliming2.vscode-go-template)
- [`mindaro.mindaro`](https://marketplace.visualstudio.com/items?itemName=mindaro.mindaro)
- [`ms-azuretools.vscode-docker`](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-docker)
- [`ms-kubernetes-tools.vscode-kubernetes-tools`](https://marketplace.visualstudio.com/items?itemName=ms-kubernetes-tools.vscode-kubernetes-tools)
- [`ms-python.python`](https://marketplace.visualstudio.com/items?itemName=ms-python.python)
- [`ms-python.vscode-pylance`](https://marketplace.visualstudio.com/items?itemName=ms-python.vscode-pylance)
- [`ms-toolsai.jupyter`](https://marketplace.visualstudio.com/items?itemName=ms-toolsai.jupyter)
- [`ms-vscode-remote.vscode-remote-extensionpack`](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.vscode-remote-extensionpack)
- [`ms-vscode.cmake-tools`](https://marketplace.visualstudio.com/items?itemName=ms-vscode.cmake-tools)
- [`ms-vscode.cpptools`](https://marketplace.visualstudio.com/items?itemName=ms-vscode.cpptools)
- [`ms-vscode.live-server`](https://marketplace.visualstudio.com/items?itemName=ms-vscode.live-server)
- [`ms-vscode.remote-explorer`](https://marketplace.visualstudio.com/items?itemName=ms-vscode.remote-explorer)
- [`ms-vsliveshare.vsliveshare`](https://marketplace.visualstudio.com/items?itemName=ms-vsliveshare.vsliveshare)
- [`njpwerner.autodocstring`](https://marketplace.visualstudio.com/items?itemName=njpwerner.autodocstring)
- [`peterj.proto`](https://marketplace.visualstudio.com/items?itemName=peterj.proto)
- [`redhat.vscode-yaml`](https://marketplace.visualstudio.com/items?itemName=redhat.vscode-yaml)
- [`Remisa.shellman`](https://marketplace.visualstudio.com/items?itemName=Remisa.shellman)
- [`tamasfe.even-better-toml`](https://marketplace.visualstudio.com/items?itemName=tamasfe.even-better-toml)
- [`timonwong.shellcheck`](https://marketplace.visualstudio.com/items?itemName=timonwong.shellcheck)
- [`tomoki1207.pdf`](https://marketplace.visualstudio.com/items?itemName=tomoki1207.pdf)
- [`twxs.cmake`](https://marketplace.visualstudio.com/items?itemName=twxs.cmake)
- [`yzane.markdown-pdf`](https://marketplace.visualstudio.com/items?itemName=yzane.markdown-pdf)
- [`yzhang.markdown-all-in-one](https://marketplace.visualstudio.com/items?itemName=yzhang.markdown-all-in-one)

## Support
<!-- act3-pt ignore -->
<!-- act3-pt ../docs/support.md section:support -->
<!-- timestamp:2025-10-29,09:24:22 -->
- **[Troubleshooting FAQ](../docs/troubleshooting-faq.md)**: consult a list of troubleshooting options and frequently asked questions
- **[Create a Support Ticket issue](https://github.com/act3-ai/up/issues)**: create a support ticket issue on the Up GitHub project

<!-- act3-pt end -->
