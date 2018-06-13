# 17.4 Collect Core Dumps

This section explains how to generate and collect core dumps (also known as crash dumps). A core dump or a crash dump is a memory snapshot of a running process. A core dump can be automatically created by the operating system when a fatal or unhandled error (for example, signal or system exception) occurs. Alternatively, a core dump can be forced by means of system-provided command-line utilities. Sometimes a core dump is useful when diagnosing a process that appears to be hung; the core dump may reveal information about the cause of the hang.

When collecting a core dump, be sure to gather other information about the environment so that the core file can be analyzed (for example, OS version, patch information, and the fatal error log).

Core dumps do not usually contain all the memory pages of the crashed or hung process. With each of the operating systems discussed here, the text (or code) pages of the process are not included in core dumps. But to be useful, a core dump must consist of pages of heap and stack as a minimum. Collecting non-truncated good core dump files is essential for postmortem analysis of the crash.

The following sections describe scenarios for collecting core dumps.

* [Collect Core Dumps on Oracle Solaris]()

* [Collect Core Dumps on Linux]()

* [Reasons for Not Getting a Core File]()

* [Collect Crash Dumps on Windows]()


### 17.4.1 Collect Core Dumps on Oracle Solaris

With the Oracle Solaris operating system, unhandled signals such as a segmentation violation, illegal instruction, and so forth, result in a core dump. By default, the core dump is created in the current working directory of the process and the name of the core dump file is core. The user can configure the location and name of the core dump using the core file administration utility, `coreadm`. This procedure is fully described in the man page for the `coreadm` utility.

The `ulimit` utility is used to get or set the limitations on the system resources available to the current shell and its descendants. Use the `ulimit -c` command to check or set the core file size limit. Make sure that the limit is set to `unlimited`; otherwise the core file could be truncated.


> **Note:**

> `ulimit` is a Bash shell built-in command; on a C shell, use the `limit` command.

Ensure that any scripts that are used to launch the VM or your application do not disable core dump creation.

The `gcore` utility can be used to get a core image of running processes. This utility accepts a process id (pid) of the process for which you want to force core dump.

To get the list of Java processes running on the machine, you can use any of the following commands:

* `ps -ef | grep java`

* `pgrep java`

* `jps`


>**Note:**

>The `jps` command-line utility does not perform name matching (that is, looking for "java" in the process command name) and so it can list Java VM embedded processes as well as the Java processes.

The following are two methods to collect core dumps on Oracle Solaris.

* **ShowMessageBoxOnError option on Oracle Solaris:**

  A Java process can be started with the `-XX:+ShowMessageBoxOnError` command-line option. When a fatal error is encountered, the process prints a message to standard error and waits for a `yes` or `no` response from standard input.[Example 17-1]() shows the output when an unexpected signal occurs.

  Example 17-1 Unexpected Signal Error on Solaris

```
=======================================================================
Unexpected Error
-----------------------------------------------------------------------
SIGSEGV (0xb) at pc=0xfeba31ac, pid=8677, tid=2
Do you want to debug the problem?
To debug, run 'dbx - 8677'; then switch to thread 2
Enter 'yes' to launch dbx automatically (PATH must include dbx)
Otherwise, press RETURN to abort...
=======================================================================
```

  Before answering `yes` or pressing RETURN (Enter), use the `gcore` utility to force a core dump. Then you can type `yes` to launch the `dbx` debugger.

* **Suspend a process with truss utility:**

  In situations where it is not possible to specify the `-XX:+ShowMessageBoxOnError` option, you might be able to use the `truss` utility. This Oracle Solaris operating system utility is used to trace system calls and signals. You can use this utility to suspend the process when it reaches a specific function or system call.

  The command in[Example 17-2]() shows how to use the `truss` utility to suspend a process when the `exit` system call is executed (in other words, the process is about to exit).

  > Example 17-2 Use truss Utility to Suspend a Process

```
$ truss -t \!all -s \!all -T exit -p pid

```

  When the process calls `exit`, it will be suspended. At this point, you can attach the debugger to the process or call `gcore` to force a core dump.


### 17.4.2 Collect Core Dumps on Linux

