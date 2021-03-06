Dotfiler: Growl helpers
=======================

This repository contains some helpers to use growl from ssh sessions.
It's purpose to be used as a repository for [dotfiler][].

For convinience, don't copy these files into you homedir. Instead,
go and install [dotfiler][], then clone this repository, using
`dot add <url>` command and run `dot update` to make all necessary
symlinks.

What is this?
-------------

This helper provides a shell command `nb`, which goes via ssh back to
you desktop and calls `growlnotify` or `terminal-notifier` or `alerter`
(Actually, if you run it on the desktop, where `/usr/local/bin/growlnotify`
is available, it will call it directly.)

This quite useful, when you frequently running some slow process on a
server and want to be notified when it is done. In this case you just do:

    some-long-running-task --with params; nb 'Horay! Task done.'

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

    nb "Hello from remote machine"

If all was done right, a growl notification should pop up on the desktop's screen.

[dotfiler]: https://github.com/svetlyak40wt/dotfiler
