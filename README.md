# BigShell

BigShell is a custom Unix-like shell implementation degigned to handle both synchronous and asynchronous commands, provide robust signal handling, and manage foreground and background processes efficiently. It serves as a lightweight, educational shell implementation for learning core Unix concepts and process management. This is my portfolio project for Operating Systems I at Oregon State University.

## Features
- **Command Execution**: Executes built-in and external commands with support for arguments and I/O redirection.
- **Job Control**: Manages foreground and background jobs with signal handling for stopping, continuing, and terminating processes.
- **Signal Handling**: Custom handlers for common signals like ```SIGINT```, ```SIGTSTP```, and ```SIGTTOU```.
- **Special Parameters**:
   - ```$?```: Reflects the exit status of the last foregound command.
   - ```$!```: Displays the PID of the most recently executed background command.
- **Pipelines**: Supports executing commands connected via pipes.

## Code Structure
- ```bigshell.c```: Entry point for BigShell. Initializes signal handlers and starts the main event loop.
- ```builtins.c```: Implements pseudo-redirection for built-in shell commands, allowing them to write to standard streams without altering the shell's actual open files by using a virtual layer on top of the existing file descriptor system.
- ```exit.c```: Defines the bigshell_exit function, which cleans up and exits the shell by sending a SIGHUP signal to all running jobs to terminate them.
- ```expand.c```: Handles variable and other expansions required by the shell, providing the necessary functionality as defined in the expand.h interface. It includes various standard and custom headers to support its operations.
- ```params.c```: Defines and initializes a params struct that holds two special parameters for the shell: status (representing the last command's exit status) and bg_pid (representing the last background process ID).
- ```runner.c```: Manages command execution, including pipelines and redirection.
- ```signal.c```: Contains custom signal handlers and functions for signal management.
- ```jobs.c```: Handles job control features, including foreground and background process management.
- ```vars.c```: Manages shell variables, defining a linked list structure to store variables with their names, values, and export status, and includes functions to manipulate and validate these variables.
- ```parser.c```: Parses user input into commands and arguments.
- ```wait.c```: Provides functions to manage and wait for foreground process groups in a shell environment, including handling job control and signaling processes to continue execution.