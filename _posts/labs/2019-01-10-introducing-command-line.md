---
layout: labs
title:  "The Command Line"
date:   2019-01-10 06:00:00 -0710
week: 1
number: 2
tags: lab
---

### Materials
* laptop
* Max OSX Terminal **or** [iTerm2](https://www.iterm2.com/)

![]({{site.url}}/assets/iterm_vs_macosx_terminal.jpg)

Navigate to the Command Line on Mac OSX (Applications > Utilities > Terminal).

You should see something that looks like the window with a white background at the top of this page. That is the **Terminal**, a name for a command line interface (often abbreviated as **CLI**) that is already installed on your computer. Though other aspects of computers have changed drastically over the last fifty years, this has not. In other words, you can see back in time at this level of your computer. Read more about the history of the command line [here](https://en.wikipedia.org/wiki/Command-line_interface).

In the above photo you will notice a semi-transparent black window that looks fairly similar to the **Terminal**. This is [iTerm2](https://www.iterm2.com/) and I prefer it to the Mac OSX **Terminal**. I do not really care which you use (it's a matter of personal preference), and not particularly interesting to talk about right now, just be aware that the same commands work across all **CLI**s.

1. Open a new terminal window with **COMMAND-N**. You should see something like `HOSTNAME:~ USERNAME$` followed by a rectangle. The rectangle is your cursor and demarcates where you can enter text commands for the **Terminal** to execute.

2. Unix commands, and really anything used in the command line, should be shipped with some sort of `manual`. Typically this is accessed by typing `man NAMEOFCOMMAND` in the **Terminal** and hitting enter. Let's start by checking the manual for the next command we will use, `ls`. Type `man ls` and hit enter. You should see something that looks like this:

    ![]({{site.url}}/assets/man_example.png)

    This is the manual for `ls`, which opens automatically in a text editor called `Vi` (also known as `Vim`, short for `Vi Improved`). `Vim` has a radically different approach to how a text editor works than Microsoft Word or Apple Pages, which you can read about in detail [here](http://www.vim.org/).

    There are two modes in `Vim`: `Normal` and `Insert`, and toggling between the two modes exposes different features of the application. `Normal` is typically reserved for navigating through a file or reading. To navigate the file you can use the `j` (down) and `k` (up) keys. In order to quit a file you simply type `q`.

    We will discuss how to use `Insert` mode, and other commands, in the future. Right now its more important to take some time to read through the `manual` for `ls`. It is considered standard practice for developers to include a `man` file for virtually everything that you use in the terminal, making `man` a very important command to commit to memory.

    Note: google `vim vs emacs` to see an example of how passionate people get about their tools (these arguments are frequently referred to as "religious").

3. Type `ls` and then hit **Enter**. `ls` lists the contents of the directory you are currently in. When you open a new **Terminal** window you will default to your user's home directory. We can confirm this by running the command `pwd` (`print working directory`), which will return `/Users/USERNAME`.

4. To move to a different directory, type `cd` at the command line and then the name of the directory. **Terminal** has autocomplete, so type the first two characters of the directory, for example, and then hit the `TAB` key, which is less work (yay!). On my machine I can move to a directory named `werk` by running the following command: `cd werk/` where `cd` means `change directory` to the directory named `werk`.

5. You can move around on the command line with arrow keys, but there are also shortcuts like **CTL-A** to go to the beginning of the line and **CTL-E** to go to the end of the line. If you make a bunch of mistakes and just want to start over you can issue a `KeyboardInterrupt` by hitting **CTL-C**, which will result in a new line.

6. Check to make sure you are in your home directory (`pwd`) and then make a new directory by typing `mkdir NEWDIRECTORY`, where `NEWDIRECTORY` is the name of your folder (name it whatever you want).

7. In the next sequence, we will move into our `NEWDIRECTORY` and create a text file named `test.txt`:


    1. `cd NEWDIRECTORY`
    2. `pwd`
    3. `touch test.txt`
    4. `ls`


8. Next lets write something in our text file using a text editor called [Nano](https://www.nano-editor.org/) (which is already installed on your machine, just like `Vim`):


    1. `nano test.txt`
    2. `this is my text`

    Save your changes with **Ctl-O**, hit **Enter** to confirm the file name, then **Ctl-X** to exit.

9. In the following sequence we will use the  [Unix](https://en.wikipedia.org/wiki/Unix) command `grep`, which searches plain-text data sets for lines matching a regular expression (definition sourced from [here](https://en.wikipedia.org/wiki/Grep)):

    1. Click [here](https://www.gutenberg.org/cache/epub/19033/pg19033.txt) to go to the `.txt` version of [The Project Gutenberg](https://www.gutenberg.org/) EBook of Alice in Wonderland, by Lewis Carroll.
    2. Click anywhere on that page, **Command-A** to select all, **Command-C** to copy to clipboard.
    3. Back in your terminal, make a new text file called `alice.txt`: `touch alice.txt`
    4. Open the file with Nano: `sudo nano alice.txt` (don't forget about autocomplete with the `TAB` key!), you should enter your password and then hit **Enter**
    5. Click anywhere in the window, **Command-V** to paste the contents of the `.txt` version of Alice in Wonderland into the file, **Ctl-O** to save, Enter to confirm file name, **Ctl-X** to Exit.
    6. Now you can search all of Alice in Wonderland for every line that contains some `regular expression` (which you specify between quotes), which could be a word, or a string of words, but is by default case sensitive.

        *Example 1:* `grep 'home' alice.txt` results in:

        "Why, Mary Ann, what _are_ you doing out here? Run home this moment and
        this creature, when I get it home?" when it grunted again so violently

        *Example 2:* the words 'hello', 'sorry', and 'god' do not occur in the entire text of Alice in Wonderland. In other words, `grep 'god' alice.txt` returns nothing.

        Note: in the future our goal would be to eliminate the steps that required the use of mouse and a web browser.

10. Let's go ahead and delete the example files we made. `rm` removes files. When you need to delete a file, run `rm NAMEOFFILE`. If you try to use `rm` on a directory, like the one you made for the `test.txt` and `alice.txt` files, the **Terminal** will stop you (as a safety measure) because `Unix` thinks that directories should only be removed when they are empty. So, there are two approaches to getting around this kind of an issue:

    1. manually `rm` every file in the directory (this sucks because its repetitive, error-prone, and time-consuming) and then use `rmdir NAMEOFDIRECTORY` to remove the empty directory.

    2. **ALTERNATELY**, the cooler (lazier) way to do this is to use `rm -r NAMEOFDIRECTORY` to recursively remove all contents of the directory.

    Note: Sometimes, in order to do certain things in the terminal, you may need to prepend a command with `sudo`. "Sandwich," from the web comic series [XKCD](https://xkcd.com/), sums `sudo` up nicely:

    ![]({{site.url}}/assets/xkcd_sandwich.jpg)

    `sudo` means `super user do` and forces the computer to let you do something. The standard practice is to avoid using `sudo` unless you know you have to, which often takes some guessing the first time.

    *For example:* I normally try a command without `sudo` first and, if I get a permissions error as a response, then run the following on a new line: `sudo !!`.

    *Note:* The command `!!`, which is pronounced `bang bang`, is a shortcut to repeat the previous command entered into the terminal. In other words, this command prepends `sudo` to whatever you ran in the terminal previously.


### ls -l

The Unix command `ls` can do a lot more than just list the contents of a directory. If you run `ls -l` you can see a full list of the following information (sourced from [here](http://www.computerhope.com/unix/uls.htm)):

* total files in the directory and subdirectories
* the names of the files in the current directory
* their permissions
* the number of subdirectories in directories listed
* the size of the file
* and the date of last modification

Go ahead and try running this command in a few different directories. Try `home`, `Applications`, and a new directory, made by you (`mkdir`), on the `Desktop` expressly for this purpose.

### Renaming = Moving

If you need to rename a file with Unix, use the `mv` command. `mv` renames/moves the **SOURCE** to the **DESTINATION**. For example, in the next sequence we will make a new file on the **Desktop**, rename it, and then move it to our **home** directory. Follow along in the **Terminal**:

1. `cd Desktop/`
2. `touch test.txt`
3. `mv test.txt mv_demo.txt`
4. `mv mv_demo.txt ../mv_is_fun.txt` *Note:* `..` is short for `up one directory level`
5. `cd ~` *Note:* `~` is a shortcut for your `home` directory (so many shortcuts!)
6. `ls` *Note:* confirms that `mv_is_fun.txt` has been moved/renamed

### Copying Files and Directories

The `cp` command allows one to copy files/directories from a **SOURCE** to a **DESTINATION**. In other words, standard usage tends to look like this: `cp ORIGINALFILE NEWFILE`. If you need to copy a directory, though, and want to copy the entire directory structure inside of it, you can tell `cp` to recursively copy the directory and all of its contents`cp -R OLDDIRECTORY NEWDIRECTORY`.

When you need to copy files over a network you can use `scp`, which is virtually the same as `cp` but copies files or folders over a secure, encrypted network (preventing the possible interception of sensitive data via what is referred to as a [Man-in-the-middle attack](https://en.wikipedia.org/wiki/Man-in-the-middle_attack)). You will use this command extensively when working with the **Raspberry Pi Zero W**.


*Note:* Though you will begin to memorize some of these commands through frequent use, it is normal to bookmark an online [cheat sheet](http://cli.learncodethehardway.org/bash_cheat_sheet.pdf) for reference.
