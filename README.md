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
- ```runner.c```: Manages command execution, including pipelines and redirection.
- ```signal.c```: Contains custom signal handlers and functions for signal management.
- ```jobs.c```: Handles job control features, including foreground and background process management.
- ```parser.c```: Parses user input into commands and arguments.