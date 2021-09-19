---
ID: 10667
post_title: 'You can&#8217;t use WITADMIN on versions older than TFS 2010'
post_name: >
  cant-use-witadmin-versions-older-tfs-2010
author: >
  Martin Hinshelwood (He/Him)
  nkdAgility.com
post_date: 2014-08-13 14:02:50
layout: post
link: >
  https://nkdagility.com/blog/cant-use-witadmin-versions-older-tfs-2010/
published: true
tags:
  - TFS
  - TFS 2010
  - TFS 2010 SP1
  - Visual Studio 2013
  - witadmin
categories:
  - 'Install &amp; Configure'
---
<p>I encountered a bit of a red herring today when I was trying to rename a Work Item Type Definition (WITD) and received the message that you can't use WITADMIN on versions older than TFS 2010. However the server was TFS 2010.</p>
<p>I am onsite in London this week doing a migration from TFS 2010 and Perforce to Visual Studio Online (VSO) and hit a confusing error message. My Surface only has Visual Studio 2013 installed so I am calling the 2013 version of WITADMIN against the TFS 2010 server. Since TFS 2010 is fully supported this should work with no issues. However instead of working I got a strange message:</p>
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; margin: 0px; display: inline; padding-right: 0px; border: 0px;" title="clip_image001" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2014/07/clip_image001.png" alt="clip_image001" width="800" height="321" border="0" /></p>
<blockquote>
<p>witadmin.exe : You cannot change the display name of a work item type. The feature is not supported on versions earlier than Team Foundation Server 2010.</p>
</blockquote>
<p>What do you mean visions older than TFS 2010! This is TFS 2010 dam it… so I bit the bullet and spun up my TFS 2012 box that has Visual Studio 2012 and the 2012 version of WITADMIN.</p>
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; margin: 0px; display: inline; padding-right: 0px; border: 0px;" title="clip_image002" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2014/07/clip_image0022.png" alt="clip_image002" width="800" height="450" border="0" /></p>
<p>And lo and behold I got the very same message. This made me think that there was something wrong with the TFS server. The server was a native 2010 (no upgrades) so there should be no issues. I logged onto the server to take a look and what did I find? TFS2012 RTM.</p>
<p>So.. First things first I need to update the server. I will be using the TFS Integration Tools to move to VSO, OpsHub do not support changing Team Project name, but its so much easier when you have the same process template and I really need to update it. I was thinking of updating strate to 2013 but that would require an upgrade of SQL Server. I thought of upgrading to TFS 2012 but that would require a Service Pack for SQL Server. The least dangerous option in the end was to apply TFS 2010 Service Pack 1…</p>
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; margin: 0px; display: inline; padding-right: 0px; border: 0px;" title="clip_image003" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2014/07/clip_image0032.png" alt="clip_image003" width="800" height="450" border="0" /></p>
<p>And after the upgrade?</p>
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border: 0px;" title="clip_image004" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2014/07/clip_image004.png" alt="clip_image004" width="800" height="153" border="0" /></p>
<p>Now I can run WITADMIN commands again.</p>
<p>You should always make sure that you have the latest version of whatever software that you want to use to make sure that you get compatibility with the tools. Even if you can't upgrade a full version you should never have less than TFS 2010 SP1, TFS 2012.4, or TFS 2013.2.</p>