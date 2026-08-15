###### History 

- Bourne Shell - `SH` => Bourne Again Shell - `BASH`
- Works almost everywhere (Linux, Mac, Windows and IoTs)
- Meant to be for System adminstration and automation
- Programming wise:
	- Bash usually does not display the line number with error, and so this makes it difficult to find errors
	- Bash is a bit slower in terms of performance compared to other languages
	- Does not have advanced features
---
###### Unix Terminology

1. Shell
	- Allows user to text-based communicate with OS 
	- Bash is the default for Linux and macOS
2. CLI
	- An interface where users enter commands to the chell 
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
# Getting Started