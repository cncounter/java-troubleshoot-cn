# Appendix C Environment Variables and System Properties

# 附录C环境变量和系统属性

This appendix describes environment variables and system properties that can be useful for troubleshooting problems with the Java HotSpot VM.

本附录描述环境变量和系统属性可以用于故障诊断问题与Java HotSpot VM。

[Submit a Bug Report](https://github.com/cncounter/java-troubleshoot-cn/tree/master/17_Submit_a_Bug_Report/) contains information on collecting environment variables in [Environment Variables](https://github.com/cncounter/java-troubleshoot-cn/tree/master/17_Submit_a_Bug_Report/17_03_Collect_Data_for_a_Bug_Report.md).

提交错误报告(https://github.com/cncounter/java-troubleshoot-cn/tree/master/17_Submit_a_Bug_Report/)包含信息收集环境变量在环境变量(https://github.com/cncounter/java-troubleshoot-cn/tree/master/17_Submit_a_Bug_Report/17_03_Collect_Data_for_a_Bug_Report.md)。

This appendix contains the following sections:

这个附录包含以下部分:

##  The `JAVA_HOME` Environment Variable

##  的`JAVA_HOME`环境变量

This variable `JAVA_HOME` indicates the directory where the Java Development Kit (JDK) software is installed.

这个变量`JAVA_HOME`显示的目录安装Java软件开发工具箱(JDK)。

##  The `JAVA_TOOL_OPTIONS` Environment Variable

##  的`JAVA_TOOL_OPTIONS`环境变量

In many environments the command line is not readily accessible to start the application with necessary command-line options. This often arises with applications that use embedded VMs (meaning they use the Java Native Interface (JNI) Invocation API to start the VM), or where the startup is deeply nested in scripts. In these environments the `JAVA_TOOL_OPTIONS` environment variable can be useful to augment a command line.

在许多环境中不容易操作命令行与必要的命令行选项启动应用程序.这通常发生在使用嵌入式虚拟机的应用程序(这意味着它们使用Java Native Interface(JNI)调用API启动VM),或者启动深深嵌套在脚本.在这些环境中,`JAVA_TOOL_OPTIONS`环境变量可能是有用的,以增加一个命令行。

When this environment variable is set, the `JNI_CreateJavaVM` function (in the JNI Invocation API) prepends the value of the environment variable to the options supplied in its `JavaVMInitArgs` argument.

这个环境变量设置时,`JNI_CreateJavaVM`函数(在JNI调用API)突出显示环境变量的值在其提供的选项`JavaVMInitArgs`论点。

> **Note:**:

> *注:* *:

> In some cases this option is disabled for security reasons (for example, on Oracle Solaris operating system this option is disabled when the effective user or group ID differs from the real ID).

> 因为安全原因在某些情况下,这个选项是禁用的(例如,在Oracle Solaris操作系统这个选项被禁用时有效的用户或组ID不同于真实身份法案)。

This environment variable allows you to specify the initialization of tools, specifically the launching of native or Java programming language agents using the `-agentlib` or `-javaagent` options. In the following example the environment variable is set so that the HPROF profiler is launched when the application is started:

这个环境变量允许您指定初始化的工具,特别推出的本地或Java编程语言代理使用`-agentlib`或`-javaagent`选项。在接下来的例子中设置环境变量,这样HPROF分析器启动应用程序时启动:

```
$ export JAVA_TOOL_OPTIONS="-agentlib:hprof"

```



This variable can also be used to augment the command line with other options for diagnostic purposes. For example, you can supply the `-XX:OnError` option to specify a script or command to be executed when a fatal error occurs.

这个变量也可以用来增强与其他选项的命令行用于诊断目的。例如,您可以提供`-XX:OnError`选项指定一个脚本或命令执行时发生致命错误。

Since this environment variable is examined at the time the `JNI_CreateJavaVM` function is called, it cannot be used to augment the command line with options that would normally be handled by the launcher, for example, VM selection using the `-client` option or the `-server` option.

因为这个环境变量时检查`JNI_CreateJavaVM`函数被调用时,它不能被用来增加的命令行选项通常是由发射器,例如,虚拟机选择使用`-client`选择或`-server`选择。

For more information on `JAVA_TOOL_OPTIONS` environment variable, see Java tool options from[JVM Tool Interface](https://docs.oracle.com/javase/8/docs/platform/jvmti/jvmti.html#tooloptions) documentation.

的更多信息`JAVA_TOOL_OPTIONS`环境变量,看到Java工具选项(JVM工具接口)(https://docs.oracle.com/javase/8/docs/platform/jvmti/jvmti.html # tooloptions)文档。


## The `java.security.debug` System Property

## 的`java.security.debug`系统属性

This system property controls whether the security system of the Java Runtime Environment (JRE) prints trace messages during execution. This option can be useful when diagnosing an issue involving a security manager when a `SecurityException` is thrown.

该系统属性控制的安全系统是否Java运行时环境(JRE)打印在执行期间跟踪消息.这个选项可能是有用的在诊断问题时涉及安全管理器`SecurityException`抛出。

The `java.security.debug` property can have the following values:

的`java.security.debug`房地产可以有以下值:

* `access`

  Print all `checkPermission` results.

打印所有`checkPermission`结果。

  The following additional options can be specified with the `access` option:

以下可以指定附加选项的`access`选择:

  * `stack`

  Include stack trace.

包括堆栈跟踪。

  * `domain`

  Dump all domains in context.


转储所有域上下文。

  * `failure`

  Before throwing an exception, dump the stack and domain that did not have permission.


抛出异常之前,转储堆栈和域,没有权限。

* `jar`

  Print JAR verification information.


打印JAR验证信息。

* `policy`

  Print permissions that `SecureClassLoader` assigns.


打印权限,`SecureClassLoader`分配。

* `scl`

  For example, to print all `checkPermission` results and trace all domains in context, set the `java.security.debug` property to `access,stack`. To trace access failures, set the property to `access,failure`.


例如,打印`checkPermission`结果和跟踪所有域上下文,设置`java.security.debug`财产`access,stack`。跟踪访问失败,设置属性`access,failure`。

> Example C-1 Program for `checkPermission` Failure

> 例颈- 1项目`checkPermission`失败

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

的更多信息`java.security.debug`系统属性,请参见(故障排除安全)(https://docs.oracle.com/javase/8/docs/technotes/guides/security/troubleshooting-security.html)从Java SE安全文档。


<https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/envvars.html#env_var_sys_prop>

