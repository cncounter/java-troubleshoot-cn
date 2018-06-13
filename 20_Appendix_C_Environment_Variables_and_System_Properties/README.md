# Appendix C Environment Variables and System Properties

This appendix describes environment variables and system properties that can be useful for troubleshooting problems with the Java HotSpot VM.

[Submit a Bug Report](https://github.com/cncounter/java-troubleshoot-cn/tree/master/17_Submit_a_Bug_Report/) contains information on collecting environment variables in [Environment Variables](https://github.com/cncounter/java-troubleshoot-cn/tree/master/17_Submit_a_Bug_Report/).

This appendix contains the following sections:


##  The `JAVA_HOME` Environment Variable


This variable `JAVA_HOME` indicates the directory where the Java Development Kit (JDK) software is installed.


##  The `JAVA_TOOL_OPTIONS` Environment Variable


In many environments the command line is not readily accessible to start the application with necessary command-line options. This often arises with applications that use embedded VMs (meaning they use the Java Native Interface (JNI) Invocation API to start the VM), or where the startup is deeply nested in scripts. In these environments the `JAVA_TOOL_OPTIONS` environment variable can be useful to augment a command line.

When this environment variable is set, the `JNI_CreateJavaVM` function (in the JNI Invocation API) prepends the value of the environment variable to the options supplied in its `JavaVMInitArgs` argument.

> **Note:**:

> In some cases this option is disabled for security reasons (for example, on Oracle Solaris operating system this option is disabled when the effective user or group ID differs from the real ID).


This environment variable allows you to specify the initialization of tools, specifically the launching of native or Java programming language agents using the `-agentlib` or `-javaagent` options. In the following example the environment variable is set so that the HPROF profiler is launched when the application is started:

```
$ export JAVA_TOOL_OPTIONS="-agentlib:hprof"

```

This variable can also be used to augment the command line with other options for diagnostic purposes. For example, you can supply the `-XX:OnError` option to specify a script or command to be executed when a fatal error occurs.

Since this environment variable is examined at the time the `JNI_CreateJavaVM` function is called, it cannot be used to augment the command line with options that would normally be handled by the launcher, for example, VM selection using the `-client` option or the `-server` option.

For more information on `JAVA_TOOL_OPTIONS` environment variable, see Java tool options from[JVM Tool Interface](https://docs.oracle.com/javase/8/docs/platform/jvmti/jvmti.html#tooloptions) documentation.



## The `java.security.debug` System Property

This system property controls whether the security system of the Java Runtime Environment (JRE) prints trace messages during execution. This option can be useful when diagnosing an issue involving a security manager when a `SecurityException` is thrown.

The `java.security.debug` property can have the following values:

* `access`

  Print all `checkPermission` results.

  The following additional options can be specified with the `access` option:

  * `stack`

  Include stack trace.

  * `domain`

  Dump all domains in context.

  * `failure`

  Before throwing an exception, dump the stack and domain that did not have permission.

* `jar`

  Print JAR verification information.

* `policy`

  Print permissions that `SecureClassLoader` assigns.

* `scl`

  For example, to print all `checkPermission` results and trace all domains in context, set the `java.security.debug` property to `access,stack`. To trace access failures, set the property to `access,failure`.

> Example C-1 Program for `checkPermission` Failure

```
$ java -Djava.security.debug="access,failure" MyApp

access denied (java.net.SocketPermission server.foobar.com resolve
)
java.lang.Exception: Stack trace
    at java.lang.Thread.dumpStack(Thread.java:1158)
    at java.security.AccessControlContext.checkPermission
                          (AccessControlContext.java:253)
    at java.security.AccessController.checkPermission(AccessController.java:427)
    at java.lang.SecurityManager.checkPermission(SecurityManager.java:532)
    at java.lang.SecurityManager.checkConnect(SecurityManager.java:1031)
    at java.net.InetAddress.getAllByName0(InetAddress.java:1117)
    at java.net.InetAddress.getAllByName0(InetAddress.java:1098)
    at java.net.InetAddress.getAllByName(InetAddress.java:1061)
    at java.net.InetAddress.getByName(InetAddress.java:958)
    at java.net.InetSocketAddress.<init>(InetSocketAddress.java:124)
    at java.net.Socket.<init>(Socket.java:178)
    at MyApp.main(MyApp.java:7)

```

For more information on `java.security.debug` system property, see[Troubleshooting Security](https://docs.oracle.com/javase/8/docs/technotes/guides/security/troubleshooting-security.html) from Java SE Security documentation.



<https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/envvars.html#env_var_sys_prop>

