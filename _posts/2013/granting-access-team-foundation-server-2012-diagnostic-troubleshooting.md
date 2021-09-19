---
ID: 10002
post_title: >
  Granting access to Team Foundation
  Server 2012 for diagnostic
  troubleshooting
post_name: >
  granting-access-team-foundation-server-2012-diagnostic-troubleshooting
author: >
  Martin Hinshelwood (He/Him)
  nkdAgility.com
post_date: 2013-09-24 10:40:35
post_excerpt: '<p class="lead">In TFS 2012 the product team added a way to get to the tbl_Command information without needing to connect directly to the SQL Server and having access to the tables. This was an awesome add as being able to diagnose server issues and troubleshoot user reported problems makes us a little more efficient.</p>'
layout: post
link: >
  https://nkdagility.com/blog/granting-access-team-foundation-server-2012-diagnostic-troubleshooting/
published: true
tags:
  - TFS
  - TFS 2012
  - TFS 2013
categories:
  - 'Problems &amp; Puzzles'
  - 'Tools &amp; Techniques'
---
<p class="lead">In TFS 2012 the product team added a way to get to the tbl_Command information without needing to connect directly to the SQL Server and having access to the tables. This was an awesome add as being able to diagnose server issues and troubleshoot user reported problems makes us a little more efficient.</p>
<p><img title="image" style="border-left-width: 0px; border-right-width: 0px; background-image: none; border-bottom-width: 0px; padding-top: 0px; padding-left: 0px; margin: 0px; display: inline; padding-right: 0px; border-top-width: 0px" border="0" alt="image" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2013/08/image11.png" width="720" height="450"/><br /><small>Figure: Viewing the diagnostic activity logs for troubleshooting</small></p>
<p>However I had always had to give access by adding the user to the “Team Foundation Administrators” group which is a little too much power just to do a little diagnostic spelunking… so my question is:</p>
<p>How do I give permission to the Activity Log without giving TFS Administrator?</p>
<p>Well, it looks like the command line has the answer. Although there is no representative entry in the GUI to give permission for a user only to the diagnostic troubleshooting page you can grant it explicitly:</p>
<pre class="brush: ps; collapse: true;">tfssecurity /a+ Diagnostic Diagnostic Troubleshoot n:domain\username ALLOW /server:http://tfsserver:8080
</pre>
<p>This gives that group explicit access. </p>
<p><img title="image" style="border-left-width: 0px; border-right-width: 0px; background-image: none; border-bottom-width: 0px; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border-top-width: 0px" border="0" alt="image" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2013/08/image12.png" width="720" height="450"/><br /><small>Figure: Use the command line to grant diagnostic troubleshooting permission</small></p>
<p>What might be a better and more manageable solution would be to create a group called “Team Foundation Troubleshooters” and instead grant that group permission to that access control. This is done in exactly the same way, you just need to replace the domain account with the TFS Group.</p>
