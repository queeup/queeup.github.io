---
layout: blog
title: Ubuntu/Linuxmint apt depolarım
---
> **Not:** Bu depolar sadece Ubuntu 14.04(Trusty) ve Linuxmint 17(Rebecca) içindir.

#### _cinnamon.list_: Cinnamon masaüstünün en güncel kararsız sürümü için.
`deb http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-nightly/ubuntu trusty main`

eklemek için:

```bash
sudo sh -c 'echo "deb http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-nightly/ubuntu trusty main" >> /etc/apt/sources.list.d/cinnamon.list' sudo apt-key adv --keyserver keyserver.ubuntu.com --recv 28949509
```
----------
#### *google.list*: Google Talk eklentisi ve Google Music için.
`deb http://dl.google.com/linux/musicmanager/deb/ stable main`
`deb http://dl.google.com/linux/talkplugin/deb/ stable main`

eklemek için:

```bash
sudo sh -c 'echo "deb http://dl.google.com/linux/talkplugin/deb/ stable main" >> /etc/apt/sources.list.d/google.list' | sudo apt-key adv --keyserver keyserver.ubuntu.com --recv 7FAC5991
```
----------
#### _transmission.list_: Transmission torrent programının en güncel stabil sürümü için.
`deb http://ppa.launchpad.net/transmissionbt/ppa/ubuntu trusty main`

eklemek için:

```bash
sudo sh -c 'echo "deb http://ppa.launchpad.net/transmissionbt/ppa/ubuntu trusty main" >> /etc/apt/sources.list.d/transmission.list' | sudo apt-key adv --keyserver keyserver.ubuntu.com --recv 365C5CA1
```
----------
#### _virtualbox.list_: Virtualbox'ın en güncel sürümü için.
`http://download.virtualbox.org/virtualbox/debian trusty contrib`

eklemek için:

```bash
sudo sh -c 'echo "http://download.virtualbox.org/virtualbox/debian trusty contrib" >> /etc/apt/sources.list.d/virtualbox.list' sudo apt-key adv --keyserver keyserver.ubuntu.com --recv 98AB5139
```
----------
#### _timeshift.list_: TimeShift.
`deb http://ppa.launchpad.net/teejee2008/ppa/ubuntu trusty main`

eklemek için:

```bash
sudo sh -c 'echo "deb http://ppa.launchpad.net/teejee2008/ppa/ubuntu trusty main" >> /etc/apt/sources.list.d/timeshift.list' | sudo apt-key adv --keyserver keyserver.ubuntu.com --recv 2D0F61F0
```
----------
#### _musescore.list_: MuseScore.
`deb http://ppa.launchpad.net/teejee2008/ppa/ubuntu trusty main`

eklemek için:

```bash
sudo sh -c 'echo "deb http://ppa.launchpad.net/mscore-ubuntu/mscore-stable/ubuntu trusty main" >> /etc/apt/sources.list.d/musescore.list' | sudo apt-key adv --keyserver keyserver.ubuntu.com --recv 3A258030
```
----------
#### _unetbootin.list_: UNetbootin.
`deb http://ppa.launchpad.net/gezakovacs/ppa/ubuntu trusty main`

eklemek için:

```bash
sudo sh -c 'echo "deb http://ppa.launchpad.net/gezakovacs/ppa/ubuntu trusty main" >> /etc/apt/sources.list.d/unetbootin.list' | sudo apt-key adv --keyserver keyserver.ubuntu.com --recv FC91AE7E
```
