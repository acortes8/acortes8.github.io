---
title: Installing Python (MacOS)
date: 2026-01-13
categories: [Learning, Guides]
tags: [mac, python, uv, guides, learning, installing]
---

There are several ways of installing Python. You could use Homebrew, or the download it directly from the Python website. I decided to use *UV*.

## What is UV
UV is a Python package and project manager. Which means many things, but this includes being a version management tool, so think of it as Python's version of *rbenv* for *Ruby*. It does additional things as well, but for now simplified version management is our reason for using it.

## How to install UV
1. Install UV by running the command below:
	```shell
    $ curl -LsSf https://astral.sh/uv/install.sh | sh
	```

2. After running this command you will be asked to restart the terminal, do so now.
   
3. After installation you can run the `uv` command in the terminal to check if it is working. This will look like this:
    ```shell
    $ uv
    An extremely fast Python package manager.

    Usage: uv [OPTIONS] <COMMAND>
  
    ...
    ```
4. Enable shell autocompletion by running the following command (this example assumes you're using zsh):
   ```shell
   $ echo 'eval "$(uv generate-shell-completion zsh)"' >> ~/.zshrc
   ```
   Autocompletion will now work, after a terminal restart.
5. Done, now you can install Python through UV. 

## Installing the latest Python version via UV
This will install the latest Python distribution from the Astral python-build-standalone project. 
1. Run the following command:
   ```shell
   $ uv python install
   ```
2. Once installed, it will be used by UV commands automatically. UV also adds installed Python versions to your PATH, so you may call it like so:
   ```shell
   $ python3.14
   ```
3. Done.

## Installing a specific Python version
You can install a specific version like so:
```shell
$ uv python install 3.12
```

You can also install multiple specific versions at the same time like so:
```shell
$ uv python install 3.11 3.12
```

## View Python installations
To view available and installed Python versions:
```shell
$ uv python list
```

## Updating Python versions
The update behavior in UV is in experimental as I write this, so instead of using an experimental feature I would lean towards using the reinstallation feature for updating Python. It will reinstall all previously installed Python versions. You can use this feature like so:
```shell
$ uv python install --reinstall
```

## Upgrading UV
> Updating UV will re-run the installer and can modify your shell profiles.
{: .prompt-info }

To update UV if needed, run `$ uv self update`.

## UV docs
[View the UV docs here](https://docs.astral.sh/uv/)