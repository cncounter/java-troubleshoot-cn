# Appendix B. Java 2D Properties

This appendix presents properties that can be useful in troubleshooting Java 2D.

This appendix contains the following sections:

## Properties on Oracle Solaris and Linux

[Table B-1](#CIHGGCJB) describes the default values of some useful properties on Oracle Solaris and Linux platforms.

Table B-1 Default Java 2D Properties on Oracle Solaris and Linux

<table>
<colgroup><col width="*">
<col width="8%">
<col width="8%">
<col width="13%">
<col width="19%">
<col width="19%">
</colgroup><thead>
<tr>
<th>Setup</th>
<th>DGA</th>
<th>SHM</th>
<th>Pixmaps</th>
<th>OnScreen</th>
<th>OffScreen</th>
</tr>
</thead>
<tbody>
<tr>
<td>Oracle Solaris SPARC with DGA support</td>
<td>On</td>
<td>On</td>
<td>Off</td>
<td>DGA/Software</td>
<td>Software</td>
</tr>
<tr>
<td>Oracle Solaris SPARC with no DGA, Oracle Solaris x86, Linux, SunRay, VNC</td>
<td>Off</td>
<td>On</td>
<td>On</td>
<td>X11/MITSHM</td>
<td>Shared/Server Pixmaps</td>
</tr>
<tr>
<td>J2SE 1.4 or greater: Remote X server, ssh</td>
<td>Off</td>
<td>Off</td>
<td>On</td>
<td>X11</td>
<td>Server Pixmaps</td>
</tr>
<tr>
<td>J2SE 1.3.1 or less: Remote X server, ssh</td>
<td>Off</td>
<td>Off</td>
<td>Off</td>
<td>X11</td>
<td>Software</td>
</tr>
</tbody>
</table>


The following list explains how to change the defaults.

* The X11 pipeline is the default pipeline for Oracle Solaris and Linux. Change this default as follows:

  * `-Dsun.java2d.opengl=true`  Attempt to enable the OpenGL pipeline.

* The use of DGA is controlled as follows:

  * `NO_J2D_DGA unset`  Use DGA, if available.

  * `NO_J2D_DGA set`  Disable the use of DGA.

* MIT Shared Memory Extension (SHM) is controlled as follows:

  * To use SHM, if available, specify either one of the following properties:

  `NO_J2D_MITSHM unset`

  `J2D_USE_MITSHM=true`

  * To **not** use SHM, specify either one of the following properties:

  `NO_J2D_MITSHM set`

  `J2D_USE_MITSHM=false`

* The general use of pixmaps is controlled as follows:

  * `-Dsun.java2d.pmoffscreen unset`  Use pixmaps if DGA is not available.

  * `-Dsun.java2d.pmoffscreen=true`  Force the use of pixmaps.

  * `-Dsun.java2d.pmoffscreen=false`  Disable the use of pixmaps.

* The use of Shared and Server pixmaps is controlled as follows:

  * `J2D_PIXMAPS unset`  Use both types.

  * `J2D_PIXMAPS=shared`  Use only shared memory pixmaps.

  * `J2D_PIXMAPS=sserver`  Use only server-side pixmaps.

* The choice of default visual is controlled as follows:

  * `FORCEDEFVIS` unset (default)  Use the best visual available.

  * `FORCEDEFVIS` set to a hexadecimal value  Use the visual whose ID is the hexadecimal value.

  * `FORCEDEFVIS` set to any other value  Use the default visual.

## Properties on Windows

The following list describes some useful properties on Windows platforms.

* The DirectDraw/GDI pipeline is the default pipeline for Windows. Change this default as follows:

  * `-Dsun.java2d.noddraw=true`  Disable the use of DirectDraw pipeline. GDI will be used instead.

  * `-Dsun.java2d.noddraw=false`  Enable the use of DirectDraw pipeline.

  * `-Dsun.java2d.d3d=false`  Disable the use of Direct3D pipeline.

  * `J2D_D3D=false`  Disable the use of Direct3D pipeline.

  * `-Dsun.java2d.d3d=true`  Enable the use of Direct3D pipeline.

  * `J2D_D3D=true`  Enable the use of Direct3D pipeline.

* Control the use of the built-in surface punting mechanism as follows:

  * `-Dsun.java2d.ddforcedram=true`  Keep volatile images in VRAM.

* Control the use of DirectDraw blit operations as follows:

  * `-Dsun.java2d.ddblit=false`  Disable the use of DirectDraw blit operations. GDI blits will be used instead.


<https://docs.oracle.com/javase/8/docs/technotes/guides/troubleshoot/java2d-props.html>
