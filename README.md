# EFunge

EFunge is a modified version of Befunge 93 that is meant to be more practical
and easy to use version for enterprise users.

**Note:** This project is for fun and is mildly to severely satirical

## Background

Befunge 93 is an esoteric programming language where programs are 2 dimensional spaces of bytes.
They are stored ascii text files or equivalently utf-8 files which contain no larger than 1-byte values.
To execute the file a cursor moves through the space interpretting each byte as a command,
and then based on the command updating its position, direction, stack, and the space itself.
To learn more about Befunge 93 see [this page](https://esolangs.org/wiki/Befunge) on esolangs.org.

## EFunge design

### Issues with Befunge 93

The main issues with using Befunge 93 for practical programming tasks are that it
 * does not standard process facilities like
   * command-line argument access
   * creating arbitrary file descriptors / streams
   * reading from and writing to arbitrary streams
   * sub-processing
 * it allows self modification of code, which makes code review difficult
 * it uses signed numbers for its stack cells (see [Signed Numbers Considered Harmful](im_not_actually_serious_this_isnt_a_thing.com))

### Issues with Funge 98

Funge 98 expands Befunge 93 significantly and adds features that make it a very capable programming language.
However, it does so at the cost of a significantly more complex language and compiler.
The fingerprinting system does achieve the desired goal, but doesn't create readable code and easy extensibility.

### EFunge design philosophy

TODO

### EFunge changes from Funge 98

TODO
* Removal of the "p" put command
* Addition of the "c" call command

## Running EFunge interpreter

Currently EFunge can only be run in an interactive mode from the command line.

When it is run you will be prompted to name a file in the programs directory.
This name should not include the .b93 file extension.

Once this is done you will be prompted for commands.

### Commands

The format for each command is the value in the quoted string after the commands name.
When prompted for commands type a value matching a single command format and then hit enter.

* Step "s" - Executes one opcode
* Run "r" - Runs the program until a breakpoint is hit or the program terminates
* Breakpoint "b \<x\> \<y\>" - Places a breakpoint at the specified location
* Input "i .." - Sends the rest of your input into the input buffer of the interpreter byte for byte
* Position "p" - Prints the current (x,y) coordinates of the kernel with the top left corner as (0,0)
* Line "l" - Prints the current line of the program
* Debug "d" - Prints the Rust debug formatted value of the entire interpreter
* Quite "q" - Terminates the EFunge interactive debugger / interpreter
