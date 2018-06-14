## Other Command-Line Options

In addition to the `-XX` options, many other command-line options can provide troubleshooting information. This section describes a few of these options.

### The -Xcheck:jni Option

This option is useful in diagnosing problems with applications that use the Java Native Interface (JNI). Sometimes bugs in the native code can cause the HotSpot VM to crash or behave incorrectly.

The `-Xcheck:jni` option is added to the command line that starts the application, as in the following example:

```
java -Xcheck:jni MyApp

```

The `-Xcheck:jni` option causes the VM to do additional validation on the arguments passed to JNI functions. _Note:_ The option is not guaranteed to find all invalid arguments or diagnose logic bugs in the application code, but it can help diagnose a large number of such problems.

When an invalid argument is detected, the VM prints a message to the application console or to standard output, prints the stack trace of the offending thread, and aborts the VM.

[Example D-3]() shows a `null` value was incorrectly passed to a JNI function that does not allow a `null` value.

> Example D-3 Null Value Passed to JNI Function

```
FATAL ERROR in native method: Null object passed to JNI
    at java.net.PlainSocketImpl.socketAccept(Native Method)
    at java.net.PlainSocketImpl.accept(PlainSocketImpl.java:343)
    - locked <0x450b9f70> (a java.net.PlainSocketImpl)
    at java.net.ServerSocket.implAccept(ServerSocket.java:439)
    at java.net.ServerSocket.accept(ServerSocket.java:410)
    at org.apache.tomcat.service.PoolTcpEndpoint.acceptSocket
                        (PoolTcpEndpoint.java:286)
    at org.apache.tomcat.service.TcpWorkerThread.runIt
                        (PoolTcpEndpoint.java:402)
    at org.apache.tomcat.util.ThreadPool$ControlRunnable.run
                        (ThreadPool.java:498)
    at java.lang.Thread.run(Thread.java:536)

```

[Example D-4]() shows an incorrect argument was provided to a JNI function that expects a `jfieldID` argument.

> Example D-4 Incorrect Argument Provided to a JNI Function

```
FATAL ERROR in native method: Instance field not found in JNI get/set 
                        field operations
        at java.net.PlainSocketImpl.socketBind(Native Method)
        at java.net.PlainSocketImpl.bind(PlainSocketImpl.java:359)
        - locked <0xf082f290> (a java.net.PlainSocketImpl)
        at java.net.ServerSocket.bind(ServerSocket.java:318)
        at java.net.ServerSocket.<init>(ServerSocket.java:185)
        at jvm003a.<init>(jvm003.java:190)
        at jvm003a.<init>(jvm003.java:151)
        at jvm003.run(jvm003.java:51)
        at jvm003.main(jvm003.java:30)

```

The following list presents examples of other problems that the `-Xcheck:jni` option can help diagnose:

* Cases where the JNI environment for the wrong thread is used

* Cases where an invalid JNI reference is used

* Cases where a reference to a non-array type is provided to a function that requires an array type

* Cases where a non-static field ID is provided to a function that expects a static field ID

* Cases where a JNI call is made with an exception pending

In general, all errors detected by the `-Xcheck:jni` option are fatal errors (that is, the error is printed and the VM is aborted). There is one exception to this behavior, when a JNI call is made within a JNI critical region. In this case, the following non-fatal warning message is printed, as shown in[Example D-5]().

> Example D-5 Non-Fatal Warning Message

```
Warning: Calling other JNI functions in the scope of 
Get/ReleasePrimitiveArrayCritical or Get/ReleaseStringCritical

```

A JNI critical region is created when native code uses the JNI functions `GetPrimitiveArrayCritical` or `GetStringCritical` to obtain a reference to an array or string in the Java heap. The reference is held until the native code calls the corresponding release function. The code between the get and release is called a JNI critical section and during that time the HotSpot VM cannot bring the VM to a state that allows garbage collection to occur. The general recommendation is not to use other JNI functions within a JNI critical section, and in particular any JNI function that could potentially cause a deadlock. The warning printed above by the `-Xcheck:jni` option is thus an indication of a potential issue; it does not always indicate an application bug.

For more information on JNI, see the[Java Native Interface](https://docs.oracle.com/javase/8/docs/technotes/guides/jni/index.html) documentation.

### The -verbose:class Option

This option enables logging of class loading and unloading.

### The -verbose:gc Option

This option enables logging of garbage collection (GC) information. It can be combined with other HotSpot VM specific options such as `-XX:+PrintGCDetails` and `-XX:+PrintGCTimeStamps` to get further information about GC. The information output includes the size of the generations before and after each GC, total size of the heap, the size of objects promoted, and the time taken.

More information about these options, along with detailed information about GC analysis and tuning are described in the[GC Portal article](http://www.oracle.com/technetwork/articles/javase/gcportal-136937.html).

The `-verbose:gc` option can be dynamically enabled at runtime using the management API or JVM TI. For more information on these APIs, see [Custom Diagnostic Tools](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/tooldescr021.html).

The JConsole monitoring and management tool can also enable or disable the option when the tool is attached to a management VM. For more information see [JConsole](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/tooldescr009.html).

### The -verbose:jni Option

This option enables logging of JNI. When a JNI or native method is resolved, the HotSpot VM prints a trace message to the application console (standard output). It also prints a trace message when a native method is registered using the JNI `RegisterNative` function. The `-verbose:jni` option can be useful in diagnosing issues with applications that use native libraries.


<https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/clopts002.html>
