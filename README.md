# zsh-pane
A tiny zsh function to display and refresh headerless output from any command in a terminal window.


This is a small and fairly straightforward function for zsh which solves a problem many others have probably solved before: how to display (and regularly refresh) the output of a given command in a terminal window / pane, without adding headers or footers, or returning to the terminal prompt.

Because it runs the command in a "real" terminal, colors and other ANSI features are preserved. (Simpler methods for accomplishing this often cause commands to revert back to plaintext output.) By using the `--exec` flag and enclosing your shell command in quotation marks, you can even run complex commands with pipes and redirection.

The code is a shell function for zsh, and needs to be added to your .zshrc file to be used. (Reload the file with `source ~/.zshrc` after adding it to activate, or just restart your terminal.)

## Usage:

```shell
pane [--interval SECONDS|-n SECONDS] 
     [--exec 'SHELL COMMAND' | -e 'SHELL COMMAND']
     [--] <command> [arg1 ...]
```

## Examples:

```shell
pane fastfetch

pane --interval 60 -- tail -n 50 /private/var/log/system.log

pane -n 180 -- curl 'wttr.in/Tokyo?Fq'

pane -n 60 --exec 'tail -n 200 /private/var/log/system.log | grep syslogd'
```

`interval` will default to 300 seconds (5 minutes).
You can optionally include `--` to indicate the end of options, after which the command to run should be specified. (It will work without this, but it can help to make the command syntax more clear.)


### To-Do:
- Add more error handling (e.g., for invalid commands)
- Implement a way to stop the command gracefully (currently you can just CTRL-C out of it)