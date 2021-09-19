---
ID: 10006
post_title: 'Issue [ TFS 2013 ] TF255466 A previous update or installation requires a restart'
post_name: >
  issue-tfs-2013-tf255466-previous-update-installation-requires-restart
author: >
  Martin Hinshelwood (He/Him)
  nkdAgility.com
post_date: 2013-09-17 10:30:36
post_excerpt: '<p class="lead">After you have installed SQL Server 2012 Service Pack 1 you may encounter the error “TF255466 A previous update or installation requires a restart” when trying to install TFS 2013. </p>'
layout: post
link: >
  https://nkdagility.com/blog/issue-tfs-2013-tf255466-previous-update-installation-requires-restart/
published: true
tags:
  - PendingFileRenameOperations
  - TF254027
  - TF255466
  - TFS
  - TFS 2013
categories:
  - 'Problems &amp; Puzzles'
---
<p class="lead">After you have installed SQL Server 2012 Service Pack 1 you may encounter the error “TF255466 A previous update or installation requires a restart” when trying to install TFS 2013.</p>
<p>Even if you install all Windows Updates and reboot you continue to get this message.</p>
<p><span class="label label-important">MANDATORY SP1 Hotfix</span> <em>SP1 installations are currently experiencing an issue in certain configurations as described in Knowledge Base article <a href="http://support.microsoft.com/kb/2793634" target="_blank">KB2793634</a>. The article provides a fix for this issue that is currently available for download, and is MANDATORY for application immediately following a Service Pack 1 installation. The fix is also being made available on Microsoft Update.</em></p>
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; margin: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="image" alt="image" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2013/08/image13.png" width="720" height="450" border="0" /><br /><small>Figure: TF255466 A previous update or installation requires a restart</small></p>
<p>Even if you reboot untill you are pounding on the keyboard....</p>
<h2>Applies to</h2>
<ul>
<li>Visual Studio 2013 Team Foundation Server Preview</li>
<li>Visual Studio 2013 Team Foundation Server RC</li>
</ul>
<h2>Findings</h2>
<p>No matter what you do this error continues to occur whenever you try an install TFS 2013. If you have a look at the log you should see that a “PendingFileRenameOperations” flag has been set and does not want to clear.</p>
<pre>[Info   @18:53:14.576] +-+-+-+-+-| Verifying that the system restart is not required |+-+-+-+-+-
[Info   @18:53:14.576] Starting Node: VPENDINGREBOOT
[Info   @18:53:14.576] NodePath : VINPUTS/Conditional/Progress/VPENDINGREBOOT
[Info   @18:53:14.577] IsPendingSxsRebootRequired() returned False
[Info   @18:53:14.577] The value 'PendingFileRenameOperations' under 'HKEY_LOCALMACHINE\SYSTEM\CurrentControlSet\Control\Session Manager' registry key is not empty
[Info   @18:53:14.577] IsSessionManagerRebootRequired(True, True) returned True
[Error  @18:53:14.577] Found a pending file operation - configuration blocked until reboot
[Info   @18:53:14.577] Node returned: Error
[Error  @18:53:14.577] TF255466: The configuration process for Team Foundation Server cannot continue.  A previous update or installation requires a restart of the operating system.  Restart the computer, and then open the administration console for Team Foundation to restart the configuration wizard.
[Info   @18:53:14.577] Completed NoPendingReboots: Error
[Info   @18:53:14.577] -----------------------------------------------------</pre>
<p>This is normally cleared when you do a reboot as whatever actions can be taken then. This can continue to happen with a newly installed copy of Windows Server 2012 due to the volume of updates that are available. Effectively every time you reboot it can start installing updates immediately. If this is the case then you can wait until all of the Updates are finished or you can stop the Windows Update service temporarily to get things done.</p>
<h2>Solution: Non Security Update for SQL Server 2012 SP1</h2>
<p>However there was a bug with SQL Server 2012 where the <a href="http://support.microsoft.com/kb/2793634">Windows Installer starts repeatedly after you install SQL Server 2012 SP1</a>. Basically there is a mismatch of the version of a file that is installed and the SQL Server installer keep trying to fix it. Thus resulting in a permanent loop of pending reboots…</p>
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; margin: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="image" alt="image" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2013/08/image14.png" width="800" height="500" border="0" /><br /><small>Figure: Windows Installer starts repeatedly after you install SQL Server 2012 SP1</small></p>
<p>If think this is the issue you can head on over here and download the <a href="http://www.microsoft.com/en-us/download/details.aspx?id=36215">Non Security Update for SQL Server 2012 SP1 (KB2793634)</a> to fix it.</p>
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; margin: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="image" alt="image" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2013/08/image15.png" width="800" height="500" border="0" /><br /><small>Figure: All readiness checks complete</small></p>
<p>For me this fixed my issue…</p>
