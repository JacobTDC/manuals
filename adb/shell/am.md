
## start \[options\] \<INTENT\>
**description:** start an Activity
**options:** 
 - `-D`: enable debugging
 - `-N`: enable native debugging
 - `-W`: wait for launch to complete
 - `--start-profiler <FILE>`: start profiler and send results to `<FILE>`
 - `--sampling INTERVAL`: use sample profiling with `INTERVAL` microseconds between samples.
	 - use with `--start-profiler`
 - `-P <FILE>`: like above, but profiling stops when app goes idle
 - `-R COUNT`: repeat the activity launch `COUNT` times.
	 - Prior to each repeat, the top activity will be finished.
 - `-S`: force stop the target app before starting the activity
 - `--track-allocation`: enable tracking of object allocations
 - `--user <USER_ID> | current`: Specify which user to run as; if not specified then run as the current user.
 - `--stack <STACK_ID>`: Specify into which stack should the activity be put.


## startservice \[options\] \<INTENT\>
**description:** start a Service.
**options:**
 - `--user <USER_ID> | current`: Specify which user to run as; if not specified then run as the current user.


## stopservice \[options\] \<PACKAGE\>
**description:** stop a Service.
**options:**
 - `--user <USER_ID> | current`: Specify which user to run as; if not specified then run as the current user.


## force-stop \[options\] \<PACKAGE\>
**description:** force stop everything associated with `<PACKAGE>`.
**options:**
 - `--user <USER_ID> | all | current`: Specify user to force stop; all users if not specified.


## kill \[options\] \<PACKAGE\>
**description:** Kill all processes associated with `<PACKAGE>`.
 - Only kills processes that are safe to kill -- that is, will not impact the user experience.

**options:**
 - `--user <USER_ID> | all | current`: Specify user whose processes to kill; all users if not specified.


## kill-all
**description:** Kill all background processes.
 - __WARNING:__ may be considered *DANGEROUS*


## broadcast \[options\] \<INTENT\>
**description:** force stop everything associated with `<PACKAGE>`.
**options:**
 - `--user <USER_ID> | all | current`: Specify which user to send to; if not specified then send to all users.
 - `--receiver-permission <PERMISSION>`: Require receiver to hold permission.


## instrument \[options\] \<COMPONENT\>
**description:** start an Instrumentation.
 - Typically this target `<COMPONENT>` is the form `<TEST_PACKAGE>/<RUNNER_CLASS>` or only `<TEST_PACKAGE>` if there is only one instrumentation.

**options:**
 - `-r`: print raw results (otherwise decode `REPORT_KEY_STREAMRESULT`).
	 - Use with `-e perf true` to generate raw output for performance measurements.
 - `-e <NAME> <VALUE>`: set argument `<NAME>` to `<VALUE>`. 
	 - For test runners a common form is `[-e <testrunner_flag> <value>[,<value>...]]`.
 - `-p <FILE>`: write profiling data to <FILE>
 - `-w`: wait for instrumentation to finish before returning.
	 - Required for test runners.
 - `--user <USER_ID> | current`: Specify user instrumentation runs in; current user if not specified.
 - `--no-window-animation`: turn off window animations while running.
 - `--abi <ABI>`: Launch the instrumented process with the selected ABI.
	 - This assumes that the process supports the selected ABI.


## trace-ipc start
**description:** start tracing IPC transactions.


## trace-ipc stop \[options\]
**description:** stop tracing IPC transactions and dump the results to file.
**options:**
 - `--dump-file <FILE>`: Specify the file the trace should be dumped to.


## profile start \[options\] \<PROCESS\> \<FILE\>
**description:** start profiler on a process.
 - The given `<PROCESS>` argument may be either a process name or pid.

**options:**
 - `--user <USER_ID> | current`: When supplying a process name, specify user of process to profile; uses current user if not specified.
 - `--sampling INTERVAL`: use sample profiling with `INTERVAL` microseconds between samples.


## profile stop \[options\] \[\<PROCESS\>\]
**description:** stop profiler on a process.
**options:**
 - `--user <USER_ID> | current`: When supplying a process name, specify user of process to profile; uses current user if not specified.


## dumpheap \[options\] \<PROCESS\> \<FILE\>
**description:** dump the heap of a process.
 - The given `<PROCESS>` argument may be either a process name or pid.

**options:**
 - `-n`: dump native heap instead of managed heap
 - `--user <USER_ID> | current`: When supplying a process name, specify user of process to dump; uses current user if not specified.


## set-debug-app \[options\] \<PACKAGE\>
**description:** set application `<PACKAGE>` to debug.
**options:**
 - `-w`: wait for debugger when application starts
 - `--persistent`: retain this value


## clear-debug-app
**description:** clear the previously set-debug-app.


## set-watch-heap \<PROCESS\> \<MEM-LIMIT\>
**description:** start monitoring pss size of `<PROCESS>`, if it is at or above `<MEM-LIMIT>` then a heap dump is collected for the user to report.


## clear-watch-heap
**description:** clear the previously set-watch-heap.


## bug-report \[options\]
**description:** request bug report generation; will launch a notification when done to select where it should be delivered.
**options:**
 - `--progress`: will launch a notification right away to show its progress.
 - `--telephony`: will dump only telephony sections.


## monitor \[options\]
**description:** start monitoring for crashes or ANRs.
**options:**  
 - `--gdb <port>`: start gdbserv on the given port at crash/ANR


## hang \[options\]
**description:** hang the system.
**options:**  
 - `--allow-restart`: allow watchdog to perform normal system restart


## restart
**description:** restart the user-space system.


## idle-maintenance
**description:** perform idle maintenance now.


## screen-compat \[on|off\] \<PACKAGE\>
**description:** control screen compatibility mode of `<PACKAGE>`.


## package-importance \<PACKAGE\>
**description:** print current importance of `<PACKAGE>`.


## to-uri \[INTENT\]
**description:** print the given Intent specification as a URI.


## to-intent-uri \[INTENT\]
**description:** print the given Intent specification as an intent: URI.


## to-app-uri \[INTENT\]
**description:** print the given Intent specification as an android-app: URI.


## switch-user \<USER_ID\>
**description:** switch to put `USER_ID` in the foreground, starting execution of that user if it is currently stopped.


## start-user \<USER_ID\>
**description:** start `USER_ID` in background if it is currently stopped, use switch-user if you want to start the user in foreground.


## unlock-user \<USER_ID\> \[TOKEN_HEX\] \([*undocumented function*](https://github.com/JacobTDC/manuals/wiki/Undocumented-Function#adb-shell-unlock-user)\)
**description:** undocumented function.


## stop-user \[options\] \<USER_ID\>
**description:** stop execution of `USER_ID`, not allowing it to run any code until a later explicit start or switch to it.
**options:**  
 - `-w`: wait for stop-user to complete.
 - `-f`: force stop even if there are related users that cannot be stopped.
