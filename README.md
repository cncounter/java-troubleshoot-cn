# java-troubleshoot-cn

**Java Platform, Standard Edition Troubleshooting Guide**

# Contents

## [Title and Copyright Information](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/title.html)

## [Preface](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/preface.html#sthref2)

*   [Audience](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/preface.html#sthref3)
*   [Documentation Accessibility](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/preface.html#sthref4)
*   [Related Documents](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/preface.html#sthref6)
*   [Conventions](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/preface.html#sthref7)

## [Part I General Java Troubleshooting](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/generalts.html#sthref8)

## [1 Prepare Java for Troubleshooting](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/prepapp.html#prepare_java_troubleshooting)

*   [1.1 Set Up Java for Troubleshooting](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/prepapp001.html#CEGGCHFI)
*   [1.2 Enable Options/Flags for JVM Troubleshooting](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/prepapp002.html#CEGBHDFH)
*   [1.3 Gather Relevant Data](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/prepapp003.html#CEGHACDF)

    *   [1.3.1 Make a Java Application Easier to Debug](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/prepapp003.html#sthref9)

## [2 Diagnostic Tools](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/tooldescr.html#diagnostic_tools)

*   [2.1 Diagnostic Tools Overview](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/tooldescr001.html#BABCBIDC)
*   [2.2 Java Mission Control](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/tooldescr002.html#BABIBBDE)

    *   [2.2.1 Troubleshoot with Java Mission Control](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/tooldescr002.html#BABDCBGE)

*   [2.3 What are Java Flight Recordings](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/tooldescr003.html#BABFDCDA)

    *   [2.3.1 Types of Recordings](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/tooldescr003.html#BABGIHBB)

*   [2.4 How to Produce a Flight Recording](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/tooldescr004.html#BABJJEEE)

    *   [2.4.1 Use Java Mission Control to Produce a Flight Recording](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/tooldescr004.html#BABJCJDB)
    *   [2.4.2 Use Startup Flags at the Command Line to Produce a Flight Recording](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/tooldescr004.html#BABHCDEA)
    *   [2.4.3 Use Triggers for Automatic Recordings](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/tooldescr004.html#BABDIGFA)

*   [2.5 Inspect a Flight Recording](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/tooldescr005.html#BABBBBIC)

    *   [2.5.1 How to Get a Sample JFR to Inspect](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/tooldescr005.html#BABCAJCG)
    *   [2.5.2 Range Navigator](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/tooldescr005.html#BABGEGAA)
    *   [2.5.3 General Tab](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/tooldescr005.html#BABHBFBC)
    *   [2.5.4 Memory Tab](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/tooldescr005.html#BABHFCDD)
    *   [2.5.5 Code Tab](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/tooldescr005.html#BABEFGIF)
    *   [2.5.6 Threads Tab](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/tooldescr005.html#BABGIJAF)
    *   [2.5.7 I/O Tab](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/tooldescr005.html#BABEHFCB)
    *   [2.5.8 System Tab](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/tooldescr005.html#BABCIABB)
    *   [2.5.9 Events Tab](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/tooldescr005.html#BABDGDGB)

*   [2.6 The jcmd Utility](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/tooldescr006.html#BABEHABG)

    *   [2.6.1 Useful Commands for jcmd Utility](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/tooldescr006.html#BABEJDGE)
    *   [2.6.2 Troubleshoot with jcmd Utility](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/tooldescr006.html#BABFFIFA)

*   [2.7 Native Memory Tracking](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/tooldescr007.html#BABGFCDA)

    *   [2.7.1 Use NMT to Detect a Memory Leak](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/tooldescr007.html#BABIIIAC)
    *   [2.7.2 How to Monitor VM Internal Memory](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/tooldescr007.html#BABJGHDB)

*   [2.8 HPROF](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/tooldescr008.html#BABGIIGB)

    *   [2.8.1 Troubleshoot with HPROF Tool](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/tooldescr008.html#BABIDBJJ)
    *   [2.8.2 Heap Allocation Profile heap=sites](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/tooldescr008.html#BABGFJFJ)
    *   [2.8.3 Heap Dump Profile heap=dump](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/tooldescr008.html#BABDFAGH)
    *   [2.8.4 CPU Usage Sampling Profile cpu=samples](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/tooldescr008.html#BABHIDGJ)
    *   [2.8.5 CPU Usage Times Profile cpu=times](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/tooldescr008.html#BABIJFIG)

*   [2.9 JConsole](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/tooldescr009.html#BABDCICF)

    *   [2.9.1 Troubleshoot with JConsole Tool](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/tooldescr009.html#BABECDDF)
    *   [2.9.2 Monitor Local and Remote Applications with JConsole](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/tooldescr009.html#BABIGBJA)

*   [2.10 Java VisualVM](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/tooldescr010.html#BABEEIFH)

    *   [2.10.1 Troubleshoot with Java VisualVM](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/tooldescr010.html#BABFIBEC)

*   [2.11 The jdb Utility](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/tooldescr011.html#BABDHAHJ)

    *   [2.11.1 Troubleshoot with jdb Utility](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/tooldescr011.html#BABGIEHH)
    *   [2.11.2 Attach a Process](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/tooldescr011.html#BABFHHEE)
    *   [2.11.3 Attach to a Core File on the Same Machine](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/tooldescr011.html#BABDJAAE)
    *   [2.11.4 Attach to a Core File or a Hung Process from a Different Machine](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/tooldescr011.html#BABHCJEE)

*   [2.12 The jhat Utility](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/tooldescr012.html#BABJGJBI)

    *   [2.12.1 Troubleshoot with jhat Utility](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/tooldescr012.html#BABJIEHJ)
    *   [2.12.2 Standard Queries](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/tooldescr012.html#BABJFDGC)
    *   [2.12.3 Custom Queries](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/tooldescr012.html#BABBGGIB)
    *   [2.12.4 Heap Analysis Hints](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/tooldescr012.html#BABDFACD)

*   [2.13 The jinfo Utility](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/tooldescr013.html#BABDHFBE)

    *   [2.13.1 Troubleshooting with jinfo Utility](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/tooldescr013.html#BABGIAAI)

*   [2.14 The jmap Utility](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/tooldescr014.html#BABGAFEG)

    *   [2.14.1 Heap Configuration and Usage](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/tooldescr014.html#BABJDAJB)
    *   [2.14.2 Heap Histogram](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/tooldescr014.html#BABJIIHH)
    *   [2.14.3 Permanent Generation Statistics](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/tooldescr014.html#BABBEBHH)

*   [2.15 The jps Utility](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/tooldescr015.html#BABHCEDC)
*   [2.16 The jstack Utility](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/tooldescr016.html#BABFCHDE)

    *   [2.16.1 Troubleshoot with jstack Utility](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/tooldescr016.html#BABEHDDH)
    *   [2.16.2 Force a Stack Dump](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/tooldescr016.html#BABFDFDH)
    *   [2.16.3 Stack Trace from a Core Dump](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/tooldescr016.html#BABBAIJC)
    *   [2.16.4 Mixed Stack](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/tooldescr016.html#BABJBDFC)

*   [2.17 The jstat Utility](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/tooldescr017.html#BABCDBEA)
*   [2.18 The visualgc Tool](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/tooldescr018.html#BABCDEBE)
*   [2.19 Control+Break Handler](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/tooldescr019.html#BABCDJFE)

    *   [2.19.1 Thread Dump](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/tooldescr019.html#BABBEFFC)
    *   [2.19.2 Detect Deadlocks](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/tooldescr019.html#BABGJGFD)
    *   [2.19.3 Heap Summary](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/tooldescr019.html#BABGEDCB)

*   [2.20 Native Operating System Tools](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/tooldescr020.html#BABBHHIE)

    *   [2.20.1 DTrace Tool](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/tooldescr020.html#BABDBCIC)
    *   [2.20.2 Probe Providers in Java HotSpot VM](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/tooldescr020.html#BABFIGEG)
    *   [2.20.3 Improvements to pmap Tool](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/tooldescr020.html#BABFIBHG)
    *   [2.20.4 Improvements to pstack Tool](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/tooldescr020.html#BABIBFFF)

*   [2.21 Custom Diagnostic Tools](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/tooldescr021.html#BABEDEBD)

    *   [2.21.1 Java Platform Debugger Architecture](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/tooldescr021.html#BABFAGDH)

*   [NMT Memory Categories](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/tooldescr022.html#BABCBGFA)
*   [Postmortem Diagnostics Tools](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/tooldescr023.html#BABEFHCI)
*   [Hung Processes Tools](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/tooldescr024.html#BABHGAEE)
*   [Monitoring Tools](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/tooldescr025.html#BABFCEEB)
*   [Other Tools, Options, Variables and Properties](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/tooldescr026.html#BABHGADF)
*   [The java.lang.management Package](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/tooldescr027.html#BABGIADG)
*   [The java.lang.instrument Package](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/tooldescr028.html#BABJBFCD)
*   [The java.lang.Thread Class](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/tooldescr029.html#BABHJEII)
*   [JVM Tool Interface](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/tooldescr030.html#BABDJEIA)
*   [The jrunscript Utility](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/tooldescr031.html#BABEBHFB)
*   [The jsadebugd Daemon](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/tooldescr032.html#CJGCCECD)
*   [The jstatd Daemon](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/tooldescr033.html#CJGHGBFD)
*   [Thread States for a Thread Dump](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/tooldescr034.html#sthref31)
*   [Troubleshooting Tools Based on Operating System](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/tooldescr035.html#BABFIBGE)

## [3 Troubleshoot Memory Leaks](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/memleaks.html#CIHGFAEG)

*   [3.1 Debug a Memory Leak Using Java Flight Recorder](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/memleaks001.html#CIHCAEIH)

    *   [3.1.1 Detect a Memory Leak](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/memleaks001.html#CIHCIEFF)
    *   [3.1.2 Find the Leaking Class](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/memleaks001.html#CIHHGDJH)
    *   [3.1.3 Find the Leak](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/memleaks001.html#CIHDBIFJ)

*   [3.2 Understand the OutOfMemoryError Exception](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/memleaks002.html#CIHHJDJE)
*   [3.3 Troubleshoot a Crash Instead of OutOfMemoryError](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/memleaks003.html#CIHDBHFB)
*   [3.4 Diagnose Leaks in Java Language Code](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/memleaks004.html#CIHIEEFH)

    *   [3.4.1 Create a Heap Dump](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/memleaks004.html#CIHJIIBA)
    *   [3.4.2 Obtain a Heap Histogram](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/memleaks004.html#CIHBDBHJ)
    *   [3.4.3 Monitor the Objects Pending Finalization](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/memleaks004.html#CIHCDBJB)

*   [3.5 Diagnose Leaks in Native Code](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/memleaks005.html#sthref46)

    *   [3.5.1 Track All Memory Allocation and Free Calls](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/memleaks005.html#CIHGHAHF)
    *   [3.5.2 Track All Memory Allocations in JNI Library](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/memleaks005.html#CIHDEEHJ)
    *   [3.5.3 Track Memory Allocation with Operating System Support](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/memleaks005.html#CIHFGCIB)
    *   [3.5.4 Find Leaks with dbx Debugger](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/memleaks005.html#CIHJCBGJ)
    *   [3.5.5 Find Leaks with libumem Tool](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/memleaks005.html#CIHEHJAG)

## [4 Troubleshoot Performance Issues Using JFR](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/performissues.html#troubleshoot_performance_issues)

*   [4.1 JFR Overhead](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/performissues001.html#CJAJBHGF)
*   [4.2 Find Bottlenecks](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/performissues002.html#CJAGIGEH)
*   [4.3 Garbage Collection Performance](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/performissues003.html#CJABBEGB)
*   [4.4 Synchronization Performance](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/performissues004.html#CJAHEGCC)
*   [4.5 I/O Performance](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/performissues005.html#CJAIGBJH)
*   [4.6 Code Execution Performance](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/performissues006.html#CJACFHEC)

## [Part II Debug JVM Issues](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/jvmts.html#sthref53)

## [5 Troubleshoot System Crashes](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/crashes.html#system_crashes)

*   [5.1 Determine Where the Crash Occurred](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/crashes001.html#CIHJABGA)

    *   [5.1.1 Crash in Native Code](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/crashes001.html#CIHBECGA)
    *   [5.1.2 Crash in Compiled Code](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/crashes001.html#CIHDEIGG)
    *   [5.1.3 Crash in HotSpot Compiler Thread](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/crashes001.html#CIHDDHCI)
    *   [5.1.4 Crash in VM Thread](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/crashes001.html#CIHDJEAE)
    *   [5.1.5 Crash Due to Stack Overflow](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/crashes001.html#CIHDGFJA)

*   [5.2 Find a Workaround](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/crashes002.html#CIHCDFJA)

    *   [5.2.1 Working Around Crashes in the HotSpot Compiler Thread or Compiled Code](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/crashes002.html#CIHDIBJA)
    *   [5.2.2 Working Around Crashes during Garbage Collection](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/crashes002.html#CIHEEBDG)
    *   [5.2.3 Working Around Crashes Caused by Class Data Sharing](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/crashes002.html#CIHJJFAH)

*   [5.3 Microsoft Visual C++ Version Considerations](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/crashes003.html#CIHBJAEI)

## [6 Troubleshoot Process Hangs and Loops](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/hangloop.html#CEGCAAHA)

*   [6.1 Diagnose a Loop Process](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/hangloop001.html#CEGEBFAB)
*   [6.2 Diagnose a Hung Process](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/hangloop002.html#CEGBIFFE)

    *   [6.2.1 Deadlock Detected](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/hangloop002.html#CEGHEEDD)
    *   [6.2.2 Deadlock Not Detected](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/hangloop002.html#CEGEHBFI)
    *   [6.2.3 No Thread Dump](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/hangloop002.html#CEGHHHCB)

*   [6.3 Oracle Solaris 8 Thread Library](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/hangloop003.html#CEGDGDIG)

## [7 Handle Signals and Exceptions](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/signals.html#BABIFHBI)

*   [7.1 Handle Signals on Oracle Solaris and Linux](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/signals001.html#CIHBBDED)
*   [7.2 Handle Exceptions on Windows](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/signals002.html#CIHFFEDF)
*   [7.3 Signal Chaining](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/signals003.html#CIHFCAIG)
*   [7.4 Handle Exceptions using Java HotSpot VM](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/signals004.html#CIHEDDDJ)
*   [Console Handlers](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/signals005.html#CIHHGHBB)
*   [Signals Used in Oracle Solaris and Linux](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/signals006.html#sthref55)

## [Part III Debug Core Library Issues](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/clibissues.html#sthref57)

## [8 Time Zone Settings in the JRE](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/time-zone.html#CBBDFAJI)

*   [8.1 Native Time Zone Information and the JRE](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/time-zone001.html#CBBIEBDG)

    *   [8.1.1 Determine the Time Zone Data Version in Use](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/time-zone001.html#CBBHHBBG)
    *   [8.1.2 Troubleshoot Problems with TZupdater](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/time-zone001.html#CBBFFAHG)

*   [8.2 Determine the Default Time Zone on Windows](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/time-zone002.html#CBBBDIGD)

    *   [8.2.1 Check the Default Time Zone JRE Reports](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/time-zone002.html#CBBBCIHB)
    *   [8.2.2 Determine the Setting in the Control Panel](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/time-zone002.html#CBBHGCAE)
    *   [8.2.3 Check for Automatic Daylight Saving Time Adjustment](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/time-zone002.html#CBBBHDHH)
    *   [8.2.4 Set the Default Time Zone in the Control Panel](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/time-zone002.html#CBBEHDGF)
    *   [8.2.5 Check -Duser.timezone System Property](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/time-zone002.html#CBBGIFJF)
    *   [8.2.6 Special Tools in Windows 7](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/time-zone002.html#CBBFABAH)
    *   [8.2.7 JRE Internal Representation of Time Zone Mappings](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/time-zone002.html#CBBCCFCD)

## [Part IV Debug Client Issues](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/clientissue.html#sthref58)

## [9 Introduction to Client Issues](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/introclientissues.html#CJAHHJGC)

*   [9.1 Java SE Desktop Technologies](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/introclientissues001.html#BCFBAEGB)
*   [9.2 General Steps to Troubleshoot an Issue](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/introclientissues002.html#BCFJCAJA)
*   [9.3 Identify the Type of Issue](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/introclientissues003.html#BCFCJDBC)

    *   [9.3.1 Java Client Crashes](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/introclientissues003.html#BCFJICFD)
    *   [9.3.2 Performance Problems](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/introclientissues003.html#BCFGIJDH)
    *   [9.3.3 Behavior Problems](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/introclientissues003.html#BCFGDJCB)

*   [9.4 Basic Tools](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/introclientissues004.html#BCFDIDCI)
*   [9.5 JDWP](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/introclientissues005.html#BCFDCIHE)

## [10 AWT](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/awt.html#CHDHIJJA)

*   [10.1 Debug Tips for AWT](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/awt001.html#CIHGAAFA)
*   [10.2 Layout Manager Issues](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/awt002.html#CIHDEDEA)
*   [10.3 Key Events](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/awt003.html#CIHJCADB)
*   [10.4 Modality Issues](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/awt004.html#CIHBFJIH)
*   [10.5 Memory Leaks](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/awt005.html#CIHCIDEJ)
*   [10.6 AWT Crashes](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/awt006.html#CIHDCHGE)
*   [10.7 Focus Events](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/awt007.html#CIHJFGGC)

    *   [10.7.1 How to Trace Focus Events](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/awt007.html#CIHHICIF)
    *   [10.7.2 Native Focus System](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/awt007.html#CIHDEDIG)
    *   [10.7.3 Focus System in Java Plug-in](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/awt007.html#CIHFAICA)
    *   [10.7.4 Focus Models Supported by X Window Managers](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/awt007.html#CIHEADEF)
    *   [10.7.5 Miscellaneous Problems with Focus](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/awt007.html#CIHHGJGF)

*   [10.8 Data Transfer](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/awt008.html#CIHBHGGE)

    *   [10.8.1 Debug Drag and Drop Applications](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/awt008.html#CIHDEEDD)
    *   [10.8.2 Frequent Issues with Data Transfer](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/awt008.html#CIHJEIIE)

*   [10.9 Other Issues](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/awt009.html#CIHGABIC)

    *   [10.9.1 Splash Screen Issues](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/awt009.html#CIHCCCGE)
    *   [10.9.2 Tray Icon Issues](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/awt009.html#CIHGJEAH)
    *   [10.9.3 Popup Menu Issues](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/awt009.html#CIHBJCHD)
    *   [10.9.4 Background/Foreground Color Inheritance](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/awt009.html#CIHHBIFG)
    *   [10.9.5 AWT Panel Size Restriction](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/awt009.html#CIHIJIJJ)
    *   [10.9.6 Hangs during Debugging Popup Menus and Similar Components on X11](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/awt009.html#CIHBAEEA)
    *   [10.9.7 Window.toFront()/toBack() Behavior on X11](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/awt009.html#CIHEBHBD)

*   [10.10 Heavyweight/Lightweight Components Mix](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/awt010.html#CIHEFCCB)

## [11 Java 2D Pipeline Rendering and Properties](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/java2dpipeline.html#java2d_pipeline)

*   [11.1 Oracle Solaris and Linux: X11 Pipeline](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/java2dpipeline001.html#BABEGFED)

    *   [11.1.1 X11 Pipeline Pixmaps Properties](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/java2dpipeline001.html#BABICHDA)
    *   [11.1.2 X11 Pipeline MIT Shared Memory Extension](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/java2dpipeline001.html#BABGGBIG)
    *   [11.1.3 Oracle Solaris on SPARC: DGA Support](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/java2dpipeline001.html#BABEEBEA)
    *   [11.1.4 Oracle Solaris on SPARC - Change Java 2D Default Visual](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/java2dpipeline001.html#BABBCDJJ)

*   [11.2 Windows OS - DirectDraw/GDI Pipeline](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/java2dpipeline002.html#BABDDDEI)
*   [11.3 Windows OS - Direct3D Pipeline in Full-Screen Mode](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/java2dpipeline003.html#BABJJHIF)
*   [11.4 OpenGL Pipeline in Oracle Solaris, Linux and Windows](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/java2dpipeline004.html#BABGIIHI)

    *   [11.4.1 Enable OpenGL Pipeline](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/java2dpipeline004.html#BABGGJEJ)
    *   [11.4.2 Minimum Requirements](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/java2dpipeline004.html#BABJEJED)
    *   [11.4.3 Diagnose Startup Issues](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/java2dpipeline004.html#BABDFFCD)
    *   [11.4.4 Diagnose Rendering and Performance Issues](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/java2dpipeline004.html#BABGFFIJ)

*   [Latest OpenGL Drivers](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/java2dpipeline005.html#BABBFJCG)

## [12 Java 2D](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/java2d.html#BABCFGDC)

*   [12.1 Generic Performance Issues](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/java2d001.html#BABIIFAE)

    *   [12.1.1 Hardware Accelerated Rendering Primitives](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/java2d001.html#BABGAIBI)
    *   [12.1.2 Primitive Tracing to Detect and Avoid Non-accelerated Rendering](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/java2d001.html#BABBBCEG)
    *   [12.1.3 Causes of Poor Rendering Performance](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/java2d001.html#BABHAAHE)
    *   [12.1.4 Improve Performance of Software-only Rendering](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/java2d001.html#BABJHBGE)

*   [12.2 Text Related Issues](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/java2d002.html#BABDGCHB)

    *   [12.2.1 Application Crash During Text Rendering](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/java2d002.html#BABFIDCA)
    *   [12.2.2 Differences in Text Appearance](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/java2d002.html#BABGDGJA)
    *   [12.2.3 Metrics](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/java2d002.html#BABJFBHE)

*   [12.3 Java 2D Printing](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/java2d003.html#BABFGDII)

## [13 Swing](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/swing.html#BCGIFCAI)

*   [13.1 General Debug Tips for Swing](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/swing001.html#BABGCDBF)
*   [13.2 Specific Debug Tips for Swing](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/swing002.html#BABDDAJI)

    *   [13.2.1 Incorrect Threading](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/swing002.html#BABGDJEG)
    *   [13.2.2 JComponent Children Overlap](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/swing002.html#BABFEABI)
    *   [13.2.3 Display Update](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/swing002.html#BABHEADA)
    *   [13.2.4 Model Change](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/swing002.html#BABFGCHB)
    *   [13.2.5 Add or Remove Components](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/swing002.html#BABGIFGG)
    *   [13.2.6 Opaque Override](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/swing002.html#BABFDIFA)
    *   [13.2.7 Permanent Changes to Graphics](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/swing002.html#BABEFFDH)
    *   [13.2.8 Custom Painting and Double Buffering](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/swing002.html#BABFGIBJ)
    *   [13.2.9 Opaque Content Pane](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/swing002.html#BABHJGAH)
    *   [13.2.10 Renderer Call for Each Cell Performance](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/swing002.html#BABBBGBI)
    *   [13.2.11 Possible Leaks](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/swing002.html#BABEHFIE)
    *   [13.2.12 Mix Heavywight and Lightweight Components](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/swing002.html#BABHEGAD)
    *   [13.2.13 Use Synth](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/swing002.html#BABGAFFC)
    *   [13.2.14 Track Activity on Event Dispatch Thread](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/swing002.html#BABEBJDF)
    *   [13.2.15 Specify Default Layout Manager](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/swing002.html#BABBJDCE)
    *   [13.2.16 Listener Object Dispatched to Incorrect Component](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/swing002.html#BABJJJDJ)
    *   [13.2.17 Add a Component to Content Pane](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/swing002.html#BABECFFH)
    *   [13.2.18 Drag and Drop Support](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/swing002.html#BABCHDJI)
    *   [13.2.19 One Parent for a Component](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/swing002.html#BABCCFFD)
    *   [13.2.20 JFileChooser Issues with Windows Shortcuts](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/swing002.html#BABEDBIA)

## [14 Internationalization](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/i18n.html#CACGHJIC)

*   [14.1 Troubleshoot Internationalization and Localization](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/i18n001.html#CJHEECHH)

## [15 Java Sound](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/sound.html#BEICEEFI)

*   [15.1 Troubleshoot Java Sound Issues](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/sound001.html#BEBBEEJE)

## [16 Applets and Java Web Start Applications](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/plugin.html#BABDHAFC)

*   [16.1 Configuration Problems](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/plugin001.html#BABEIICJ)

    *   [16.1.1 Validation](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/plugin001.html#BABGEBFB)
    *   [16.1.2 Common Configuration Problems](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/plugin001.html#BABDCJCH)
    *   [16.1.3 Manage Java Runtime](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/plugin001.html#BABGCFIE)
    *   [16.1.4 Pass Parameters to the JRE](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/plugin001.html#BABDCIAF)
    *   [16.1.5 Java Deployment Home](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/plugin001.html#BABHHDGA)
    *   [16.1.6 Deployment Tracing](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/plugin001.html#BABDCDHH)
    *   [16.1.7 Deployment Cache](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/plugin001.html#BABFHBEC)
    *   [16.1.8 Network Configuration](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/plugin001.html#BABCFJBF)

*   [16.2 Troubleshoot Applets](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/plugin002.html#BABCFFHE)

    *   [16.2.1 Plugin Cheat Sheet for Applet Start](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/plugin002.html#BABIDCCF)
    *   [16.2.2 Browser or Java Process Crash](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/plugin002.html#BABDIDHB)
    *   [16.2.3 Unresponsive Web page](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/plugin002.html#BABFEGJJ)

*   [16.3 Avoid Security Dialogs](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/plugin003.html#BABBAEFA)

    *   [16.3.1 Signed Applications](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/plugin003.html#BABBHCBF)
    *   [16.3.2 Mixed Code Issues](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/plugin003.html#BABGIAIB)

*   [16.4 Development Tips](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/plugin004.html#BABEFGDI)

## [Part V Submit Bug Reports](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/submitreport.html#sthref66)

## [17 Submit a Bug Report](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/bugreports.html#submit_a_bug_report_tsg)

*   [17.1 Check for Fixes in Update Releases](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/bugreports001.html#CHDEGGIG)
*   [17.2 Prepare to Submit a Bug Report](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/bugreports002.html#CHDBFAEE)
*   [17.3 Collect Data for a Bug Report](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/bugreports003.html#CHDCAAAD)

    *   [17.3.1 Hardware Details](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/bugreports003.html#CHDJBIJA)
    *   [17.3.2 Operating System Details](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/bugreports003.html#CHDFDCGD)
    *   [17.3.3 Java SE Version](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/bugreports003.html#CHDIIIHH)
    *   [17.3.4 Command-Line Options](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/bugreports003.html#CHDGAHDH)
    *   [17.3.5 Environment Variables](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/bugreports003.html#CHDHHHBJ)
    *   [17.3.6 Fatal Error Log](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/bugreports003.html#CHDBIACE)
    *   [17.3.7 Core or Crash Dump](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/bugreports003.html#CHDIGIHE)
    *   [17.3.8 Detailed Description of the Problem](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/bugreports003.html#CHDCCAHH)
    *   [17.3.9 Logs and Traces](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/bugreports003.html#CHDCACIH)
    *   [17.3.10 Results from Troubleshooting Steps](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/bugreports003.html#CHDFJFFG)

*   [17.4 Collect Core Dumps](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/bugreports004.html#CHDJJAJE)

    *   [17.4.1 Collect Core Dumps on Oracle Solaris](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/bugreports004.html#CHDIEHDJ)
    *   [17.4.2 Collect Core Dumps on Linux](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/bugreports004.html#CHDHDCJD)
    *   [17.4.3 Reasons for Not Getting a Core File](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/bugreports004.html#CHDGGGCH)
    *   [17.4.4 Collect Crash Dumps on Windows](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/bugreports004.html#CHDHIHBJ)

## [Part VI Appendix](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/appendix.html#sthref67)

## [A Fatal Error Log](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/felog.html#fatal_error_log_vm)

*   [Location of Fatal Error Log](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/felog001.html#BABIDHJC)
*   [Description of Fatal Error Log](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/felog002.html#BABDFGEB)
*   [Header Format](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/felog003.html#BABFFJBB)
*   [Thread Section Format](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/felog004.html#BABFIIJH)
*   [Process Section Format](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/felog005.html#BABIBEJD)
*   [System Section Format](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/felog006.html#BABFJBCC)

## [B Java 2D Properties](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/java2d-props.html#CIHDJJDF)

*   [Properties on Oracle Solaris and Linux](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/java2d-props001.html#CIHEHDHD)
*   [Properties on Windows](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/java2d-props002.html#CIHJDJHI)

## [C Environment Variables and System Properties](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/envvars.html#env_var_sys_prop)

*   [The `JAVA_HOME` Environment Variable](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/envvars001.html#CIHEEHEI)
*   [The `JAVA_TOOL_OPTIONS` Environment Variable](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/envvars002.html#CIHDGJHI)
*   [The `java.security.debug` System Property](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/envvars003.html#CIHDAFDD)

## [D Command-Line Options](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/clopts.html#BABGEHCF)

*   [Java HotSpot VM Command-Line Options](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/clopts001.html#CHDJEIHC)
*   [Other Command-Line Options](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/clopts002.html#CHDHCBBG)

## [E Summary of Tools in This Release](https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/tools-by-rel.html#CIHDAHBJ)




















https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/toc.html
