# Text Files and Text Editors
- Text Files: Configuration files and shell scripts.
- Text Editor: Lets you edit documents that are stored in plain-text format (scripts).

## File Types:
- Human language files
- Programming language files
- Formatted text files
- Program and system configuration files
- Program log files

## Popular Text Editors
- vi:
    - Very small and installed by default
    - A little more difficult to use
- emacs:
    - Big editor with a lot more features
    - Less likely to be installed by default on lightweight distributions
    - Also has a GUI version
- pico: 
    - Modeled after emacs
    - More lightweight and better suited for lightweight distributions
    - Often installed by default
- nano:
    - clone of pico but has extra features
    - much more lightweight than emacs
    - commonly found in small and lightweight distributions

## GUI-based Editors
- KWrite
- Gedit

---

# Shell Script
- A shell script is a text file containing a series of commands written for the Linux shell (e.g., bash, zsh, or sh).
- Shell script in Linux is an easy to use time-saving solution for automating repetitive or complex set of tasks.

---

# Commands and Arguments
- Most commands entered into a shell prompt are external commands.
- The **ampersand (&)** at the end of a command lets users run many programs simultaneously.

- A **command** in Linux is an instruction given to the shell to perform a specific action.
    - For example: The echo command is used to print a line of text on the screen.
```bash
echo
```
- An **argument** acts as an input to the command.
    - For example: To print a hello message type echo hello command.
```bash
echo "Hello"
```
- Many of the commands needs arguments to work, though it is not mandatory. There are several commands that work without arguments too.
    - For example: Type in the command called uptime, this is used to print information about how long a system has been running for since the last reboot along with the other information.
```bash
uptime
```
- A command can also have **options** to modify its behavior in some predetermined way.
- The option, also sometimes referred to as a **switch** or a **flag**, is usually start with a - (single character) or -- (full word).
    - For example: To print a same word hello but without a trailing line, use echo command with -n flag.
```bash
echo -n "Hello"
```

## Command Types
- Commands in Linux can be generally categorized into two types:
    1. Internal or Built-in Commands:
    - This are part of the shell itself and come bundled with it.
    - There are total of 30 such commands.
    - For example: echo, cd, pwd, set, etc.
    2. External Commands:
    - This are binary programs or scripts which are usually located in distinct files in the system.
    - They either come pre-installed with the distributions package manager or can be created or installed by the user.
    - For Example: mv, date, uptime, cp, etc.
- To determine whether the command is internal or external, use the <code>type</code> command.
```bash
type echo                        # command
echo is a shell build-in         # output

type mv                          # command
mv is hashed (/bin/mv)           # output
```

---

# Variables
- In shell scripting, variables allow the user to store and use the data dynamically in the script.
- They make scripts more flexible and reusable by allowing dynamic data to be used instead of hardcoding values.

## Key Points
- A variable is a value that can vary or change.
- A variable always has a <code>$</code> sign before it's name (not while defining).
- A variable name only contain alphanumeric or underscores.
- A variable is case sensitive as well.

## Defining Variables
- No spaces are allowed around the <code>=</code> when assigning values and do not use $ sign before the variable name.
```bash
mission_name="lunar-mission"
```

## Accessing Variables
- Use a <code>$</code> prefix to reference a variable's value.
```bash
echo $mission_name
```
- We can also use variables to store the result of another command and print it.
```bash
rocket_status=$(rocket-status $mission_name)
echo "Status of launch: $rocket_status"
```

## Types of Variables
1. **Local Variables**
- Defined and used within the script or a function.
```bash
my_var="Hello"
echo $my_var
```
2. **Environment Variables**
- System-wide variables available to all processes.
```bash
export NAME="Rohit"
echo $NAME
```
3. **Positional Variables**
- Special variables representing arguments passed as input to the script.
```bash
echo "Script Name: $0"
echo "First Argument: $1"
```
4. **Special Variables**
- Variables with predefined meanings.
    - <code>$?</code>: Exit status of the last command.
    - <code>$$</code>: Process ID (PID) of the current shell.
    - <code>$#</code>: Number of arguments passed to the script.
    - <code>$@</code>: All arguments as separate words.
    - <code>$*</code>: All arguments as a single string.

---

# Read Inputs
- The <code>read</code> command in shell scripting is used to take input from the user during script execution.
- It pauses the script until the user provides input and then assigns the entered value to a variable.

## Syntax
```bash
read -p "Enter mission name:" mission_name
```
- <code>mission_name</code>: The variable where the input will be stored.
- Options:
    - <code>-p</code>: Display a prompt message.
    - <code>-s</code>: Silent input (useful for passwords).
    - <code>-t</code>: Timeout for input.
    - <code>-n</code>: Read a specific number of characters.

---

# Conditional Logic
- Conditional logic in shell scripting is used to **execute commands based on specific conditions**. This allows scripts to make decisions, enabling dynamic and flexible execution paths.

## Types of Conditional Statements
1. <code>if</code> Statement
2. <code>if-else</code> Statement
3. <code>if-elif-else</code> Statement

---

# Loops
- The loop in shell scripting is used to iterate over a sequence of items, performing a set of commands for each item.

## Types of loops
1. <code>for</code> Loop: Same command multiple times.
2. <code>while</code> Loop: Executes for as long as its condition is true
3. <code>Until</code> Loop: Similar to the while loop but continues to execute as long as its condition is false or until the condition becomes true


- <code>seq</code>: 
    - Generates a list of numbers starting from its first argument and continuing to its last one
    - Example: <code>seq 1 10</code>, <code>seq 1 2 10</code>

---

# Case Statement
- The <code>case</code> statement in shell scripting is used to simplify the evaluation of multiple conditions.
- It is a more concise and readable alternative to <code>if-elif-else</code> structures when need to compare a single variable or expression against multiple patterns.

---

# Functions
- Function in a shell script is a piece of or block of reusable code that perform specific task.
- They help to organize code, improve readability, and avoid repetition by encapsulating logic into a single callable unit.
- When a shell script runs it runs line-by-line. So your Function must always be defined first before calling it, if not then it will give error.
- The return statement within a function call helps in specifying the exit code for that function. It is just like the exit code for the entire script but in this case it wont exit the script but the function.

## Syntax
- There are two common ways to define a function in shell scripting:
1. Using the <code>function</code> Keyword:
```bash
function function_name() {
    # Commands
}
```
2. Without the function Keyword:
```bash
function_name() {
    # Commands
}
```

---

# Exit Codes
 - In shell scripting, exit codes (also known as **return codes** or **exit status**) indicate the success or failure of a command or script.

## Exit Code Conventions
1. **Success (0)**: An exit code of 0 means the command or script executed successfully without errors.
2. **Failure (Non-Zero)**: Any non-zero exit code indicates an error or a specific failure condition. Common non-zero codes are typically integers from 1 to 255.
