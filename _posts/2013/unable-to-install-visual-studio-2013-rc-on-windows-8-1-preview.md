---
ID: 9998
post_title: >
  Unable to install Visual Studio 2013 RC
  on Windows 8.1 Preview
post_name: >
  unable-to-install-visual-studio-2013-rc-on-windows-8-1-preview
author: >
  Martin Hinshelwood (He/Him)
  nkdAgility.com
post_date: 2013-09-09 10:40:43
post_excerpt: '<p class="lead">When you try to install Visual Studio 2013 RC (or Visual Studio 2013 RC Team Foundation Server) you get the message “Error: This version of Team Foundation Server is not compatible with Windows 8.1 Preview”</p>'
layout: post
link: >
  https://nkdagility.com/blog/unable-to-install-visual-studio-2013-rc-on-windows-8-1-preview/
published: true
tags:
  - TFS
  - TFS 2013
  - Windows
  - Windows Server
categories:
  - News and Reviews
  - 'Problems &amp; Puzzles'
---
<p class="lead">When you try to install Visual Studio 2013 RC (or Visual Studio 2013 RC Team Foundation Server) you get the message “Error: This version of Team Foundation Server is not compatible with Windows 8.1 Preview”</p>
<p><img title="image" style="border-left-width: 0px; border-right-width: 0px; background-image: none; border-bottom-width: 0px; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border-top-width: 0px" border="0" alt="image" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2013/08/image10.png" width="750" height="450"><br>Figure: This version of Team Foundation Server is not compatible with Windows 8.1 Preview</p>
<h2>Applies to</h2>
<ul>
<li>Team Foundation Server 2013 Preview on Windows Server 2012 R2 Preview
<li>Visual Studio on Windows Server 2012 R2 Preview
<li>Team Foundation Server 2013 Preview on Windows 8.1 Preview
<li>Visual Studio on Windows 8.1 Preview</li>
</ul>
<h2>Findings</h2>
<p>Unfortunately in order to install the Release Candidate there is a requirement to update the version of .NET that is on the server. As the Preview copies of Windows 8.1 and Windows Server 2012 R2 has .net 4.5.1 Preview baked in you will not be able to install the new version on there.</p>
<p>You can however use Windows Server 2012, Windows 8, Windows Server 2008 R2, and Windows 7 to install the components.</p>
<h2>Conclusion</h2>
<p>In order to move forward with the new RC versions of Visual Studio and Team Foundation Server you will need to move to an RTM version of Windows. If you can get the Windows 8.1 or Windows Server 2012 R2 RTM then you are good to go. However you will be unlikely to get them prior to General Availability in October. </p>
<p>You can however use any of the existing version of Windows and Windows Server that are supported.</p>
<p>&nbsp;</p>
<p><!--EndFragment--></p>
