# systemd-pingerd
Simple pinger daemon with several example systemd service units.

**pingerd** just outputs "ping" to stdout forever - Both Bourne and Python3 variants.

Several examples are provided demonstrating different ways of starting and running daemons:

**simple-pinger.service** - runs *pingerd* directly from *ExecStart* in the unit using *Type=simple* and is recommended way. systemd automatically daemonises the process and there is no need for a wrapper script to fork it.

**forking-pinger.service** - uses a wrapper shell which forks pingerd and exits. Unit *Type=forking* is used - this is typical of traditional sysV init scripts. systemd automatically detects the main PID for pingerd.

**oneshot-pinger.service** - demonstrates running a forking process as *Type=oneshot*. For this to work *RemainAfterExit=yes* must be set. The subtle difference here is that the main PID detected is that of the wrapper script, not the daemon. 
