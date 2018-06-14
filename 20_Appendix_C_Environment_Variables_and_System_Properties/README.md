# Appendix C Environment Variables and System Properties

# 附录C. 环境变量与系统属性

This appendix describes environment variables and system properties that can be useful for troubleshooting problems with the Java HotSpot VM.

附录C主要介绍 Java HotSpot VM 故障诊断相关的 环境变量(Environment Variables) 和 系统属性(System Properties)

[Submit a Bug Report](https://github.com/cncounter/java-troubleshoot-cn/tree/master/17_Submit_a_Bug_Report/) contains information on collecting environment variables in [Environment Variables](https://github.com/cncounter/java-troubleshoot-cn/tree/master/17_Submit_a_Bug_Report/17_03_Collect_Data_for_a_Bug_Report.md).

[提交错误报告](https://github.com/cncounter/java-troubleshoot-cn/tree/master/17_Submit_a_Bug_Report/) 时, 需要包含 [环境变量](https://github.com/cncounter/java-troubleshoot-cn/tree/master/17_Submit_a_Bug_Report/17_03_Collect_Data_for_a_Bug_Report.md) 中相关的信息。

This appendix contains the following sections:

包含以下部分:


##  The `JAVA_HOME` Environment Variable

##  `JAVA_HOME` 环境变量

This variable `JAVA_HOME` indicates the directory where the Java Development Kit (JDK) software is installed.

`JAVA_HOME` 环境变量用于指明 Java Development Kit (JDK) 的安装目录。


##  The `JAVA_TOOL_OPTIONS` Environment Variable

##  `JAVA_TOOL_OPTIONS` 环境变量

In many environments the command line is not readily accessible to start the application with necessary command-line options. This often arises with applications that use embedded VMs (meaning they use the Java Native Interface (JNI) Invocation API to start the VM), or where the startup is deeply nested in scripts. In these environments the `JAVA_TOOL_OPTIONS` environment variable can be useful to augment a command line.

有些情况下, 不方便使用命令行参数来启动应用程序. 例如嵌入式的虚拟机(embedded VM, 也就是通过 Java Native Interface(JNI) Invocation API 来启动JVM), 或者是深度嵌套在别的脚本中的启动命令. 这时候, 在命令行中增加  `JAVA_TOOL_OPTIONS` 环境变量可能会很有用。

When this environment variable is set, the `JNI_CreateJavaVM` function (in the JNI Invocation API) prepends the value of the environment variable to the options supplied in its `JavaVMInitArgs` argument.

设置了这个环境变量之后, JNI Invocation API 中的 `JNI_CreateJavaVM` 函数就会将这个环境变量值包含在 `JavaVMInitArgs` 参数中。

> **Note:**

> **注:**

> In some cases this option is disabled for security reasons (for example, on Oracle Solaris operating system this option is disabled when the effective user or group ID differs from the real ID).

> 在某些情况下可能会因为安全原因, 将这个选项禁用。 例如, 在 Oracle Solaris 操作系统中, 如果有效的用户或者组ID与真实的ID不同, 这个选项就会被自动禁用。

This environment variable allows you to specify the initialization of tools, specifically the launching of native or Java programming language agents using the `-agentlib` or `-javaagent` options. In the following example the environment variable is set so that the HPROF profiler is launched when the application is started:

这个环境变量可以控制指定工具的初始化, 特别是 `-agentlib` 或者 `-javaagent` 选项。 在下面的例子中, 设置了这个环境变量, 在应用程序启动时, 就会自动加载 HPROF 分析器:

```
$ export JAVA_TOOL_OPTIONS="-agentlib:hprof"

```


This variable can also be used to augment the command line with other options for diagnostic purposes. For example, you can supply the `-XX:OnError` option to specify a script or command to be executed when a fatal error occurs.

这个变量也可以配置其他的值, 用来辅助问题排查和诊断。 例如, 设置 `-XX:OnError` 选项, 来指定发生致命错误时执行时钩子脚本/命令。

Since this environment variable is examined at the time the `JNI_CreateJavaVM` function is called, it cannot be used to augment the command line with options that would normally be handled by the launcher, for example, VM selection using the `-client` option or the `-server` option.

只有在调用 `JNI_CreateJavaVM` 函数时才会检查这个环境变量, 所以不能包含常规启动程序所使用的命令行选项, 例如, 选择具体虚拟机的 `-client` 或者 `-server` 等选项。

=====

For more information on `JAVA_TOOL_OPTIONS` environment variable, see Java tool options from[JVM Tool Interface](https://docs.oracle.com/javase/8/docs/platform/jvmti/jvmti.html#tooloptions) documentation.

更多 `JAVA_TOOL_OPTIONS` 环境变量相关的信息, 请参考 [JVM Tool Interface](https://docs.oracle.com/javase/8/docs/platform/jvmti/jvmti.html#tooloptions) 文档中的 Java tool options 部分。


## The `java.security.debug` System Property

## `java.security.debug` 系统属性

This system property controls whether the security system of the Java Runtime Environment (JRE) prints trace messages during execution. This option can be useful when diagnosing an issue involving a security manager when a `SecurityException` is thrown.

系统属性 `java.security.debug`  用于控制 JRE 的安全系统在执行过程中是否打印跟踪消息(trace message). 在抛出 `SecurityException` 时, 通过这个选项来辅助排查安全管理器(security manager), 可能会很有用。

The `java.security.debug` property can have the following values:

`java.security.debug` 属性的值可以有:

* `access`

  Print all `checkPermission` results.

  打印所有的 `checkPermission` 结果。

  The following additional options can be specified with the `access` option:

  还可以在`access`选项后面附加以下子选项:

  * `stack`

  Include stack trace.

  包括调用栈跟踪(stack trace)。

  * `domain`

  Dump all domains in context.

  导出上下文中的所有域(domain)。

  * `failure`

  Before throwing an exception, dump the stack and domain that did not have permission.

  在抛出异常之前,转储没有权限的调用栈和域。

* `jar`

  Print JAR verification information.

  打印JAR验证信息。

* `policy`

  Print permissions that `SecureClassLoader` assigns.

  打印 `SecureClassLoader` 分配的权限。

* `scl`

  For example, to print all `checkPermission` results and trace all domains in context, set the `java.security.debug` property to `access,stack`. To trace access failures, set the property to `access,failure`.


  例如, 要打印所有 `checkPermission` 的结果, 以及跟踪上下文中的所有域, 可以设置 `java.security.debug` 属性为 `access,stack`。 如果要追踪(方法)访问失败, 设置属性值为 `access,failure`。

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

关于 `java.security.debug` 系统属性的详细信息, 请参考 Java SE 安全文档中的 [Troubleshooting Security](https://docs.oracle.com/javase/8/docs/technotes/guides/security/troubleshooting-security.html)。


<https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/envvars.html#env_var_sys_prop>