On the Linux operating system, unhandled signals such as segmentation violation, illegal instruction, and so forth, result in a core dump. By default, the core dump is created in the current working directory of the process and the name of the core dump file is core.pid, where pid is the process id of the crashed Java process.

The `ulimit` utility is used to get or set the limitations on the system resources available to the current shell and its descendants. Use the `ulimit -c` command to check or set the core file size limit. Make sure that the limit is set to `unlimited`; otherwise the core file could be truncated.

> **Note:**

`ulimit` is a Bash shell built-in command; on a C shell, use the `limit` command.


Ensure that any scripts that are used to launch the VM or your application do not disable core dump creation.

You can use the `gcore` command in the `gdb` (GNU Debugger) interface to get a core image of a running process. This utility accepts the pid of the process for which you want to force the core dump.

To get the list of Java processes running on the machine, you can use any of the following commands:

* `ps -ef | grep java`

* `pgrep java`

* `jps`


> **Note:**

> The `jps` command-line utility does not perform name matching (that is, looking for "java" in the process command name) and so it can list Java VM embedded processes as well as the Java processes.

The following is one option to collect core dumps on Linux.

* **ShowMessageBoxOnError option in Linux:**

  A Java process can be started with the `-XX:+ShowMessageBoxOnError` command-line option. When a fatal error is encountered, the process prints a message to standard error and waits for a `yes` or `no` response from standard input.[Example 17-3]() shows the output when an unexpected signal occurs.

  > Example 17-3 Unexpected Signal Error in Linux

```
=======================================================================
Unexpected Error
-----------------------------------------------------------------------
SIGSEGV (0xb) at pc=0x06232e5f, pid=11185, tid=8194
Do you want to debug the problem?
To debug, run 'gdb /proc/11185/exe 11185'; then switch to thread 8194
Enter 'yes' to launch gdb automatically (PATH must include gdb)
Otherwise, press RETURN to abort...
=======================================================================

```

  Type `yes` to launch the `gdb` (GNU Debugger) interface, as suggested by the error report shown above. In the `gdb` prompt, you can give the `gcore` command. This command creates a core dump of the debugged process with the name core.pid, where pid is the process ID of the crashed process. Make sure that the `gdb gcore` command is supported in your versions of `gdb`. Look for `help gcore` in the `gdb` command prompt.


### 17.4.3 Reasons for Not Getting a Core File

The following list explains the major reasons that a core file might not be generated. This list pertains to both Oracle Solaris and Linux operating systems, unless specified otherwise.

* The current user does not have permission to write in the current working directory of the process.

* The current user has write permission on the current working directory, but there is already a file named core that has read-only permission.

* The current directory does not have enough space or there is no space left.

* The current directory has a subdirectory named core.

* The current working directory is remote. It might be mapped by NFS (Network File System), and NFS failed just at the time the core dump was about to be created.

* Oracle Solaris operating system only: The `coreadm` tool has been used to configure the directory and name of the core file, but any of the above reasons apply for the configured directory or filename.

* The core file size limit is too low. Check your core file limit using the `ulimit -c` command (Bash shell) or the `limit -c` command (C shell). If the output from this command is not unlimited, the core dump file size might not be large enough. If this is the case, you will get truncated core dumps or no core dump at all. In addition, ensure that any scripts that are used to launch the VM or your application do not disable core dump creation.

* The process is running a `setuid` program and therefore the operating system will not dump core unless it is configured explicitly.

* Java specific: If the process received `SIGSEGV` or `SIGILL` but no core dump, it is possible that the process handled it. For example, HotSpot VM uses the `SIGSEGV` signal for legitimate purposes, such as throwing `NullPointerException`, deoptimization, and so forth. The signal is unhandled by the Java VM only if the current instruction (PC) falls outside Java VM generated code. These are the only cases in which HotSpot dumps core.

* Java specific: The JNI Invocation API was used to create the VM. The standard Java launcher was not used. The custom Java launcher program handled the signal by just consuming it and produced the log entry silently. This situation has occurred with certain Application Servers and Web Servers. These Java VM embedding programs transparently attempt to restart (fail over) the system after an abnormal termination. In this case, the fact that a core dump is not produced is a feature and not a bug.


### 17.4.4 Collect Crash Dumps on Windows

On Windows operating system there are three types of crash dumps:

