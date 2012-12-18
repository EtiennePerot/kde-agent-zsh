kde-agent-zsh
=============

Purpose
-------
Arch has a [`kde-agent`][kde-agent] package which starts its own [GPG]/[SSH]
agent on [KDE] startup.

This package replaces `kde-agent`. Instead of starting its own set of agents,
it runs zsh in interactive mode, grabs the GPG/SSH agent-related environment
variables, and uses those instead. This way you don't end up with four agents.

Usage
-----
Make sure that the following environment variables are exported in your ZSH
environment:

* `SSH_AUTH_SOCK`
* `SSH_AGENT_PID`
* `GPG_AGENT_INFO`
* `GPG_TTY` (optional)

Additionally, if you keep your environment variables stored in stateful files,
make sure the following environment variables are exported as well:

* `GPG_AGENT_ENV_FILE`
* `SSH_AGENT_ENV_FILE`

If exported, the files they refer to will be deleted on shutdown. This is not
guaranteed, however (since you may have a power outage or something), so make
sure that your ZSH startup script also takes care of ignoring those if they
contain stale values.

License
-------
kde-agent-zsh is licensed under the [WTFPL]. Enjoy.

[kde-agent]: https://www.archlinux.org/packages/extra/any/kde-agent/
[GPG]: https://en.wikipedia.org/wiki/GNU_Privacy_Guard
[SSH]: https://en.wikipedia.org/wiki/OpenSSH
[KDE]: https://kde.org/
[WTFPL]: http://sam.zoy.org/wtfpl/
