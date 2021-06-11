# Introducing: The Command Line!

* the **Command Line** is a window into which you can talk directly to your computer
  * aka *console* or *terminal* or *command prompt* or *shell*
* when you type into the terminal, you are issuing **commands** to the computer
* a *CLI* (Command Line Interface) is different from the *GUI* (Graphical User Interface) you are used to
  * a CLI is more primitive **and more powerful** than a GUI

---

# Directories

* a *directory* is a location on your hard disk
  * also called a *folder*
* directories can contain *files*
* directories can also contain other directories (called *subdirectories*)

---

# Where am I?

* Inside the Terminal, you are always "inside" a directory.
* It is very easy to get lost in a maze of directories.
* To find out which directory you are in, type <kbd>p</kbd><kbd>w</kbd><kbd>d</kbd> and then hit <kbd>Return</kbd>
  * This stands for "print working directory" (not "password").
  * Most of the time you can also look at the prompt to see what the current directory is.

---

# The Path

The command line is very dependant on the file path. Here are a few key directional commands in the command line:

* `.` means "this directory I'm currently inside of"
* `..` means "the directory containing the directory I'm currently inside of"
* `/another-directory` means "look for a directory named `another-directory` inside of the current directory
  * Paths can also be chained to go through multiple subdirectories
  * e.g. `/another-directory/further-down`
  * when `cd`ing into subdirectories hitting <kbd>Tab</kbd> will autofill the directory name after typing at least one character

---

# Basic Commands (Unix)

* `pwd` ("print working dir") -- shows the name of the current directory
* `ls` ("list") -- shows the contents of the current directory
* `mkdir` ("make dir") -- creates a new subdirectory inside the current directory
* `cd` ("change dir") -- move into a different directory

> These apply to Mac / Unix / Linux / bash

---

# Basic Commands (DOS)

* `cd` ("change dir") -- With no directory, it lists the current directory. Otherwise, it changes to the specified directory
* `dir` ("directory") -- shows the contents of the current directory
* `mkdir` ("make dir") -- creates a new subdirectory inside the current directory

> These apply to Windows / DOS / PowerShell

---

# Running Programs

You can also run programs through the command line. To run a program through the command line, you type a preset keyword for the type of program you want to run, and then the name of the file you want to run.

* Source code is the essence of a program
* Source files are text files that contain source code
* To run a JS file called *hello.js* `cd` into the directory where the file lives, then type `node hello.js`. This will execute the JS in the source file.

> In the cookie recipe metaphor, the *source file* is the **recipe** and *running the program* is **cooking**.

---

# VS Code

* VS Code is a code editor that allows us to more easily write and edit programs
* To open VSCode from the command line you can issue the command `code .`
  * `code` is the keyword to open VSCode
  * `.` means "from this directory I'm currently in"
  * You should always `cd` into the directory you want to be working in, then open VSCode from the command line
  * Don't open VSCode through the GUI!

---

# JS in the CLI

You can also write JavaScript directly in th command line. This is a great way for testing out code snippets, and operations!

* To write JavaScript you need to be in a "Node" environment
* You can check that Node is installed with the command `node --version`
  * If Node **isn't** installed you'll get the error: `node is not recognized as an internal or external command`
  * typing `node` by itself and hitting <kbd>Enter</kbd> will open a Node environment inside your terminal
  * to exit a Node environment hit <kbd>Ctrl</kbd> and <kbd>C</kbd> twice
