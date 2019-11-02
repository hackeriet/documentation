# How to restart the doorsystem

The doorservice is now installed as a daemon and should get started on
boot. Use regular "service" commands to start, stop, restart og check
status.
```
    root@humladoor:~# service door start
    [ ok ] Starting system door daemon:.

    root@humladoor:~# service door stop
    [ ok ] Stopping system door daemon:.

    root@humladoor:~# service door restart
    [....] Stopping system door daemon:start\-stop\-daemon: warning: failed to kill 2449: No such process
    No process in pidfile '/var/run/door.pid' found running; none killed.
     failed!
    [ ok ] Starting system door daemon:.

    root@humladoor:~# service door status
    [ ok ] /usr/local/bin/door.sh is running.
```

Other usefull files for making changes:

* `/etc/init.d./door`

