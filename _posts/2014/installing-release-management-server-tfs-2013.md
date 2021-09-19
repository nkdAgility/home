---
ID: 10351
post_title: >
  Installing Release Management Server for
  TFS 2013
post_name: >
  installing-release-management-server-tfs-2013
author: >
  Martin Hinshelwood (He/Him)
  nkdAgility.com
post_date: 2014-01-30 11:30:07
layout: post
link: >
  https://nkdagility.com/blog/installing-release-management-server-tfs-2013/
published: true
tags:
  - InRelease
  - Install
  - Release Management
  - Release Management Server
  - TFS
  - TFS 2013
categories:
  - 'Install &amp; Configure'
---
<p class="lean">Unless you have been living under a rock you might have noticed that Microsoft has added a Release Management tool to its Visual Studio product line. I have been playing with it for a while now and I think I have it figured out. However as this is a new addition to the product it is extremely poorly documented.</p>
<p>I have just finished writing for the Release Management chapter in Professional Application Lifecycle Management with Visual Studio 2013 [<a title="Professional Application Lifecycle Management with Visual Studio 2013 on Amazon USA" href="http://www.amazon.com/gp/product/1118836588/ref=as_li_ss_tl?ie=UTF8&amp;camp=1789&amp;creative=390957&amp;creativeASIN=1118836588&amp;linkCode=as2&amp;tag=martinhinshe-20" target="_blank">Amazon USA</a> | <a title="Professional Application Lifecycle Management with Visual Studio 2013 on Amazon UK" href="http://www.amazon.co.uk/gp/product/1118836588/ref=as_li_ss_tl?ie=UTF8&amp;camp=1634&amp;creative=19450&amp;creativeASIN=1118836588&amp;linkCode=as2&amp;tag=marthinssblog-21" target="_blank">Amazon UK</a>] and while I covered the ALM aspects I did not really cover how to install the components. So here goes...</p>
<p>You can either download the individual components from <a href="http://www.visualstudio.com/en-us/downloads#d-release-management" target="_blank">the Visual Studio site</a> or if you have an MSDN account you can download an ISO with all three applications inside.</p>
<p>Note: If you want to take the public download offline you can run "setup.exe /layout" and all of the components will be downloaded for offline use. Good for servers not on the internet.</p>
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; margin: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="clip_image001" alt="clip_image001" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2014/01/clip_image0012.png" width="800" height="450" border="0" /><br /><small>Figure: ISO for Release Management for Visual Studio 2013</small></p>
<p>Here I am simply running the rm_server.exe in the 'Server' folder on the ISO.</p>
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; margin: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="clip_image002" alt="clip_image002" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2014/01/clip_image0022.png" width="800" height="450" border="0" /><br /><small>Figure: Installing Release Management Server for Team Foundation Server 2013</small></p>
<p>Selecting the usual licence agreement the only thing of note is the size of the tool. At a mere 25MB this is a ridiculously quick install. Remember this is just putting the files on disk and registering any required DLL's and is not configuring it for use.</p>
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; margin: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="clip_image003" alt="clip_image003" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2014/01/clip_image0032.png" width="800" height="450" border="0" /><br /><small>Figure:</small> Install Release Management Server for Team Foundation Server 2013</p>
<p>There is little drama and it’s a small install that I think finished in just a few minutes, despite the long name :). At the end of the install you get a simple Launch button to launch the configuration tool. There is a link on the start menu as well.</p>
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; margin: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="clip_image004" alt="clip_image004" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2014/01/clip_image0041.png" width="800" height="450" border="0" /><br /><small>Figure: After install you need to launch the configuration</small></p>
<p>Unfortunately as I noted with the Client tool the team has modelled the configuration on the old style Test Agent and Controller configuration rather than the more modern and featureful TFS configuration. I am hoping that this will end up as a node in the main Team Foundation Server configuration wizard. I would settle for the same configuration experience as the SharePoint extensions or Build Agents but what we have now is good enough.. Se la vie, however if it has been integrated it would likely have picked up the DB server and Ports if we were installing on our Team Foundation Server, which I believe to be the common case. Hopefully the TFS team will work on this for the next realese, or even better, in an update for 2013. For now, we are just configuring this as if it was a separate thing.</p>
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; margin: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="clip_image005" alt="clip_image005" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2014/01/clip_image0051.png" width="800" height="450" border="0" /><br /><small>Figure: Configuring Release Management Server</small></p>
<p>In my configuration I am keeping the defaults. As I have the Release Management Server installed on the same server as TFS I will be unlikely have locked down communication between servers and can mostly get away with Network Service.</p>
<p><small><span class="label label-info">Note You can cheat a little here by creating an Active Directory group and adding all of the machine accounts, that how Network Service authenticates, in it. You can then give permission to that group and remove the need for passwords or password changes of service accounts across many computers.</span></small></p>
<p>Now all we have to do is apply the changes..</p>
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="clip_image006" alt="clip_image006" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2014/01/clip_image0061.png" width="800" height="450" border="0" /><br /><small>Figure: All Configuration tasks have completed successfully</small></p>
<p>And low… we have a Release Management Server for Team Foundation Server 2013… First configuration is a little tricky and I covered that in <a href="http://nakedalmweb.wpengine.com/installing-release-management-client-visual-studio-2013/">Installing Release Management Client for Visual Studio 2013</a>…</p>