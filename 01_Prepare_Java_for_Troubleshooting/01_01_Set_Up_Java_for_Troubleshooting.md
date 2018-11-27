## 1.1 Set Up Java for Troubleshooting

## 1.1 Java问题排查设置

This section describes setting up the Java environment and command-line options to enable gathering relevant data for troubleshooting. Follow these steps to set up Java.

本节讲述如何设置Java环境,以及相应的命令行选项, 进行相关的数据采集, 以支持问题排查。 请按照以下步骤设置Java。

1. Update the Java version: As a first step, use the latest Java version to avoid spending time on troubleshooting issues in Java that have been fixed. Often, a problem caused by a bug in the Java runtime is fixed in the latest update release. Working on the latest Java version helps avoid some known and common issues.

1. 升级JDK版本: 首先, 使用最新的JDK版本, 以免碰到那些已经修复的BUG. 通常来说, 在Java运行时中复现的BUG, 最新版的JDK中都已经修复了。这能避开已知/常见的问题。

2. Set up the Java environment to debug: Consider the following scenarios while setting up a bigger Java application, starting an application with a launcher script, or running distributed Java on several machines.

2. 设置调试Java环境:考虑以下场景而建立一个更大的Java应用程序,应用程序开始启动脚本,或分布式运行Java在几个机器。

  - Make it easy to change the Java version: Using the latest Java version helps avoid many runtime issues. If your application starts by running a script, make sure that you have to update the Java path in only one place. If you run in a distributed system, think about easy ways to change the Java versions across all of the machines.

- 使它容易改变Java版本:使用最新的Java版本有助于避免许多运行时问题.如果您的应用程序开始运行一个脚本,确保您必须更新Java路径只在一个地方.如果你运行在一个分布式系统,考虑简单的方法改变Java版本的所有机器。

  - Make it easy to change the Java command-line options: Sometimes while troubleshooting you may want to change Java options; for example, to add a verbose output, to turn off a feature, or to tune Java for better performance. Make sure to prepare the systems for these changes.

- 很容易改变Java命令行选项:有时当故障排除你可能想改变Java选项;例如,添加一个详细的输出,关闭功能,或为更好的性能优化Java.确保准备这些变化的系统。

  In a Java application that is running remotely, for example in a testing framework or a cloud solution, make sure you can still change the Java flags easily. Sometimes the application takes command-line parameters or you may want to try a flag quickly to reproduce a problem. Prepare the systems to make these changes easy.

远程运行在Java应用程序中,例如在一个测试框架或云解决方案,确保你仍然可以轻易改变Java旗帜.有时应用程序接受命令行参数或你可能想尝试国旗很快繁殖问题。准备简单的系统来实现这些变化。

<https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/prepapp001.html>
