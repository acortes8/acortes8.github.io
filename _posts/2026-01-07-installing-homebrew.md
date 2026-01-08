---
title: Installing Homebrew (MacOS)
date: 2026-01-07
categories: [Learning, Guides]
tags: [mac, homebrew, guides, learning, installing]
---

1. Open the terminal.
2. Run the code below:
```shell
$ /bin/bash -c "$(curl -fsSL \
  https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```
3. Complete the steps the terminal will prompt you to take. At the present those steps will likely be as follows:
~~~bash
$ echo >> ~/.zprofile
$ echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> /.zprofile
$ eval "$(/opt/homebrew/bin/brew shellenv)"
~~~
4. Done.
