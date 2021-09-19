---
ID: 10321
post_title: >
  Installing Release Management Client for
  Visual Studio 2013
post_name: >
  installing-release-management-client-visual-studio-2013
author: >
  Martin Hinshelwood (He/Him)
  nkdAgility.com
post_date: 2014-01-10 10:35:19
post_excerpt: >
  With the addition of the new Release
  Management Client for Visual Studio 2013
  to the Visual Studio ALM roundup many
  folks are going to be giving it a go. If
  you might remember some of my post
  during the preview days of this tool
  there were some issue with installing.
layout: post
link: >
  https://nkdagility.com/blog/installing-release-management-client-visual-studio-2013/
published: true
tags:
  - InRelease
  - Release Management
  - Release Management Client
  - TFS
  - TFS 2013
  - Visual Studio 2013
  - VS
categories:
  - 'Install &amp; Configure'
---
<p class="lead">With the addition of the new Release Management Client for Visual Studio 2013 to the Visual Studio ALM roundup many folks are going to be giving it a go. If you might remember some of my post during the preview days of this tool there were some issue with installing it. It looks like Microsoft has gotten most of them sorted out and I can now get everything installed.</p>
<p>The Release Management Client for Visual Studio 2013 allows you to create and configure all aspects of your release pipeline. You can configure environments from servers and stages of binary promotion with workflow and parameters for deployment at each stage to any environment.</p>
<p><img alt="" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2014/01/011014_1034_READYInstal1.png" /><br /><small>Figure: Running the installer from the ISO</small></p>
<p>You can either download the web installers from the <a href="http://www.visualstudio.com/en-us/downloads">public website</a> or you can download the ISO from MSDN if you have an account. If you go with the pubic downloads you will need an active internet connection. If however you want to download the contents for later use you can use the "whatever.exe /layout" option and have the files downloaded locally for later.</p>
<p><img alt="" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2014/01/011014_1034_READYInstal2.png" /><br /><small>Figure: Installing the Release Management Client</small></p>
<p>Within a few seconds you will have the client installed. It is a simple SPF application and thus this is an extremely quick install.</p>
<p>I like that the team managed to update the installers. With the early preview releases of Release Management, there were many issues with installation that really needed to be addresses and this was quick and painless. Like it should be.</p>
<p><img alt="" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2014/01/011014_1034_READYInstal3.png" /><br /><small>Figure: Configured client</small></p>
<p>When you first launch the Release Management client you will be asked to select the server and port where you installed the server. Once you have done this the client will open easily and quickly. If you get an error at this point it is likely a communication problem between you and the server.</p>
<p>One thing that you should make sure of is that you add users to Release Management as soon as you can. The only user that is added initially is the account of the user that installed the server. This will be under the heading of 'Admin' in "Administration | Users". Don't get caught short and unable to access your server if you used another account to install the Server and the client.</p>
<p>You should now be ready to go...</p>