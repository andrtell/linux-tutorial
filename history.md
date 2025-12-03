[Back to top](README.md)

# History
Hints on how to use the `history` command with the `bash` shell.
## Help

```
history --help
```
```
man bash
```
The following is a summary (or copy) of the above.



## Session

Bash maintains a history of commands in memory while running. They are written to `.bash_history` on exit.

```
shopt -s histappend
```
Append to history file on exit.

## CLI
```
history

1  ls
2  cat README.md
3  history
```
Show history
```
history 2

2  cat README.md
3  history
```
Show recent history
```
!2
```
Execute entry no: `2` from history
```
CTRL-r or CTRL-s
```
Search history. Add `stty -ixon` to `.bashrc` to enable `CTRL-s`.
```
history -c
```
Clear history
```
history -d 192
```
Delete specific entry
## ENV
See `man bash`.

```
echo $HISTFILE

/home/john/.bash_history
```
Location of the history file
```
export HISTCONTROL=ignoredups
```
Do not save command if already in history.
```
export HISTCONTROL=erasedups
```
Store command but remove any previous duplicates.
```
export HISTCONTROL=ignorespace
```
Do not store if command start with a space.
```
export HISTCONTROL=erasedups:ignorespace
```
Combine options with a `:`.
```
export HISTSIZE=10000
```
Number of entries to save in history.
```
export HISTTIMEFORMAT='%y-%m-%d %R  '
```
Print time stamp for each entry. See `man 3 strftime`.
```
export PROMPT_COMMAND='history -a'
```
Append entry to `.bash_history` after command is issued. If you have multiple bash sessions going, history will be interleaved.


