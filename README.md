# Introduction
`psig` list process signal information using `bash`.

# Prerequisites
* The following packages are installed:
```no-highlight
gawk
column
```

* The path `/usr/local/bin/` exists in the `${PATH}` variable:
```bash
$ echo "${PATH//:/\n}"
```
```
/home/ramon/bin
/usr/local/bin
/usr/bin
/bin
/usr/local/sbin
/usr/sbin
/sbin
/usr/local/games
/usr/games
/usr/lib/llvm/6/bin
/opt/bin
```

# Installation
Clone the repository into your current working directory:
```bash
$ git clone "https://codeberg.org/keks24/psig.git"
```

Copy all necessary files:
```bash
$ cd "psig/"
$ cp "usr/local/bin/psig" "/usr/local/bin/"
$ chmod 755 "/usr/local/bin/psig"
```

# Usage
```bash
$ psig <pid> [pid...]
```

## Example
```bash
$ psig "${$}" 4710

PID: 23367
Name: zsh
UID: 1000 1000 1000 1000
GID: 1000 1000 1000 1000
Queued: 0/63858
Signals caught:
---------------
Signal 28: SIGWINCH
Signal 17: SIGCHLD
Signal 14: SIGALRM
Signal 13: SIGPIPE
Signal 2: SIGINT
Signal 1: SIGHUP
Hexadecimal:  0     0     0     0     0     0     0     0     0     8     0     1     3     0     0     3
Binary:       0000  0000  0000  0000  0000  0000  0000  0000  0000  1000  0000  0001  0011  0000  0000  0011

Signals ignored:
----------------
Signal 22: SIGTTOU
Signal 21: SIGTTIN
Signal 20: SIGTSTP
Signal 15: SIGTERM
Hexadecimal:  0     0     0     0     0     0     0     0     0     0     3     8     4     0     0     0
Binary:       0000  0000  0000  0000  0000  0000  0000  0000  0000  0000  0011  1000  0100  0000  0000  0000

Signals pending (process):
--------------------------
No signals found.

Signals pending (thread):
-------------------------
No signals found.

Signals blocked:
----------------
Signal 28: SIGWINCH
Hexadecimal:  0     0     0     0     0     0     0     0     0     8     0     0     0     0     0     0
Binary:       0000  0000  0000  0000  0000  0000  0000  0000  0000  1000  0000  0000  0000  0000  0000  0000

PID: 4710
Name: awesome
UID: 1000 1000 1000 1000
GID: 1000 1000 1000 1000
Queued: 0/63858
Signals caught:
---------------
Signal 15: SIGTERM
Signal 11: SIGSEGV
Signal 8: SIGFPE
Signal 7: SIGBUS
Signal 6: SIGABRT
Signal 4: SIGKILL
Signal 2: SIGINT
Signal 1: SIGHUP
Hexadecimal:  0     0     0     0     0     0     0     1     8     0     0     0     4     4     e     b
Binary:       0000  0000  0000  0000  0000  0000  0000  0001  1000  0000  0000  0000  0100  0100  1110  1011

Signals ignored:
----------------
Signal 13: SIGPIPE
Hexadecimal:  0     0     0     0     0     0     0     0     0     0     0     0     1     0     0     0
Binary:       0000  0000  0000  0000  0000  0000  0000  0000  0000  0000  0000  0000  0001  0000  0000  0000

Signals pending (process):
--------------------------
No signals found.

Signals pending (thread):
-------------------------
No signals found.

Signals blocked:
----------------
No signals found.
```

List signals of all processes:
```bash
$ psig $(ps aux | awk 'NR >= 2 { print $2 }') | less
```

# Parameters
Multiple `PIDs` can be analysed.

# Further information
```bash
$ man 5 proc
$ man 7 signal
```
