---
ID: 11097
post_title: >
  Unable to load task handler PowerShell
  for task VSBuild
post_name: >
  unable-load-task-handler-powershell-task-vsbuild
author: >
  Martin Hinshelwood (He/Him)
  nkdAgility.com
post_date: 2015-03-18 14:12:00
post_excerpt: |
  <p class="lead">If you are setting up to run Team Foundation Server's vNext build system that Microsoft is previewing on VSO you may hit a "Unable to load task handler PowerShell for task VSBuild with version 1.0.1" error when you try to build on Windows Server Technical Preview.</p>
layout: post
link: >
  https://nkdagility.com/blog/unable-load-task-handler-powershell-task-vsbuild/
published: true
tags:
  - Agent
  - Build.vNext
  - PowerShell
  - TFS
  - TFS 2015
  - VSBuild
  - VSTeamServices
categories:
  - 'Problems &amp; Puzzles'
---
<p class="lead">If you are setting up to run Team Foundation Server's vNext build system that Microsoft is previewing on VSO you may hit a "Unable to load task handler PowerShell for task VSBuild with version 1.0.1" error when you try to build on Windows Server Technical Preview.</p>
<div class="bs-callout bs-callout-info">
<h4>Download Team Foundation Server 2015 today</h4>
<p>Microsoft has released a CTP of TFS 2015 that includes the vNext build system. You can <a href="https://www.visualstudio.com/en-us/downloads/visual-studio-2015-ctp-vs" target="_blank">download TFS 2015</a> and try it out today. Remember that this is <em>not</em> a go-live version and you should <em>not </em>install it in production.</p>
</div>
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; margin: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="clip_image001" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2015/01/clip_image0013.png" alt="clip_image001" width="800" height="446" border="0" /></p>
<p>After you have <a href="http://nakedalmweb.wpengine.com/configure-vso-vnext-build-agent/">configured a vNext build agent</a> you may get an error when you try and build. This error occurs regardless of the tasks that you pick for your build.</p>
<pre>****************************************************************************** 
Starting Build (debug, any cpu) 
****************************************************************************** 
Executing the following commandline: 
C:\VsoWinAgent\agent\worker\vsoWorker.exe /name:Worker-4649b2ea-e06d-47b0-9a89-5f4aa4d545df /id:4649b2ea-e06d-47b0-9a89-5f4aa4d545df /rootFolder:"C:\VsoWinAgent" /logger:Forwarding,1.0.0;Verbosity=Verbose,Name=Agent1;JobId=4649b2ea-e06d-47b0-9a89-5f4aa4d545df 
Unable to load task handler PowerShell for task VSBuild with version 1.0.1. 
****************************************************************************** 
Finishing Build (debug, any cpu) 
****************************************************************************** 
Worker Worker-4649b2ea-e06d-47b0-9a89-5f4aa4d545df finished running job 4649b2ea-e06d-47b0-9a89-5f4aa4d545df 
</pre>
<p>I tried to build both with the "Visual Studio Build" task and the "MS Build" tasks that come out of the box. Both resulted in the same error and I can only assume that there is an internal dependency on a particular PowerShell version that is not present.</p>
<p>After some investigation on Windows Server Technical Preview I noticed that only PowerShell 5 is available and enabled out of the box. Just like on Server 2008 R2, if you want an older version of PowerShell or .NET to be available then you need to go manually enable it.</p>
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; margin: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="clip_image002" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2015/01/clip_image0024.png" alt="clip_image002" width="800" height="450" border="0" /></p>
<p>If you launch the "Add roles and features" you should see, on the features tab, an option for PowerShell with only PowerShell 5.0 installed. As this is only available in the Technical Preview my assumption would be that the team targeted the latest common version. Which would be the 2.x version.</p>
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; margin: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="clip_image003" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2015/01/clip_image0033.png" alt="clip_image003" width="800" height="450" border="0" /></p>
<p>On Server 2012 R2 you will also find that only PowerShell 4.0 is configured by default and you will need to add PowerShell 2.0 here as well. This will in addition also enable .NET 2 / 3.5 if it has not been already.</p>
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; margin: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="clip_image004" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2015/01/clip_image0043.png" alt="clip_image004" width="800" height="450" border="0" /></p>
<p>Although a better error message could be used, like detecting if the Windows feature is indeed enabled, this is an alfa version of the product and you don’t expect any such polish. After enabling the feature, and re-running the build…</p>
<p>And Poo, I still have a problem, so that’s not it. This brought me to the end of my wits and I had to go ask some folks.</p>
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; margin: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="clip_image005" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2015/01/clip_image0053.png" alt="clip_image005" width="800" height="450" border="0" /></p>
<p>After a flurry of emails to my peers on the champs list Jakob asked if I had Unblocked the Zip files! Do what now?</p>
<p>It turns out that if you download a zip file from the internet it may be "partially" blocked. Windows will block access to some files that it deems risky but not warn you nor stop you from unpacking it. Unfortunately it will only partially unpack… which rendered my build agent useless.</p>
<p>So if you are downloading a Zip file from the internet you may need to unblock them before you can use them fully.</p>
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="clip_image006" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2015/01/clip_image0063.png" alt="clip_image006" width="800" height="419" border="0" /></p>
<p>Woohoo… A successful build on the new Build vNext…</p>
