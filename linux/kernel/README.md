# Kernel

## How to control to OOM Killer
Linux memory and swap usage become very high, Linux will run OOM Killer. OOM Killer evaluates all processes and selects the most proper process. After that, OOM Killer sends a SIGKILL signal to this process, forcibly terminates the process and reserves memory. Here will describe the means to control OOM Killer to some extent.

### Protect process from OOM Killer
In order to protect a specific process from OOM Killer, you can configure `-17` to `/proc/[PID]/oom_adj`. OOM Killer does not forcibly termination of process that have this setting.
