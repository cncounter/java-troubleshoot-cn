## 17.3 Collect Data for a Bug Report

In general, it is recommended to **test with the available latest update release or even an available latest EA (Early Access) release to see if the issue persists** and then collect as much relevant data as possible when you create a bug report or submit a support call. The following sections suggest the data to collect and, where applicable, it provides recommendations for the commands or general procedure for obtaining the data.

* [Hardware Details]()

* [Operating System Details]()

* [Java SE Version]()

* [Command-Line Options]()

* [Environment Variables]()

* [Fatal Error Log]()

* [Core or Crash Dump]()

* [Detailed Description of the Problem]()

* [Logs and Traces]()

* [Results from Troubleshooting Steps]()


### 17.3.1 Hardware Details

Sometimes a bug arises or can be reproduced only on certain hardware configurations. If a fatal error occurs, the error log might contain the hardware details. If an error log is not available, document in the bug report the number and the type of processors in the machine, the clock speed, and, where applicable and if known, some details on the features of that processor. For example, in the case of Intel processors, it might be relevant that hyper-threading is available.


### 17.3.2 Operating System Details

On the Oracle Solaris operating system, the `showrev -a` command prints the operating system version and patch information.

On Linux, it is important to know which distribution and version is used. Sometimes the /etc/*release file indicates the release information, but as components and packages can be upgraded independently, it is not always a reliable indication of the configuration. Therefore, in addition to the information from the `*`release file, collect the following information:

* The kernel version. This can be obtained using the `uname -a` command.

* The `glibc` version. The `rpm -q glibc` command indicates the patch level of `glibc`.

* The thread library. There are two thread libraries for Linux, namely `LinuxThreads` and `NPTL`. The `LinuxThreads` library is used on 2.4 and older kernels and has "fixed stack" and "floating stack" variants. The Native POSIX Thread Library (`NPTL`) is used on the 2.6 kernel. Some Linux releases (such as RHEL3) include backports of `NPTL` to the 2.4 kernel. Use the command `getconf GNU_LIBPTHREAD_VERSION` to determine which thread library is used. If the `getconf` command returns an error to say that the variable does not exist, then it is likely that you are using an old kernel with the `LinuxThreads` library.


### 17.3.3 Java SE Version

The Java SE version string can be obtained using the `java -version` command.

Multiple versions of Java SE may be installed on the same machine. Therefore, ensure that you use the appropriate version of the `java` command by verifying that the installation bin directory appears in your `PATH` environment variable before other installations.


### 17.3.4 Command-Line Options

If the bug report does not include a fatal error log, it is important to document the full command line and all its options. This includes any options that specify heap settings (for example, the `-mx` option) or any `-XX` options that specify HotSpot specific options.

One of the features in Java SE is garbage collector ergonomics. On server-class machines the `java` command launches the HotSpot Server VM and a parallel garbage collector. A machine is considered to be a server machine if it has at least two processors and 2GB or more of memory.

The `-XX:+PrintCommandLineFlags` option can be used to verify the command-line options. This option prints all command-line flags to the VM. The command-line options can also be obtained for a running VM or core file using the `jmap` utility.

### 17.3.5 Environment Variables

Sometimes problems arise due to environment variable settings. When creating the bug report, indicate the values of the following Java environment variables (if set).

* `JAVA_HOME`

* `JRE_HOME`

* `JAVA_TOOL_OPTIONS`

* `_JAVA_OPTIONS`

* `CLASSPATH`

* `JAVA_COMPILER`

* `PATH`

* `USERNAME`

In addition, collect the following operating-system-specific environment variables.

* On Oracle Solaris and Linux operating systems, collect the values of the following environment variables.

  * `LD_LIBRARY_PATH`

  * `LD_PRELOAD`

  * `SHELL`

  * `DISPLAY`

  * `HOSTTYPE`

  * `OSTYPE`

  * `ARCH`

  * `MACHTYPE`

* On Linux, also collect the values of the following environment variables.

  * `LD_ASSUME_KERNEL`

  * `_JAVA_SR_SIGNUM`

* On Windows, collect the values of the following environment variables.

  * `OS`

  * `PROCESSOR_IDENTIFIER`

  * `_ALT_JAVA_HOME_DIR`



### 17.3.6 Fatal Error Log

**It is recommended to test with the latest update release to see if the problem persists.**

When a fatal error occurs, an error log is created. For detailed information about this file, see[Appendix A](https://github.com/cncounter/java-troubleshoot-cn/tree/master/18_Appendix_A_Fatal_Error_Log/).

The error log contains much information obtained at the time of the fatal error, such as version and environment information, details on the threads that provoked the crash, and so forth.

If the fatal error log is generated, be sure to include it in the bug report or support call.



### 17.3.7 Core or Crash Dump

Core and crash dumps can be very useful when trying to diagnose a system crash or hung process. The procedure for generating a dump is described in[Collect Core Dumps](17_04_Collect_Core_Dumps.md).



### 17.3.8 Detailed Description of the Problem

When creating a problem description, try to include as much relevant information as possible. Describe the application, the environment, and most importantly the events leading up to the time when the problem was encountered.

* If the problem is reproducible, list the steps that are required to demonstrate the problem.

* If the problem can be demonstrated with a small test case, include the test case and the commands to compile and execute the test case.

* If the test case or problem requires third-party code (for example, a commercial or open source library or package), provide details on where and how to obtain the library.

Sometimes the problem can be reproduced only in a complex application environment. In this case, the description, coupled with logs, core file, and other relevant information, might be the sole means to diagnose the issue. In these situations the description should indicate if the submitter is willing to run further diagnosis or run test binaries on the system where the issue arises.

### 17.3.9 Logs and Traces

In some cases, log or trace output can help to quickly determine the cause of a problem.

For example, in the case of a performance issue the output of the `-verbose:gc` option can help in diagnosing the problem. (This is the option to enable output from the garbage collector.)

In other cases the output from the `jstat` command can be used to capture statistical information over the time period leading up to the problem.

In the case of a deadlock or a hung VM (for example, due to a loop) the thread stacks can help diagnose the problem. The thread stacks are obtained by pressing Control+\ on Oracle Solaris and Linux and Control+Break on Windows.

In general, include all relevant logs, traces and other output in the bug report or support call.

### 17.3.10 Results from Troubleshooting Steps

Before submitting the bug report, be sure to document any troubleshooting steps that were performed.

For example, if the problem is a crash and the application has native libraries, you might have already run the application with the `-Xcheck:jni` option to reduce the likelihood that the bug is in the native code. Another case could be a crash that occurs with the HotSpot Server VM (`-server` option). If you have also tested with the HotSpot Client VM (`-client` option) and the problem does not occur, this gives an indication that the bug might be specific to the HotSpot Server VM.

In general, include in the bug report all troubleshooting steps and results that have already occurred. This type of information can often reduce the time that is required to diagnose an issue.

<https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/bugreports003.html>
