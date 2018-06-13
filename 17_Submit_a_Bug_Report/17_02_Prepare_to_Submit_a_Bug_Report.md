## 17.2 Prepare to Submit a Bug Report

Before submitting a bug report, consider the following recommendations:

* **First of all, test with the latest update release to see if the issue persists. Frequently, a bug report submitted for an older release is first suggested to test with the available latest update release or even an available latest EA (Early Access) release. The EA release may contain many new features and bug fixes.**

* Collect as much relevant data as possible. For example, generate a thread-dump in the case of a deadlock, or locate the core file (where applicable) and `hs_err` file in the case of a crash. In every case, it is important to document the environment and the actions performed just before the problem is encountered.

* Where applicable, try to restore the original state and reproduce the problem using the documented steps. This helps to determine if the problem is reproducible or an intermittent issue.

* If the issue is reproducible, try to narrow down the problem. In some cases, a bug can be demonstrated with a small standalone test case. Bugs that are demonstrated by small test cases will typically be easy to diagnose when compared to test cases that consist of a large complex application.

* [Search the bug database](http://bugs.java.com/bugdatabase/index.jsp) to see if this bug or a similar bug has been reported. If the bug has already been reported, the bug report might have further information, such as the following:

  * If the bug has already been fixed, the release in which it was fixed.

  * A workaround for the problem.

  * Comments in the evaluation that explain, in further detail, the circumstances that cause the bug to arise.

* If you conclude that the bug has not already been reported, submit a new bug.

Before submitting a bug, verify that the environment where the problem arises is a supported configuration. See the [Supported System Configurations](http://www.oracle.com/technetwork/java/javase/certconfig-2095354.html).

In addition to the system configurations, check the list of supported locales. See the [Supported Locales](http://www.oracle.com/technetwork/java/javase/java8locales-2095355.html) web page.

In the case of Oracle Solaris, check the recommended patch cluster for the operating system release to ensure that the recommended patches are installed.

<https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/bugreports002.html>