* Dr. Watson logfile, which is a text error log file that includes faulting stack trace and a few other details.

* User minidump, which can be considered a "partial" core dump. It is not a complete core dump, because it does not contain all the useful memory pages of the process.

* Dr. Watson full-dump, which is equivalent to a Unix core dump. This dump contains most memory pages of the process (except for code pages).

When an unexpected exception occurs on Windows, the action taken depends on two values in the following registry key:

```
\\HKEY_LOCAL_MACHINE\Software\Microsoft\Windows NT\CurrentVersion\AeDebug

```

The two values are named `Debugger` and `Auto`. The `Auto` value indicates if the debugger specified in the value of the `Debugger` entry starts automatically when an application error occurs.

* A value of `0` for `Auto` means that the system displays a message box notifying the user when an application error occurs.

* A value of `1` for `Auto` means that the debugger starts automatically.

The value of `Debugger` is the debugger command that is to be used to debug program errors.

When a program error occurs, Windows examines the `Auto` value and if the value is `0` it executes the command in the `Debugger` value. If the value for `Debugger` is a valid command, a message box is created with two buttons: **OK** and **Cancel**. If the user clicks **OK**, the program is terminated. If the user clicks **Cancel**, the specified debugger is started. If the value for the `Auto` entry is set to `1` and the value for the `Debugger` entry specifies the command for a valid debugger, the system automatically starts the debugger and does not generate a message box.

The following are two ways to collect crash dump on Windows.

* **Configure Dr.Watson:**

  The Dr. Watson debugger is used to create crash dump files. By default, the Dr. Watson debugger (drwtsn32.exe) is installed into the Windows system folder (%SystemRoot%\System32).

  To install Dr. Watson as the postmortem debugger, run the following command:

```
drwtsn32 -i

```

  To configure name and location of crash dump files, run `drwtsn32` without any options.

  In the Dr. Watson GUI window, make sure that the **Create Crash Dump File** check box is selected and that the crash dump file path and log file path are configured in their respective text fields.

  Dr. Watson may be configured to create a full dump using the registry. The registry key is shown in[Example 17-4]().

  > Example 17-4 Registry Key to Create a Full Dump

```
System Key: [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DrWatson]
Entry Name: CreateCrashDump
Value: (0 = disabled, 1 = enabled)

```

  > _Note:_ If the application handles the exception, then the registry-configured debugger is not invoked. In that case it might be appropriate to use the `-XX:+ShowMessageBoxOnError` command-line option to force the process to wait for user intervention on fatal error conditions.

* **Force a crash dump:**

  On the Windows operating system, the `userdump` command-line utility can be used to force a Dr. Watson dump of a running process. The `userdump` utility does not ship with Windows but instead is released as a component of the OEM Support Tools package.

  An alternative way to force a crash dump is to use the `windbg` debugger. The main advantage of using `windbg` is that it can attach to a process in a non-invasive manner (that is, read-only). Normally Windows terminates a process after a crash dump is obtained but with the non-invasive attach it is possible to obtain a crash dump and let the process continue. To attach the debugger non-invasively requires selecting the **Attach to Process** option and the **Noninvasive** checkbox.

  When the debugger is attached, a crash dump can be obtained using the command shown in[Example 17-5]().

  > Example 17-5 Get a Crash Dump

```
.dump /f crash.dmp

```

  The `windbg` debugger is included in the "Debugging Tools for Windows" download.

  An additional utility in this download is the `dumpchk.exe` utility, which can verify that a memory dump file has been created correctly.

  Both `userdump.exe` and `windbg` require the pid of the process. The `userdump -p` command lists the process and program for all processes. This is useful if you know that the application is started with the `java.exe` launcher. However, if a custom launcher is used (embedded VM), it might be difficult to recognize the process. In that case you can use the `jps` command-line utility as it lists the pids of the Java processes only.

  As with Oracle Solaris and Linux operating systems, you can also use the `-XX:+ShowMessageBoxOnError` command-line option on Windows. When a fatal error is encountered, the process shows a message box and waits for a `yes` or `no` response from the user.

  Before clicking **Yes** or **No**, you can use the `userdump.exe` utility to generate the Dr. Watson dump for the Java process. This utility can also be used in cases when the process appears to be hung.




<https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/bugreports004.html>
