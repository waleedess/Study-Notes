###### History 

- Bourne Shell - `SH` => Bourne Again Shell - `BASH`
- Works almost everywhere (Linux, Mac, Windows and IoTs)
- Meant to be for System adminstration and automation
- Programming wise:
	- Bash usually does not display the line number with error, and so this makes it difficult to find errors
	- Bash is a bit slower in terms of performance compared to other languages
	- Does not have advanced features
- Note that bash scripts will often run smoothly under shells like “zsh”, and etc.
---
###### Unix Terminology

1. Shell
	- Allows user to text-based communicate with OS 
	- Bash is the default for Linux and macOS
2. CLI
	- An interface where users enter commands to the shell 
	- Accessed via a terminal or console application
3. Command
	- Instruction given to the operating system to perform a certain action
4. Script 
	- An automated set of commands stored in a file `.sh` then interpreted and executed by the shell
5. Pipelining
	- The ability to use the output of one command as the input of other
		`ls | grep `
6. Environment Variables
	- Environment variables allow the shell and the programs it runs to store and access certain values
		- `PATH` environment variable specifies which directories the shell will check for commands. These environment variables can be set system-wide or for a specific user
7. STDIN/OUT/ERR
	- These terms refer to standard channels for the input and output of the shell and programs
		- `STDIN` usually represents input from the keyboard
		- `STDOUT` represents correct output
		- `STDERR` represents erroneous output
8. Exec. Permissions
	- These permissions can be changed with the `chmod` command
---
###### Bash for Win

**Installing Bash got many methods, mentioned below:**
1. Windows Subsystem for Linux - **WSL**
	- Steps:
		1. `wsl --install` from Adminstrator PowerShell
	- Setup a virtual Ubuntu
2. **CygWIN**
	- Translates POSIX APIs to Windows APIs
---
# BASH

### Variables

- Data containers for later use
  
**Normal Variable**

- Global by default

1. Definition:
	- Global (Default) `<varname> = <value>`
	- Local (Inside a function only) `local <varname> = <value>`
	- Super Global (Environmental) `export <varname> = <value>`
2. Recall:
	`$<varname>` 
	- $PATH -> ==An Enviromental Variable== displays the list of directories where your operating system searches for executable programs

- **Environmental** Variable
	- Environmental Variables are ==Super Global== , as they are Global and also inherited by child processes
	- To create or modify an environmental variable, use `export` command:

	![[Pasted image 20260815062459.png]]

###### Reading Input into a variable

`read <varname>`

---
# IF & Loop Structures

#### If-elseif-else

`if ["$<varname>" -<operator> "const"]`
`then`
	`echo "xyz"`
`elif ["$<varname>" -<operator> "const"]`
`then`
	`echo "zyx"`
`else`
	`echo "xxx"`
`fi` => Closes the `if` statement block

- Bash operators and their Values 
	![[Pasted image 20260816020534.png]]


#### For Loops

`for <varname> in <val1> <val2> <val3>`
`do` => To start commanding for each iteration
    `<commands using "$<varname>">`
`done`=> To end each iteration command

- `val1, 2, 3` Can be other things rather than integers only like:
	1. Integers
	2. Strings

	3. * with files 
	   `for filesystem_variable in /home/letsdefend/ex*`
		`do`
		    `echo "Example File: $filesystem_variable"`
		`done`
		- expands to every file/folder in `/home/letsdefend/` starting with "ex". The loop prints "Example File: PATH" for each match

	4. Command substitution
	   `for output_variable in $(cut -d: -f1 /etc/passwd)`
		`do`
		    `echo "User in Passwd File: $output_variable"`
		`done`
		- `$(cut -d: -f1 /etc/passwd)` runs the `cut` command first, which reads `/etc/passwd` then using `:` as the delimiter (`-d:`) splits **every line** by `:` into fields, then (`-f1`) keeps and extracts only field 1 (the first chunk before the first `:`)  that's the username field. The `for` loop then iterates over each username printed by that command, echoing "User in Passwd File: NAME" for each one

#### While Loops

`our_variable=1`
`while [ $our_variable -le 5 ]`
`do`
    `echo "Value: $our_variable"`
    `((our_variable++))`
`done`

- While loop runs certain commands as long as a certain condition is true

#### Case Structure 

`echo "Please input value"`
`read our_variable`

`case $our_variable in`
    `1 )`
        `echo "our_variable value is Equal To 1"`
        `;;` => To end the 1st situation commands
    `2 )`
        `echo "our_variable value is Equal To 2"`
        `;;` => To end the 2nd situation commands
    `* )` => ~ **else**
        `echo "our_variable value is NOT Equal To 1 or 2"`
        `;;` => To end the ~else situation commands
`esac` => To end the case structure

#### Until Loop


#### Select Loop

---
# Functions

###### Function Definition

`functionname() {`
    `Commands`
`}`

###### Function Call

 `functionname`


--- 
# Notes 

1. `echo "zyx $var zyx "` or `echo "zyx" "$var"` => Both works for mentioning a variable in this command
2. `sleep 10` => Sleeps 10 secs
3. `while [ -f /folde/file.ext ]` => Checks file existence
	- That file test operator can work **Standalone**, In Scripts with **&&** or **||**, **Until Loop**, **While Loop** and **If Statement**
	- Other related operators
		`-d` -> for dir
		`-e` -> for paths, file/dir/symlink or else
		`-x` -> for **executability** 
		`-r` / `-w` -> for read/**write**
		`-s` -> file exists and is **not** **empty**
4. While, For doesnot have whole block closer like if -> fi, case -> esac
   -> But, they got do...done for each iteration
   -> But, IF got then before each situation command except for **else**
5. `bash -n` in the terminal will check the syntax of bash script
6. Prompts: `read -p 'Enter your name: ; ' name`=> With the exact syntax 
	- can be used instead of 
	   `echo "Enter your name"`
	   `read varinput`
   