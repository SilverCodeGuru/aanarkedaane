# daemons

services
hidden
background

process - instance of a runnign program
interactive process - that we started

command

ps -aux | grep systemd
pstree
systemctl
    start
    stop
    status
    enable
    disable
    restart
    reload
    reload-or-restart (some services)
    is-enabled
    list-units -t service -all
    list-unit-files

journalctl -xe

daemons

- ssh
- ntp
- thermald
- systemd

master daemon is systemd
init system
first process created
it is also service manager


units are also daemons but started by systemd

some services will fail
some you will have to enable