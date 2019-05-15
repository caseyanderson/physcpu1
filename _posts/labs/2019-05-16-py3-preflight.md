---
layout: post
title:  "Python3 Pre-flight"
date:   2019-05-16 06:00:00 -0700
week: 1
number: 1
tags: lab
---

Below are instructions regarding installing tools needed for general development with Python3. They include:

* [Xcode](https://developer.apple.com/xcode/) (Command Line Tools)
* [Homebrew](http://brew.sh/)
* [Python3](https://www.python.org/)
* [PyPI](https://pypi.python.org/pypi)
* [Jupyter](https://jupyter.org/index.html)


## Xcode / The Command Line Tools

Do you have **Xcode**? To check go to the terminal and execute `xcode-select -p`.

* If `/Applications/Xcode.app/Contents/Developer` (or something similar) appears as a response proceed to the next step.
* If anything else happens download and install `Xcode` from [here](https://itunes.apple.com/us/app/xcode/id497799835?mt=12) before moving on.

Enter `xcode-select --install` into the terminal, which should result in something like this:

![]({{site.url}}/assets/xcode-select_install_cmnd_line_tools.png)

Click `Install` to download and install the **Xcode Command Line Tools** (it takes a while so maybe go make some food or get a cup of coffee or something).


## Homebrew

Copy and paste this code into the terminal and press `enter` to install [homebrew](http://brew.sh/): `/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"`

If prompted, agree to the **Xcode** license

![]({{site.url}}/assets/agree_to_xcode_license.png)

by executing `sudo xcodebuild -license` in the terminal.

Search to see if something is available on `homebrew` with `search`. For example:  `brew search python3`


## Python3

To install **Python3** execute `brew install python3` in the terminal.


## PyPI

**PyPi** is frequently referred to as `pip`. It is used to manage **Python** library installations and ships with **Python3** when installed via **Homebrew**. The command to use it is `pip3`, **not** `pip`.

Search for something on `pip3` with the `search` command. For example: `pip3 search jupyter`


## Jupyter

Install **Jupyter** via `pip3` as follows:
1. `pip3 install --upgrade pip`
2. `pip3 install jupyter`

Executing `jupyter notebook` in the terminal starts the [IDE](https://en.wikipedia.org/wiki/Integrated_development_environment).

![]({{site.url}}/assets/jupyterhome.png)

On the **Jupyter** homepage click `New` and select **Python3**. This will create and open an **iPython Notebook** file.

![]({{site.url}}/assets/pyjupyternotebook.png)

Click `File`, select `Save As` and then name the file. Next click `File` and select `Close and Halt` to exit.

When you return to the **Jupyter** homepage you should see the **iPython Notebook** file (`.ipynb`) that you just saved.

![]({{site.url}}/assets/jupyteripynb.png)
