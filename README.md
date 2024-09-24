# Comprehensive Bash Guide

## Table of Contents
1. [Introduction](#introduction)
2. [Basic Operations](#basic-operations)
   - [File Operations](#file-operations)
   - [Text Operations](#text-operations)
   - [Directory Operations](#directory-operations)
   - [SSH, System Info & Network Operations](#ssh-system-info--network-operations)
   - [Process Monitoring Operations](#process-monitoring-operations)
3. [Basic Shell Programming](#basic-shell-programming)
   - [Variables](#variables)
   - [Arrays](#arrays)
   - [String Manipulation](#string-manipulation)
   - [Functions](#functions)
   - [Conditionals](#conditionals)
   - [Loops](#loops)
   - [Regular Expressions](#regular-expressions)
   - [Pipes](#pipes)
4. [Advanced Topics](#advanced-topics)
   - [Debugging](#debugging)
   - [Multi-threading](#multi-threading)
   - [Error Handling](#error-handling)
   - [Command Substitution](#command-substitution)
5. [Best Practices](#best-practices)
6. [Useful Tricks](#useful-tricks)
7. [Learning Path](#learning-path)
8. [Common Interview Questions](#common-interview-questions)
9. [Additional Resources](#additional-resources)

## Introduction

Bash (Bourne Again SHell) is a powerful command-line interface and scripting language used in Unix-like operating systems. This guide aims to provide a comprehensive overview of Bash, from basic operations to advanced scripting techniques.

## Basic Operations

### File Operations

| Command | Description | Example |
|---------|-------------|---------|
| `cat` | Display file contents | `cat file.txt` |
| `chmod` | Change file permissions | `chmod 755 script.sh` |
| `cp` | Copy files or directories | `cp file1.txt file2.txt` |
| `mv` | Move or rename files | `mv oldname.txt newname.txt` |
| `rm` | Remove files or directories | `rm file.txt` |
| `touch` | Create an empty file | `touch newfile.txt` |

### Text Operations

| Command | Description | Example |
|---------|-------------|---------|
| `grep` | Search for patterns in files | `grep "pattern" file.txt` |
| `sed` | Stream editor for text manipulation | `sed 's/old/new/g' file.txt` |
| `awk` | Text processing tool | `awk '{print $1}' file.txt` |
| `sort` | Sort lines of text | `sort file.txt` |
| `uniq` | Report or omit repeated lines | `uniq -c file.txt` |

### Directory Operations

| Command | Description | Example |
|---------|-------------|---------|
| `cd` | Change directory | `cd /path/to/directory` |
| `pwd` | Print working directory | `pwd` |
| `ls` | List directory contents | `ls -la` |
| `mkdir` | Create a new directory | `mkdir newdir` |
| `rmdir` | Remove an empty directory | `rmdir emptydir` |

### SSH, System Info & Network Operations

| Command | Description | Example |
|---------|-------------|---------|
| `ssh` | Secure shell client | `ssh user@hostname` |
| `scp` | Secure copy (remote file copy) | `scp file.txt user@host:/path` |
| `ping` | Send ICMP echo request | `ping google.com` |
| `wget` | Retrieve files using HTTP/HTTPS/FTP | `wget https://example.com/file` |
| `curl` | Transfer data from or to a server | `curl https://api.example.com` |

### Process Monitoring Operations

| Command | Description | Example |
|---------|-------------|---------|
| `ps` | Report process status | `ps aux` |
| `top` | Display system processes | `top` |
| `kill` | Terminate processes | `kill -9 1234` |
| `bg` | Put a process in the background | `command & bg` |
| `fg` | Bring a process to the foreground | `fg %1` |

## Basic Shell Programming

### Variables

```bash
# Assigning variables
name="John Doe"
age=30

# Using variables
echo "Name: $name, Age: $age"
```

### Arrays

```bash
# Declaring arrays
fruits=("apple" "banana" "cherry")

# Accessing array elements
echo ${fruits[0]}  # Output: apple

# Array length
echo ${#fruits[@]}  # Output: 3
```

### String Manipulation

```bash
# String length
str="Hello, World!"
echo ${#str}  # Output: 13

# Substring
echo ${str:7:5}  # Output: World

# String replacement
echo ${str/World/Bash}  # Output: Hello, Bash!
```

### Functions

```bash
# Function definition
greet() {
    echo "Hello, $1!"
}

# Function call
greet "Alice"  # Output: Hello, Alice!
```

### Conditionals

```bash
# If statement
if [ "$1" == "hello" ]; then
    echo "Hello to you too!"
elif [ "$1" == "bye" ]; then
    echo "Goodbye!"
else
    echo "I don't understand"
fi

# Case statement
case "$1" in
    start)
        echo "Starting the service"
        ;;
    stop)
        echo "Stopping the service"
        ;;
    *)
        echo "Usage: $0 {start|stop}"
        ;;
esac
```

### Loops

```bash
# For loop
for i in {1..5}; do
    echo "Iteration $i"
done

# While loop
counter=0
while [ $counter -lt 5 ]; do
    echo "Counter: $counter"
    ((counter++))
done
```

### Regular Expressions

```bash
# Matching a pattern
if [[ "example@email.com" =~ ^[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Z|a-z]{2,}$ ]]; then
    echo "Valid email"
else
    echo "Invalid email"
fi
```

### Pipes

```bash
# Using pipes to chain commands
echo "Hello, World!" | tr '[:lower:]' '[:upper:]'
```

## Advanced Topics

### Debugging

```bash
# Enable debug mode
set -x

# Your script here

# Disable debug mode
set +x
```

### Multi-threading

```bash
# Running commands in parallel
command1 & command2 & command3 &
wait
```

### Error Handling

```bash
# Exit on error
set -e

# Error handling function
handle_error() {
    echo "An error occurred on line $1"
    exit 1
}

# Set error handler
trap 'handle_error $LINENO' ERR
```

### Command Substitution

```bash
# Old syntax
current_date=`date +%Y-%m-%d`

# New syntax
current_date=$(date +%Y-%m-%d)

echo "Today's date is $current_date"
```

## Best Practices

1. Use meaningful variable and function names
2. Comment your code
3. Use proper indentation
4. Quote variables to prevent word splitting
5. Use `set -e` to exit on errors
6. Use `set -u` to exit on undefined variables
7. Use `shellcheck` to lint your scripts

## Useful Tricks

### Set an alias

Aliases allow you to create shortcuts for commonly used commands. To set an alias:

1. Open your `.bash_profile` or `.bashrc` file:
   ```bash
   nano ~/.bash_profile
   ```

2. Add your alias:
   ```bash
   alias dockerlogin='ssh www-data@adnan.local -p2222'
   ```

3. Save the file and reload it:
   ```bash
   source ~/.bash_profile
   ```

### Quick directory navigation

To quickly navigate to specific directories:

1. Open your `.bashrc` file:
   ```bash
   nano ~/.bashrc
   ```

2. Add your directory shortcut:
   ```bash
   export hotellogs="/workspace/hotel-api/storage/logs"
   ```

3. Save and reload:
   ```bash
   source ~/.bashrc
   ```

4. Now you can use:
   ```bash
   cd $hotellogs
   ```

### Re-execute the previous command

To run the last command in your history:
```bash
!!
```

This is particularly useful when you forget to use `sudo`:
```bash
sudo !!
```

### Exit traps

Make your scripts more robust by performing cleanup operations:

```bash
function finish {
  # your cleanup here. e.g. kill any forked processes
  jobs -p | xargs kill
}
trap finish EXIT
```

### Saving environment variables

To persist environment variables, append them to your `.bash_profile`:

```bash
echo export FOO=BAR >> ~/.bash_profile
```

### Accessing your scripts

Create a bin folder in your home directory for easy script access:

```bash
mkdir ~/bin
```

Add this to your `.bash_profile`:

```bash
# set PATH so it includes user's private bin if it exists
if [ -d "$HOME/bin" ] ; then
    PATH="$HOME/bin:$PATH"
fi
```

Then reload:

```bash
source ~/.bash_profile
```

Now any scripts in `~/bin` will be accessible from any directory.

## Learning Path

1. Start with basic command-line operations
2. Learn about variables and data types
3. Understand control structures (if, case, loops)
4. Practice with functions and scripts
5. Explore text processing tools (grep, sed, awk)
6. Study file and process management
7. Dive into regular expressions
8. Learn about networking and system administration tasks
9. Explore advanced topics like error handling and debugging
10. Practice by writing real-world scripts and contributing to open-source projects

## Common Interview Questions

1. What is the difference between `$*` and `$@`?
2. How do you redirect both stdout and stderr to a file?
3. Explain the purpose of the `shift` command.
4. How can you check if a file exists in a Bash script?
5. What is the difference between single and double quotes in Bash?
6. How do you create an alias in Bash?
7. Explain the concept of exit status in Bash.
8. How can you run a command in the background?
9. What is the purpose of the `set` command?
10. How do you handle command-line arguments in a Bash script?

## Additional Resources

- [Bash Manual](https://www.gnu.org/software/bash/manual/)
- [Advanced Bash-Scripting Guide](https://tldp.org/LDP/abs/html/)
- [ShellCheck](https://www.shellcheck.net/) - Online shell script analyzer
- [Bash Hackers Wiki](https://wiki.bash-hackers.org/)
- [Awesome Bash](https://github.com/awesome-lists/awesome-bash) - A curated list of Bash scripts and resources
- [Exercism Bash Track](https://exercism.io/tracks/bash) - Practice exercises for Bash

Remember, the best way to learn Bash is through practice. Start with small scripts and gradually work your way up to more complex projects. Happy scripting!
