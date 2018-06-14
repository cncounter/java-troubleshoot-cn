# 1. Prepare Java for Troubleshooting

This chapter provides some guidelines for setting up both Java and a Java application for better troubleshooting techniques; in case you run into problems at a later stage. These proactive Java setups help debug and narrow down issues with Java and the application. Not all suggestions apply to every application.

This chapter contains the following sections:

- [Set Up Java for Troubleshooting]()

- [Enable Options/Flags for JVM Troubleshooting]()

- [Gather Relevant Data]()


## 1.1 Set Up Java for Troubleshooting

This section describes setting up the Java environment and command-line options to enable gathering relevant data for troubleshooting. Follow these steps to set up Java.

1. **Update the Java version**: As a first step, use the latest Java version to avoid spending time on troubleshooting issues in Java that have been fixed. Often, a problem caused by a bug in the Java runtime is fixed in the latest update release. Working on the latest Java version helps avoid some known and common issues.

2. **Set up the Java environment to debug**: Consider the following scenarios while setting up a bigger Java application, starting an application with a launcher script, or running distributed Java on several machines.

  - **Make it easy to change the Java version**: Using the latest Java version helps avoid many runtime issues. If your application starts by running a script, make sure that you have to update the Java path in only one place. If you run in a distributed system, think about easy ways to change the Java versions across all of the machines.

  - **Make it easy to change the Java command-line options**: Sometimes while troubleshooting you may want to change Java options; for example, to add a verbose output, to turn off a feature, or to tune Java for better performance. Make sure to prepare the systems for these changes.

  In a Java application that is running remotely, for example in a testing framework or a cloud solution, make sure you can still change the Java flags easily. Sometimes the application takes command-line parameters or you may want to try a flag quickly to reproduce a problem. Prepare the systems to make these changes easy.





<https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/prepapp.html>
