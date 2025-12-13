# Files - editing, finding, descriptors?

## nano

nano's interface is called pager

^ stands for control
^w searches with the opened file

important files

- /etc/passwd
- /etc/shadow

## vim

vim is modal editor - it can distinguish between text and command input

vimtutor to learn vim commands
hjkl to move cusor
i to enter insert mode
in normal mode, x to delete characters
:q to quit
:q! to quit without saving
:wq to save changes

vimtutor command to shell to activate tutor

:tutor command is vim

## Find

which - which python

find - find "location" "filter"

find / -name *.py

use following to clean up output of find command 
2>/dev/null

## Locate

faster than find as it uses database

sudo updatedb

## File Descriptors and Redirections

file handle of windows is file descriptor in linux

file descriptor is the system's way of keeping track of active I/O connections

By default, the first three file descriptors in Linux are:

    Data Stream for Input
        STDIN – 0
    Data Stream for Output
        STDOUT – 1
    Data Stream for Output that relates to an error occurring.
        STDERR – 2

> to redirect output to a file

it overrides if file already exists

>> appends to file

| to pass STDOUT between two commands

## wc

count files or words etc.

to count files returned by list. beware output from previous command may contain some more e.g. total, listing etc. either at the beginnin or at the end.

wc -l