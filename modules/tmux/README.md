Tmux
====

Defines [tmux][1] aliases and provides for auto launching it at start-up.

Settings
--------

### Auto-Start

Starts a tmux session automatically when Zsh is launched.

To enable this feature, add the following line to *zshrc*:

    zstyle ':dotzsh:module:tmux' auto-start 'yes'

It will create a background session named _#DOTZSH_ and attach every new shell to
it.

To avoid keeping open sessions, this module sets `destroy-unattached off` on
the background session and `destroy-unattached on` on every other session
(global setting).

Aliases
-------

  - `ta` attaches or switches to a tmux session.
  - `tl` lists sessions managed by the tmux server.

If [tmuxinator][6] is installed, these aliases will also be setup

  - `ts [project_name]` start a tmux session using project's tmuxinator config
  - `to [project_name]` create a new project file and open it in your editor
  - `tc [source_project] [new_project]` copy source_project project file to a new project called new_project
  - `tD [project_name]` deletes the project called project_name
  - `tI` deletes all existing projects!
  - `tls` list all existing projects
  - `tlsv` verbosly list all existing projects
  - `tdoc` look for problems in your configuration

Caveats
-------

On Mac OS X, launching tmux can cause the error **launch_msg(...): Socket is not
connected** to be displayed, which can be fixed by installing
[reattach-to-user-namespace][3], available in [Homebrew][4], and adding the
following to *tmux.conf*:

  if-shell 'test "$(uname)" = "Darwin"' set-option -g default-command "reattach-to-user-namespace -l $SHELL -l"

Furthermore, tmux is known to cause **kernel panics** on Mac OS X. A discussion
about this and DOTZSH has already been [opened][2].

Authors
-------

*The authors of this module should be contacted via the [issue tracker][5].*

  - [Sorin Ionescu](https://github.com/sorin-ionescu)
  - [Colin Hebert](https://github.com/ColinHebert)

[1]: http://tmux.sourceforge.net
[2]: http://git.io/jkPqHg
[3]: ChrisJohnsen/tmux-MacOSX-pasteboard
[4]: mxcl/homebrew
[5]: https://github.com/dotphiles/dotzsh/issues
[6]: https://github.com/aziz/tmuxinator

