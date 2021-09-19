---
ID: 10596
post_title: >
  Getting a service account for VSO with
  TFS Service Credential Viewer
post_name: >
  getting-service-account-vso-tfs-service-credential-viewer
author: >
  Martin Hinshelwood (He/Him)
  nkdAgility.com
post_date: 2014-06-18 15:41:22
layout: post
link: >
  https://nkdagility.com/blog/getting-service-account-vso-tfs-service-credential-viewer/
published: true
tags:
  - TFS
  - VSTeamServices
categories:
  - 'Tools &amp; Techniques'
---
<p>Have you tried to get a service account for Visual Studio Online (VSO)? Did you know that you can use the TFS Service Credential Viewer to get it.</p>
<p>When you join a local or azure build server to your VSO account you are asked to log in with an account that is an administrator to get credentials. However it cant continue to use your credentials as your Microsoft ID token expires after 2 days and you would have to login again. Not a good experience. However there is a little bit of code that the build server uses to get a basic service username and password that it uses instead. I have used this to create unit tests that hit the TFS API’s in VSO as well as do all sorts of automated tasks that I need.</p>
<p>I created the TFS Service Credential Viewer when the service was still in Preview but it is no less required now. Its your gateway to automation with VSO.</p>
<h3>Download TFS Service Credential Viewer</h3>
<p>The following prerequisites are required:</p>
<ul>
<li>Team Explorer 2013 <del>Visual Studio 11 (any version)</del></li>
<li>.NET 4.5</li>
</ul>
<p>If these components are already installed, you can <a href="http://nakedalmweb.wpengine.com/downloads/tools/tfs2012/TfsServiceCredentialViewer/TfsServiceCredentialsUI.application">launch</a> the application now. Otherwise, click install below to install the prerequisites and run the application.</p>
<h6><a href="http://nakedalmweb.wpengine.com/downloads/tools/tfs2012/TfsServiceCredentialViewer/setup.exe"><span style="font-size: medium;">install</span></a><span style="font-size: medium;"> or </span><a href="http://nakedalmweb.wpengine.com/downloads/tools/tfs2012/TfsServiceCredentialViewer/TfsServiceCredentialsUI.application"><span style="font-size: medium;">launch via clickonce</span></a></h6>
<h3>How it works</h3>
<p>Once you have authenticated as a TFS Collection Administrator using your Microsoft ID to your hosted VSO instance we use the Access Control Service to provision a service identity that you can use for unattended connections to VSO.</p>
<p><a href="http://i0.wp.com/blog.hinshelwood.com/files/2012/03/SNAGHTML85af783.png"><img title="SNAGHTML85af783" src="http://i1.wp.com/blog.hinshelwood.com/files/2012/03/SNAGHTML85af783_thumb.png?zoom=1.5&amp;resize=460%2C461" alt="SNAGHTML85af783" width="460" height="461" border="0" /></a><br /><strong>Figure: A quick #1, #2 to get your credentials</strong></p>
<p>http://youtu.be/Fkn6V0_zz28<br /><strong>Video: How to get your credentials</strong></p>
<h3>Troubleshooting</h3>
<p>If you are using Windows 8 you will not get an automatic launch of the application due to an extra security check called Smart Screen for applications that come from the internet.</p>
<ol>
<li>Click or Press “Start” and Scroll all the way to the right</li>
<li>Select the TFS Service Credential Viewer</li>
<li>When the security dialog pops up click “More Info”
<p><a href="http://i1.wp.com/blog.hinshelwood.com/files/2012/03/image22.png"><img title="image" src="http://i2.wp.com/blog.hinshelwood.com/files/2012/03/image_thumb22.png?zoom=1.5&amp;resize=640%2C268" alt="image" width="640" height="268" border="0" /></a><br /><strong>Figure: Select More Info<br /></strong></p>
</li>
<li>Click “Run anyway” to launch the application and add it to the safe list
<p><a href="http://i2.wp.com/blog.hinshelwood.com/files/2012/03/image23.png"><img title="image" src="http://i2.wp.com/blog.hinshelwood.com/files/2012/03/image_thumb23.png?zoom=1.5&amp;resize=640%2C270" alt="image" width="640" height="270" border="0" /></a><br />Figure;</p>
</li>
<li>Done</li>
</ol>
<p>If you encounter an exception when clicking “Connect” the most likely cause if that you do not have Team Explorer 2013 installed (it should also work with 2012).</p>