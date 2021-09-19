---
ID: 11072
post_title: >
  Could not load file or assembly while
  configuring Build vNext Agent
post_name: >
  could-not-load-file-or-assembly-while-configuring-build-vnext-agent
author: >
  Martin Hinshelwood (He/Him)
  nkdAgility.com
post_date: 2015-01-15 16:56:46
post_excerpt: '<p class="lead">If you are using Windows Server 2012 R2 to test out the new vNext build agent then you may run into an error where it could not load file or assembly while configuring Build.vNext Agent.  </p>'
layout: post
link: >
  https://nkdagility.com/blog/could-not-load-file-or-assembly-while-configuring-build-vnext-agent/
published: true
tags:
  - Build
  - Build Agent
  - Build.vNext
  - Strong Name
  - Team Build
  - TFS
  - TFS 2015
  - VSTeamServices
categories:
  - 'Problems &amp; Puzzles'
---
<p class="lead">If you are using Windows Server 2012 R2 to test out the new vNext build agent then you may run into an error where it could not load file or assembly while configuring Build vNext Agent.</p>
<div class="bs-callout bs-callout-info">
<h4>Download Team Foundation Server 2015 today</h4>
<p>Microsoft has released a CTP of TFS 2015 that includes the vNext build system. You can <a href="https://www.visualstudio.com/en-us/downloads/visual-studio-2015-ctp-vs" target="_blank">download TFS 2015</a> and try it out today. Remember that this is <em>not</em> a go-live version and you should <em>not </em>install it in production.</p>
</div>
<p>I have been playing around with the new Build vNext Agent that Microsoft has been developing and I found that I was not able to register the Agent on Windows Server 2012 R2 when I had Visual Studio 2015 Preview installed. Before I installed Visual Studio I had no issues, but once on I got a "Could not load file or assembly" when trying to run the registration.</p>
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="clip_image001" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2015/01/clip_image001.jpg" alt="clip_image001" width="800" height="450" border="0" /></p>
<p>It looks like there is a version mismatch on the DLL.</p>
<pre>Unhandled Exception: System.IO.FileLoadException: Could not load file or assembly 'Microsoft.VisualStudio.Services.Client, Version=14.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a' or one of its dependencies. Strong name validation failed. (Exception from HRESULT: 0x8013141A) ---> System.Security.SecurityException: Strong name validation failed. (Exception from HRESULT: 0x8013141A)

--- End of inner exception stack trace ---

at VsoAgent.Program.Main(String[] args)

WARNING: UnConfigure agent finish with Error, you can check logs under _diag folder, determine whether you can ignore the error.
</pre>
<p>I am fairly sure that this is a time limited error and once VS 2015 comes out of Preview, or the DLL versions settle down this will not be an issue, however to fix it for now we need to turn of Strong Naming for .NET at the command prompt.</p>
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="clip_image002" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2015/01/clip_image0022.png" alt="clip_image002" width="800" height="450" border="0" /></p>
<p>You need to run "sn -Vr *,*" on the server to disable strong signing. This should only be the case as part of the current preview program. I would expect this issue to go away with the next release, at least on Server 2012 R2.</p>
<p>This is only required when you are running Visual Studio 2015 Preview on the Build vNext Agent.</p>
