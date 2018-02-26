# Linux misc

## Under the /proc directory
Although the purpose of the original `/proc` directory was debugging, it is now begin used for various purposes. The main contents of the pid directory are as follows.

|Contents|Explain|
|:---|:---|
|cmdline|Process complete command line|
|cwd|Symbolic link to the current working directory of the process|
|environ|Process's environment variables|
|exe|Pointer to executed binary|
|fd|A subdirectory containing an entry to the file descriptor whose process is open|
|maps|Process address space state|
|mem|Process memory space|
|mounts|A list of file systems currently mounted in the namespace for that process|
|root|A root directory of this process|
|stat|Status of this process|
|statm|Usage of memory|
|status|Detail status of this process|

## What is the difference between realtime and monotonic on dualtimestamp structure
Systemd has the structer of `dual_timestamp`.
It can contain `realtime` and `monotonic` timestamps.
The difference between these timestamps is as follows.

|field|meaning|
|:---|:---|
|realtime|This represents the real time. Hence, these is a possibility of go back due to synchronization of ntp. Therefore This is not suitable for acquisition of benchmark etc.|
|monotonic|It simply represents an increasing time. Time will not back.|

Also these times can be obtained from the `clock_gettime` function.
To obtain realtime, specify `CLOCK_REALTIME` as an argument, and when acquiring monotonic, specify `CLOCK_MONOTONIC` as an argument.
