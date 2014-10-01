===sdnotify-proxy

This hack solves the problem of Docker containers running under systemd and wishing to make use of sd_notify facility.
Because Docker containers end up running as child processes of Docker daemon, they end up in a cgroup different from that
of the service. systemd will thus not process sd_notify event from them.

This utility will proxy events between Docker container and systemd. It is launched with name of proxy socket and a command
to execute. It will then start listening on the proxy socket and execute the command.
