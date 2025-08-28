# zsh-pane
A tiny zsh function to display and refresh headerless output from any command in a terminal window.


This is a small and fairly straightforward function for zsh which solves a problem many others have probably solved before: how to display (and regularly refresh) the output of a given command in a terminal window / pane, without adding headers or footers, or returning to the terminal prompt.

Because it runs the command in a "real" terminal, colors and other ANSI features are preserved. (Simpler methods for accomplishing this often cause commands to revert back to plaintext output.)

The code is a shell function for zsh, and needs to be added to your .zshrc file to be used. (Reload the file with `source ~/.zshrc` after adding it to activate, or just restart your terminal.)

## Usage:

```shell
pane <command...> [--interval SECONDS]
```

`interval` will default to 300 seconds (5 minutes).


### To-Do:
- Add more error handling (e.g., for invalid commands)
- Implement a way to stop the command gracefully (currently you can just CTRL-C out of it)
- Allow more complex commands to be interpreted correctly (pipes etc.)
- Fix cases where certain commands don't behave as expected.