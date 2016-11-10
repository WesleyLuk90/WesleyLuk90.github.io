---
layout: page
title:  "Reinstall"
permalink: /reinstall
date:   2016-04-23 2:38:00 -0700
---

Here are my personal notes on what I should backup when I reformat my computer

# Backup

## User Folder

```
	robocopy C:\Users\wesleyluk F:/Backups/2016-4-23/wesleyluk /e /z /xj /mt:5 /r:1 /w:1 /xd C:\Users\wesleyluk\OneDrive\ /xd C:\Users\wesleyluk\Dropbox\ /xd node_modules
```

## Ninite

[My Installer](https://ninite.com/7zip-chrome-dropbox-firefox-foxit-itunes-jdk8-jdkx8-klitecodecs-python-skype-vlc-windirstat/)

## Webserver/Database

## Home Folder (cygwin)

# Install

## General

1. Graphics Drivers
2. Chrome
3. 7zip
4. [AutoHotkeys](/autohotkey)
4. [Startup Scripts](/startup-scripts)
4. [Push to Talk Key](/ptt-key)

## Development

1. Sublime Text
2. nodejs
3. Console (cmder, conemu)
4. cygwin [Install Script](/files/cygwin-install.bat)

# Configuration
1. Disable User Account Control
2. Disable Windows Defender [Instructions](http://www.tenforums.com/tutorials/5918-windows-defender-turn-off-windows-10-a.html)
3. Disable Windows Firewall
4. Disable Power Settings
5. Disable Keyboard Switch Hotkey

	Control Panel > Language > Advanced > Switching input methods > Change language bar hotkeys > Change Key Sequence

6. Disable Grouping Icons
7. Make AppData folder not hidden
8. Disable Skype Ads [Insturctions](http://www.cnet.com/how-to/how-to-disable-ads-in-skype/)
