---
weight: 2
title: Ubuntu
bookToc: false
---

# Ubuntu 2022

## Enhanced Hyper-V Session

[Reference](https://www.nakivo.com/blog/install-ubuntu-20-04-on-hyper-v-with-enhanced-session/)

``` bash
wget https://raw.githubusercontent.com/Hinara/linux-vm-tools/ubuntu20-04/ubuntu/20.04/install.sh
sudo chmod +x install.sh
sudo ./install.sh
shutdown

Set-VM -VMName Ubuntu22 -EnhancedSessionTransportType HvSocket
```

## App Store

[Reference](https://snapcraft.io/store)

``` bash
sudo snap install node --channel=18/stable --classic
npm config set prefix '~/npm-prefix/'
sudo apt-get install git-gui
```

## Packages

* __snap__ snapcraft.io
