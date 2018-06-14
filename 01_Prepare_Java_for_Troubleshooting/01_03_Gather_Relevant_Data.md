## 1.3 Gather Relevant Data

If your application runs into a problem and you want to debug the problem further, make sure that you collect any relevant data before restarting the system, especially if restarting will remove previous files.

The following are important files to gather:

* Core files for crash issues.

* `hs_err` printed text file for Java crashes.

* Log files: Java and application logs.

* Java heap dumps for `-XX:+HeapDumpOnOutOfMemoryError`.

* Java flight recordings (if enabled) - If the problem didn't terminate the application, dump the continuous recordings.

If the application has stopped responding, then gather the following files.

* Stack traces: Take several stack traces using `jcmd <pid> Thread.print` before restarting the system.

* Dump flight recordings (if enabled).

* Force a core file: If the application can't be closed properly, then stop the application and force a core file using `kill -6 <pid>` on Linux or Solaris systems.

### 1.3.1 Make a Java Application Easier to Debug

Using a logging framework is a good way to enable future debugging. If you run into problems in a specific module, you should be able to enable logging in that module. It is also good to specify different levels of logging, for example info, debug and trace. For details about how to use the `java.util.logging` framework, see[Java Logging Technology](https://docs.oracle.com/javase/8/docs/technotes/guides/logging/index.html).

<https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/prepapp003.html>
