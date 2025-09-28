# Functions
1. strdup 
2. exec variants 
| Function | Program Path Argument | Argument List | Environment Passing |
| -------- | --------------------- | ------------- | ------------------- |
| `execl`  | Full path             | List of args  | Inherits env        |
| `execv`  | Full path             | `argv[]`      | Inherits env        |
| `execle` | Full path             | List of args  | Custom env          |
| `execve` | Full path             | `argv[]`      | Custom env          |
| `execlp` | Search in `PATH`      | List of args  | Inherits env        |
| `execvp` | Search in `PATH`      | `argv[]`      | Inherits env        |

All exec* calls replace the process with another program. The letters l/v/p/e tell you how arguments are passed, whether PATH is searched, and if you control the environment.

## Choosing Between Them
- Use execl / execv if you know the full path (/bin/ls).
- Use execlp / execvp if you want the shell-like behavior of searching in PATH.
- Use execle / execve if you want to specify a custom environment instead of inheriting.