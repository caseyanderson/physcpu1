---
layout: labs
title:  "Command Line Tools (Installation)"
date:   2019-01-10 06:00:00 -0700
week: 1
number: 1
tags: lab
---

## Is Xcode on my computer?

Do you have [Xcode](https://developer.apple.com/xcode/) on your computer? We are not going to use it in this class, but need something that Apple ships with it (unfortunately there is not an alternative to this for Mac OSX). To check to see if you have Xcode on your CPU, go to the Terminal (In finder navigate to `Applications/Utilities` and double click on the `Terminal`) and type the following:

`xcode-select -p`

If you see this as a response:

`/Applications/Xcode.app/Contents/Developer`

Then go ahead and enter the following command: `xcode-select --install` and then click `Install`.

If you do **NOT** see this as a response:

`/Applications/Xcode.app/Contents/Developer`

Then you do **not** have XCode and need to download it from [here](https://itunes.apple.com/us/app/xcode/id497799835?mt=12).

Once you have downloaded XCode, go back to your Terminal and enter this command:

`xcode-select --install`

Click "Install" to download and install Xcode Command Line Tools.
