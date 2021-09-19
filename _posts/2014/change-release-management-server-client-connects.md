---
ID: 10329
post_title: >
  Change the Release Management Server
  that your Client connects to
post_name: >
  change-release-management-server-client-connects
author: >
  Martin Hinshelwood (He/Him)
  nkdAgility.com
post_date: 2014-01-13 10:45:59
post_excerpt: >
  As a consultant I am onsite at a
  different customer every week and as I
  use my own laptop for most engagements I
  need to be able to change the Release
  Management Server that I connect to from
  the thick client.
layout: post
link: >
  https://nkdagility.com/blog/change-release-management-server-client-connects/
published: true
tags:
  - InRelease
  - Release
  - Release Management
  - Release Management Client
  - TFS
  - TFS 2013
  - Visual Studio 2013
categories:
  - 'Install &amp; Configure'
  - 'Upgrade &amp; Maintenance'
---
<p class="lead">As a consultant I am onsite at a different customer every week and as I use my own laptop for most engagements I need to be able to change the Release Management Server that I connect to from the thick client.</p>
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="clip_image001" alt="clip_image001" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2014/01/clip_image001.png" width="800" height="450" border="0" /><br /><small>Figure: The Release Management Client</small></p>
<p>The Release Management team kindly added a UI to allow us to change which server that we are connected to. Open you RM client ad head over to "Administration | Settings| System Setting" and you can then click the "Edit" button next to the current "Release Management Server URL".</p>
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="clip_image002" alt="clip_image002" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2014/01/clip_image002.png" width="800" height="450" border="0" /><br /><small>Figure: Editing the configured Release Management Server</small></p>
<p>However if you try to open the client without being able to access that server you get an error message and you are unable to get to that screen to change the server URL. It would have been nice if it just asked us if we wanted to reconfigure and launched the original configuration dialog, however that is not the case.</p>
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="clip_image003" alt="clip_image003" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2014/01/clip_image003.png" width="800" height="450" border="0" /><br /><small>Figure: Can't open Release Management Client with no Server available</small></p>
<p>By default the port of your RM server is 1000 but you may have changed it so you need to know both the port and the server. Unfortunately if your correct release management server is unavailable then the client will error our and close.</p>
<p>In order to work around this you need to change the URL that tells the Release Management Client to connect to that specifc server and it is fairly well hidden. You need to head over to the Microsoft.TeamFoundation.Release.Data.dll.config file and update it manually.</p>
<p>The Release Management team however have created a handy utility that may make it a little quicker. You can run ReleaseManagementConsoleAdjustConfigFile.exe and pass in both the configuration that you want to change and the configuration property along with the value.</p>
<blockquote>
<p>C:\Program Files (x86)\Microsoft Visual Studio 12.0\Release Management\bin\ReleaseManagementConsoleAdjustConfigFile.exe –configfilename   .\Microsoft.TeamFoundation.Release.Data.dll.config -newwebserverurl http://bvtirserverpod1:1000</p>
</blockquote>
<p>In this way you can update the server when you move from site to site. If you switch between client sites often it might be useful to create batch files on your desktop for launching the client with the right connection. Just call the connection change and then launch the app. Simples...</p>