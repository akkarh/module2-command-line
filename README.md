# Module 2: Introduction to the Command Line

## Overview
The **command-line** is an _interface_ to a computer---a way for you (the human) to communicate with the machine. But unlike common graphical interfaces that use <a href="https://en.wikipedia.org/wiki/WIMP_(computing)">windows, icons, menus, and pointers</a>, the command-line is _text-based_: you type commands instead of clicking on icons. The command-line lets you do everything you'd normally do by clicking with a mouse, but by typing in a manner similar to programming!

![example command-line (from Wikipedia)](img/cli-wikipedia.png)

The command-line is not as friendly or intuitive as a graphical interface--it's much harder to learn and figure out. However, it has the advantage of being both more powerful and more efficient in the hands of expert users. (It's faster to type than to move a mouse, and you can do _lots_ of "clicks" with a single command). Thus all professional developers interact with the command-line, particularly when working with large amounts of data or files.

This module will give you a brief introduction to basic tasks using the command-line: enough to get you comfortable navigating the interface and able to interpret commands.

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Contents**

- [Resources](#resources)
- [Accessing the Command-Line](#accessing-the-command-line)
- [Navigating the Command Line](#navigating-the-command-line)
  - [Changing Directories](#changing-directories)
  - [Listing Files](#listing-files)
  - [Paths](#paths)
- [File Commands](#file-commands)
  - [Learning New Commands](#learning-new-commands)
  - [Dealing With Errors](#dealing-with-errors)
- [Conclusion](#conclusion)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

## Resources
- [Learn Enough Command Line to be Dangerous](https://www.learnenough.com/command-line-tutorial#sec-basics)
- [Video series: Bash commands](https://www.youtube.com/watch?v=sqYUYHn-HKg&list=PLCAF7D691FFA25555)
- [List of Common Commands](http://www.lagmonster.org/docs/unix/intro-137.html) (also [here](http://www.math.utah.edu/lab/unix/unix-commands.html))

## Accessing the Command-Line
In order to use the command-line, you will need to open a **command shell** (a.k.a. a _command prompt_). This is a program that provides the interface to type commands into. You should have installed a command shell (hereafter "the terminal") as part of [module 1](https://github.com/info201-w17/module1-setup).

Once you open up the shell (Terminal or Git Bash), you should see something like this (red notes are mine):

![Newly opened command-line](img/cli-blank.png)

This is the textual equivalent of having opened up Finder or File Explorer and having it show you the user's "Home" folder. The text shown lets you know:

- what machine you're currently interfacing with (you can use the command-line to control different computers across a network or the Internet)
- what **directory** (folder) you are currently looking at (`~` is a shorthand for the "home directory")
- what user you are logged in as.

After that you'll see the prompt, which is where you will type in your commands.

## Navigating the Command Line
Although the command-prompt gives us the name of the folder we're in, you might like more detail about where that folder is. Time to send your first command! At the prompt, type:

```bash
pwd
```

This stands for **p**rint **w**orking **d**irectory (CLI commands are highly abbreviated to make them faster to type), and will tell the computer to print the folder you are currently "in".

- _Fun fact:_ technically this command starts a tiny program (app) that does exactly one thing: prints the working directory. When you run a command, you're actually executing a tiny program! And when you run programs (tiny or large) on the command-line, it looks like you're typing in commands.

Folders on computers are stored in a hierarchy: each folder has more folders inside it, which have more folders inside them. This produces a ["tree"](https://en.wikipedia.org/wiki/Tree_(data_structure)) structure:

![Directory Tree, from Bradnam and Korf](img/dir-tree.png)

We describe what folder we are in putting a slash `/` between each folder: thus `/Users/iguest` means "the `iguest` folder, which is inside the `Users` folder".

At the very top (or bottom, depending on your point of view) we have the **root** `/` directory--which has no name, and so is just indicated with that single slash. So `/Users/iguest` really means "the `iguest` folder, which is inside the `Users` folder, which is inside the root folder".

### Changing Directories
What if we want to change folders? In a graphical system like Finder, we would just double-click on the folder to open it. But there's no clicking on the command-line.

- This includes clicking to move the cursor to an earlier part of the command you typed. You'll need to use the left and right arrow keys to move the cursor instead. 
- **Protip:** The up and down arrow keys will let you cycle though your previous commands so you don't need to re-type them!

Since we can't click on a folder, we'll need to use another command:

```bash
cd folder_name
```

The first word is the **command**, or what we want the computer to do. In this case, we're issuing the command that means **c**hange **d**irectory.

The second word is an example of an **argument**, which is a programming term that means "more details about what to do". In this case, we're providing a _required_ argument of what folder we want to change to! (You'll of course need to replace `folder_name` with the name of the folder).

- Try changing to the `Desktop` folder, which should be inside the home folder you started in---you could see it in Finder!

- After you change folders, try printing your currently location. Can you see that it has changed?


### Listing Files
In a graphical system, once you've double-clicked on a folder Finder will show you the contents of that folder. The command-line doesn't do this automatically, instead we need another command:

```apache
ls [folder_name]
```

This command says to **l**i**s**t the folder contents. Note that I've put the _argument_ here in brackets (`[]`) to indicate that it is _optional_. If you just issue the **`ls`** command, it will list the contents of the current folder. If you include the optional argument (leaving off the brackets), you can "peek" at the contents of a folder you are not currently in.

- ___Warning___: The command-line can be not great about giving **feedback** for your actions. For example, if there are no files in the folder, then `ls` will simply show nothing, potentially looking like it "didn't work". Or when typing a **password**, the letters you type won't show (not even as `*`) as a security measure. 

    Just because you don't see any results from your command/typing, doesn't mean it didn't work! Trust in yourself, and use basic commands like `ls` and `pwd` to confirm any changes if you're unsure. Take it slow, one step at a time.


### Paths
Note that both the **`cd`** and **`ls`** commands work even for folders that are not "immediately inside" the current directory! We can refer to _any_ file or folder on the computer by specifying its **path**. A file's path is "how you get to that file": the list of folders we'd need to click through to get to the file, with each folder separated by a `/`:

```
/Users/iguest/Desktop/myfile.txt
```

This says to start at the root directory (that initial `/`), then go to `Users`, then go to `iguest`, then to `Desktop`, and finally to the `myfile.txt` file.

Because this path starts with the root directory, it is referred to as an **absolute path**. No matter what folder you currently happen to be in, that path will refer to the correct file because it always starts on its journey from the root.

Contrast that with:

```
iguest/Desktop/myfile.txt
```

Because this path doesn't have the leading slash, it just says to "go to the Desktop folder _from the current location_". Thus it is known as a **relative path**: it gives you directions to a file _relative to the current folder_. Thus the relative path `iguest/Desktop/myfile.txt` path will only refer to the correct file if we happen to be in the `/Users` folder; if we start somewhere else, who knows where we'll end up!

- You should almost **always** use relative paths, particularly when programming! That way file directions are more likely to work across computers (e.g., in case the username is different making your home folder `janesmith` instead of `iguest`; with a relative path, `Desktop/myfile.txt` will work for either person).

Finally, we can refer to the "current folder" by using a single dot **`.`**. So the command

```apache
ls .
```

means "list the contents of the current folder" (the same thing we get if we left off the argument).

If you want to go _up_ a directory, we use _two_ dots: **`..`** to refer to the _parent_ folder (that is, the one that contains this one). So the command

```apache
ls ..
```

means "list the contents of the folder that contains the current folder".

Note that **`.`** and **`..`** act just like folder names, so you can include them anywhere in paths: `../../my_folder` says to go up two folders, and then into `my_folder`.

- **Super Protip** Most command shells like Terminal and Git Bash support **tab-completion**. If you type out just the first few letters of a file or folder name and then hit the `tab` key, it will automatically fill in the rest of the name! If the name is ambiguous (e.g., you type `Do` and there is both a `Documents` and a `Downloads` folder, you can hit `tab` _twice_ to see the list of matching folders. Then add enough letters to distinguish them and tab to complete! This will make your life better.

- Also remember that you can use a tilde **`~`** as shorthand for the home directory of the current user. Just like `.` refers to "current folder", `~` refers to the user's home directory (usually  `/Users/USERNAME`). And of course, you can use the tilde as part of a path as well.


## File Commands
![Matrix meme](img/matrix-cli.jpg)

Once you're comfortable navigating folders in the command-line, you can start to use it to do all the same things you would do with Finder or File Explorer, simply by using the correct command:

| Command | Behavior	|
| ------- |  --------- |
| **`mkdir`** | **m**a**k**e a **dir**ectory |
| **`rm`** | **r**e**m**ove a file or folder |
| **`cp`** | **c**o**p**y a file from one location to another |
| **`open`** | opens a file or folder |
| **`cat`** | con**cat**enate (combine) file contents and display the results |
| **`history`** | show previous commands executed |

Be aware that many of these commands **won't print anything** when you run them. This often means that they worked; they just did so quietly. If it _doesn't_ work, you'll know because you'll see a message telling you so (and why, if you read the message). So just you didn't get any output doesn't mean you did something wrong--you can use another command (such as **`ls`**) to confirm that the files or folders changed the way you wanted!

### Learning New Commands
How can we figure out what kind of arguments these commands take? We can look it up! This information is available online, but many command shells (though not Git Bash) also include their own manual we can use to look up commands!

```apache
man mkdir
```

Will show the **man**ual for the **`mkdir`** program/command.

- Because manuals are often long, they are opened up in a command-line viewer called [`less`](https://en.wikipedia.org/wiki/Less_(Unix)). You can "scroll" up and down by using the arrow keys. Hit the `q` key to **q**uit and return to the command-prompt.

![man mkdir](img/mkdir.png)

If you look under "Synopsis" you can see a summary of all the different arguments this command understands. A few notes about reading this syntax:

- Recall that anything in brackets `[]` is optional. Arguments that are not in brackets (e.g., `directory_name`) are required. 

- **"Options"** (or "flags") for command-line programs are often marked with a leading dash **`-`** to make them distinct from file or folder names. Options may change the way a CLI program behaves---like how you might set "easy" or "hard" mode in a game. You can either write out each option individually, or combine them: **`mkdir -p -v`** and **`mkdir -pv`** are equivalent.

    - Some options may require an additional argument beyond just indicating a particular operation style. In this case, you can see that the `-m` option requires you to specify an additional `mode` parameter; see the details below for what this looks like.

- Underlined arguments are ones you choose: you don't actually type the word `directory_name`, but instead your own directory name! Contrast this with the options: if you want to use the `-p` option, you need to type `-p`.

Command-line manuals ("man pages") are often very difficult to read and understand: start by looking at just the required arguments (which are usually straightforward), and then search for and use a particular option if you're looking to change a command's behavior.

For practice, can you read the man page and figure out how to delete a folder and not just a single file? Note that you'll want to be careful, as this is a good way to [break things](http://www.pcworld.com/article/3057235/data-center-cloud/that-man-who-deleted-his-entire-company-with-a-line-of-code-it-was-a-hoax.html).

### Dealing With Errors
Note that the syntax of these commands (how you write them out) is very important. Computers aren't good at figuring out what you meant if you aren't really specific; you can't forget spaces or anything.

Try another command: **`echo`** lets you "echo" (print out) some text. Try echoing `"Hello World"` (which is the traditional first computer program):

```apache
echo "Hello world"
```

But what happens if you forget the closing quote? You keep hitting "enter" but you just get that `>` over and over again! What's going on?

- This is because you didn't close the quote, so the shell thinks you are still typing the message you want to echo! When you hit "enter" it adds a line break instead of ending the command, and the `>` marks that you're still going. If you finally close the quote, you'll see  your multi-line message printed!

**IMPORTANT TIP** If you ever get stuck in the command-line, hit **`ctrl-c`** (The `control` and `c` keys together). This almost always means "cancel", and will "stop" whatever program/command is currently running in the shell so that you can try again. Just remember: "**`ctrl-c`** to flee".

- If that doesn't work, try hitting the `esc` key, or typing `exit`, `q`, or `quit`. That should cover most cases.


## Conclusion
Don't hesitate to experiment with any of these commands, though I suggest making files to experiment with moving, deleting, editing, etc. To practice using basic command-line syntax, see [exercise-1](exercise-1).
