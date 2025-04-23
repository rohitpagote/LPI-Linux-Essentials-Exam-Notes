# Basic Shell
- The Linux Shell is a program that allows text-based interaction between the user and the OS. 

## Check current shell
- You can find out which shell you are using by running:
```bash
    echo $SHELL
```

## Switch between shell
- To switch to a different shell, type its name in the terminal (if installed). For example:
```bash
    zsh  # Switch to zsh
    bash # Switch to bash
```
- To make a shell your default, you can use the chsh command:
```bash
chsh -s /bin/sh rohit      # change shell from bash to sh for user rohit
```

---

# Command Line Syntax
- A computer's operation, no matter which OS it's running, can be loosely described in just 3 steps:
    1. Computer waits for user input
    2. User selects a command and enters it using a keyboard or a mouse
    3. Computer executes the command
- In Linux, the shell displays a prompt.
    - This prompt usually consists of a user and the host (computer/machine name), the current directory, and a final character ($).

## Command and Arguments
- A command in Linux is an instruction given to the shell to perform a specific action.
- For example: The echo command is used to print a line of text on the screen.
```bash
    echo
```

- An argument acts as an input to the command.
- For example: To print a hello message type echo hello command.
```bash
    echo hello
```

- Many of the commands needs arguments to work, though it is not mandatory. There are several commands that work without arguments too.
- For example: Type in the command called uptime, this is used to print information about how long a system has been running for since the last reboot along with the other information.
```bash
    uptime
```

- A command can also have options to modify its behavior in some predetermined way.
- The option, also sometimes referred to as a switch or a flag, is usually start with a - (single character) or -- (full word).
- For example: To print a same word hello but without a trailing line, use echo command with -n flag.
```bash
    echo -n hello
```

## Command Types
- Commands in Linux can be generally categorized into two types:
    1. Internal or Build-in Commands:
        - This are part of the shell itself and come bundled with it.
        - There are total of 30 such commands.
        - For example: echo, cd, pwd, set, etc.
    2. External Commands:
        - This are binary programs or scripts which are usually located in distinct files in the system.
        - They either come pre-installed with the distributions package manager or can be created or installed by the user.
        - For Example: mv, date, uptime, cp, etc.
- To determine whether the command is internal or external, use the type command.
```bash
        type echo                        # command
        echo is a shell build-in         # output

        type mv                          # command
        mv is hashed (/bin/mv)           # output
```

---

# What is Shell Script?
- A Shell Script is a text file containing a series of commands written for the Linux Shell (e.g., bash, zsh, or sh).
- Shell script in Linux is an easy to use time-saving solution for automating repetitive or complex set of tasks.

---

# Variables
- In shell scripting, variables allow the user to store and use the data dynamically in the script.
- Variables make the script more flexible and reusable by allowing dynamic data to be used instead of hardcoding values.

## Key Points
- A variable is a value that can vary or change.
- A variable always has a $ sign before it's name (not while defining).
- A variable name only contain alphanumeric or underscores
- A variable is case sensitive as well.
- **printenv/env** displays all the environmental variables (variables in ALL CAPS)

## Defining Variables
- No spaces are allowed around the = when assigning values and do not use $ sign before the variable name.
```bash
    age=40
```

## Accessing Variables
- Use a $ prefix to reference a variable's value.
```bash
    echo $age
```

## Naming rules
- Variable names must start with a letter
- A name must not contain embedded spaces (Underscores are used instead)
- Punctuation marks are not allowed

---

# Quoting 
## Shell Meta Characters
- In Linux shells, meta characters are special characters that have specific meanings and are used for various purposes like command execution, redirection, and pattern matching.
- These characters, if not properly handled (e.g., escaped or quoted), can alter the shell's interpretation of commands, leading to unexpected behavior. 

## Breakdown
1. Command Execution and Grouping:
    - Semicolon (;):
        - Separates multiple commands on a single line, executing them sequentially. 
    - Ampersand (&):
        - Executes a command in the background, allowing the shell to continue with other commands. 
    - Pipe (|):
        - Redirects the output of one command as the input to another command, enabling command chaining. 
    - Left and Right Parentheses ( ( ) ):
        - Used for grouping commands together, allowing for more complex command sequences. 
2. Redirection and Input/Output:
    - Greater-than sign (>): 
        - Redirects the output of a command to a file, overwriting its contents.
    - Less-than sign (<): 
        - Redirects the input of a command from a file.
    - Double greater-than sign (>>): 
        - Appends the output of a command to the end of a file. 
3. Pattern Matching and Filename Wildcards:
    - Asterisk ():*: 
        - Matches any sequence of characters, used in filename pattern matching. 
    - Question mark (?): 
        - Matches any single character, also used in filename pattern matching. 
    - Brackets (): 
        - Used to specify a set of characters to match. 
    - Backslash (\\): 
        - Used to escape or quote a metacharacter, effectively turning it into a literal character. 
4. Other Metacharacters:
    - Space, Tab, and Newline: 
        - These characters are used to separate words and commands in the shell. 
    - Dollar sign ($): 
        - Used to expand variables and access their values. 
    - Backtick (`): 
        - Used for command substitution, allowing the output of a command to be used as part of another command. 
    - Single and Double Quotes (' ' and " "): 
        - Used for quoting, preventing the shell from interpreting special characters within the quoted text. 

## Quoting
- It is the act of protecting shell meta characters from being treated specially by the shell.
- Prevents the shell from acting on and expanding the meta-characters.
- Done in double quotes ( “ “ ), single quotes ( ‘ ‘ ), or backslash ( \ ).
- Backlashes can be used to quote or turn off a special character’s ability.

---

# Man and Info Pages
## Manual (Man) Pages
- Most of the commands internal or external come bundled with man pages which provides information about the command in detail (with examples, usecases and with command options).
```bash
    man <command>
    man -k <search term>
```

## Commands
### Long hand
- More human-readable
- Lets users remember what the command is doing
- Example: --all

### Short hand
- Quicker to type out
- Allows for multiple options to be chained together and is quicker to type out
- Example: -a

## Info Pages
- More detailed than man pages; divided into different nodes or pages and works like a web browser.
```bash
    info <command>
```
- p for previous
- n for next
- q for exit
