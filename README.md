Dotfiler: Growl helpers
=======================

This repository contains some helpers to use growl from ssh sessions.
It's purpose to be used as a repository for [dotfiler][].

For convinience, don't copy these files into you homedir. Instead,
go and install [dotfiler][], then clone this repository, using
`dot add <url>` command and run `dot update` to make all necessary
symlinks.

This helper is a zsh function notify-back, which goes via ssh back to
you desktop and calls growlnotify.

To make it work, add something like that to the `~/.ssh/config` on your
desktop machine:

    Host salmon
    RemoteForward *:2022 localhost:22

And something like this on your remote machine:

    Host back
    Hostname localhost
    Port 2022

After that, install [command line utility `growlnotify`](http://growl.info/downloads) to
the desktop. And of cause don't forget to install this helper, using these commands on
remote machine:

    dot add https://github.com/svetlyak40wt/dot-growl
    dot update

To test, login via ssh to the remote machine and run:

    notify-back "Hello from remote machine"

If all was done right, a growl notification should pop up on the desktop's screen.

[dotfiler]: https://github.com/svetlyak40wt/dotfiler