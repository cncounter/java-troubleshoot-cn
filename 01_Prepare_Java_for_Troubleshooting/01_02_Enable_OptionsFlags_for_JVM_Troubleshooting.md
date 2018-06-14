## 1.2 Enable Options/Flags for JVM Troubleshooting

This section describes setting up JVM options/flags to enable gathering relevant data for troubleshooting.

The data you gather depends on the system and what data you actually would use in case you ran into problems. Consider gathering the following data before you run into a problem.

1. **Enable core files:** If Java crashes, for example due to a segmentation fault, the OS saves to disk a _core file_ (complete dump of the memory). On Linux and Solaris, _core files_ are sometimes disabled by default. To enable _core files_ on Linux/Solaris, it is usually enough to run the command `ulimit -c unlimited` on the command line before starting the application (some systems may have different ways to handle these limits).

  > _Note:_ The _core files_ take up a lot of disk space, especially when run with a large Java heap.

  To decide whether to enable _core files_, consider what you would do if you had a crash in your system. Would you want to see a core file? Many Java users won't have much use for a core file. However, if you would want to debug a possible crash either in a native debugger such as `gdb` or by using the _Serviceability Agent_, then make sure that you enable _core files_ before the start of application.

  Many times crashes may be hard to reproduce; therefore, enable core files before the start of application. For more details about _Serviceability Agent's HSDB and CLHSDB tools_, read the article from[Java Magazine](http://www.oraclejavamagazine-digital.com/javamagazine/20120708?pg=41#pg41).

2. **Add -XX:+HeapDumpOnOutOfMemoryError to the JVM flags:** The `-XX:+HeapDumpOnOutOfMemoryError` flag saves a Java Heap dump to disk if the applications runs into an `OutOfMemoryError`. Use [The jhat Utility](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/tooldescr012.html) tool to inspect the Java heap and find out which object takes up the most space, and then check for objects that are no longer used, but kept alive.

  Like _core files_, heap dumps can be very large, especially when run with a big Java heap.

  Again, think about what you would do if the application runs into an `OutOfMemoryError`. Would you want to inspect the heap at the time of the error? In that case, turn onthis flag by default so that you get this data if the application runs into an unexpected `OutOfMemoryError`.

3. **Run a continuous Java flight recording:** The Java Flight Recorder (JFR) is a commercial feature. You can use it for free on developer desktops/laptops, and for evaluation purposes in test, development, and production environments. **However, to enable JFR on a production server, you need a commercial license**.

  Set up Java to run with a continuous flight recording. Continuous flight recordings are a circular buffer of JFR events. If the application runs into an issue, you can dump the data from the last hour of the run. The JFR events can be extremely helpful to debug a wide range of issues from memory leaks to network errors, high CPU usage, thread blocks and so on.

  The overhead of running with a continuous flight recording is very low. For more details about producing a continuous Java Flight Recording, see [How to Produce a Flight Recording](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/tooldescr004.html).

4. **Add -verbosegc to the JVM command-line:** The flag `-verbosegc` logs basic information about Java Garbage Collector. This log helps you find the following:

  * Does garbage collection run for a long time?

  * Does the free memory decrease over time?

  The garbage collector log helps diagnose issues when the application throws an `OutOFMemoryError` or the application runs into performance issues; therefore, turning on the `-verbosegc` flag on by default helps troubleshoot issues.

  > _Note:_ Use log rotation so that an application restart doesn't delete the previous logs. Since JDK7, the flags `UseGClogFileRotation` and `NumberOfGCLogFiles` can be used to set up for log rotation. For description on these flags, see [Debugging Options for Java HotSpot VM](http://www.oracle.com/technetwork/java/javase/tech/vmoptions-jsp-140102.html).

5.  **Print Java version and JVM flags:** Prior to filing a bug on Java or seeking help from a forum, have the basic information handy in the log files. For example, it's helpful to print out the Java version and the JVM flags used.

  If your application starts with a script, simply run `java -version` to print the Java version and print the command line before executing it. Another alternative is to add `-XX+PrintCommandLineFlags` and `-showversion` to the JVM arguments.

6.  **Set up JMC JMX for remote monitoring:** JMX can be used to connect to a Java application remotely using tools such as Mission Control or Visual VM. Unless you can run these tools on the same machine that is running your application, setting this up can be helpful later on to monitor the application, send diagnostic commands, manage flight recordings and so on. There is no performance overhead in enabling JMX.

  See the instructions about [How to monitor JVM using JMX Technology](https://docs.oracle.com/javase/8/docs/technotes/guides/management/agent.html).

  Another alternative to enable JMX after a Java application has started is to use the diagnostic command `ManagementAgent.start`. Run `jcmd &lt;pid&gt; help ManagementAgent.start` for a list of flags that can be sent with the command.

  For more details on `jcmd`, see [The jcmd Utility](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/tooldescr006.html).


<https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/prepapp002.html>
