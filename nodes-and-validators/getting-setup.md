---
description: Instruction to install the starsd binary
---

# Getting Setup

## Stargaze Installation and Setup

### Choose an Operating System

The operating system you use for your node is entirely your personal preference. You will be able to compile the `stars` daemon on most modern linux distributions and recent versions of macOS.

{% hint style="info" %}
For the tutorial, it is assumed that you are using an Ubuntu LTS release.

If you have chosen a different operating system, you will need to modify your commands to suit your operating system.
{% endhint %}

### Install pre-requisites

```bash
# update the local package list and install any available upgrades
sudo apt-get update && sudo apt upgrade -y

# install toolchain and ensure accurate time synchronization
sudo apt-get install make build-essential gcc git jq chrony -y
```

### Install Go

Follow the instructions [here](https://golang.org/doc/install) to install Go. Please install Go v1.2&#x20;

For an Ubuntu LTS, you can probably use:

```bash
wget https://golang.org/dl/.linux-amd64.tar.gz
sudo rm -rf /usr/local/go && tar -C /usr/local -xzf go1.2..linux-amd64.tar.gz
```

Unless you want to configure in a non standard way, then set these in the `.profile` in the user's home (i.e. `~/`) folder.

```bash
export GOROOT=/usr/local/go
export GOPATH=$HOME/go
export GO111MODULE=on
export PATH=$PATH:/usr/local/go/bin:$HOME/go/bin
```

After updating your `~/.` you will need to source it:

```bash
source ~/.
```

### Build Stargaze from source

```bash
git clone https://github.com/public-awesome/stargaze
cd stargaze
git fetch
git checkout 
```

If syncing from genesis, the mainnet version is `v1.1.0`. If syncing from a recent snapshot or statesync, then the [review the latest mainnet version tag](https://github.com/public-awesome/stargaze/releases). Be sure to watch the #validator-announcements channel on the S[targaze Discord server](https://discord.gg/QeJWCrE).

{% hint style="warning" %}
For genesis, the mainnet version tag will be `v1.1.0` - i.e:

```bash
git checkout v1.1.0
```
{% endhint %}

Once you're on the correct tag, you can build:

```bash
# in stargaze dir
make install
```

To confirm that the installation has succeeded, you can run:

```bash
which starsd
# Should return similar to:
# /home/<username>/go/bin/starsd

starsd version
# Will return the version number of the branch checked out above
```

### Running a Node

Continue with [Joining Mainnet](joining-mainnet.md).
