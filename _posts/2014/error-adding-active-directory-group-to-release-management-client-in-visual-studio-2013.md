---
ID: 10316
post_title: >
  Error adding Active Directory Group to
  Release Management Client in Visual
  Studio 2013
post_name: >
  error-adding-active-directory-group-to-release-management-client-in-visual-studio-2013
author: >
  Martin Hinshelwood (He/Him)
  nkdAgility.com
post_date: 2014-01-07 07:42:09
post_excerpt: >
  When you try to add a group from Active
  Directory in the Release Management
  Client in Visual Studio 2013 you get an
  unhandled exception.
layout: post
link: >
  https://nkdagility.com/blog/error-adding-active-directory-group-to-release-management-client-in-visual-studio-2013/
published: true
tags:
  - InRelease
  - Release Management
  - TFS
  - TFS2013
  - Visual Studio 2013
  - VS
categories:
  - 'Problems &amp; Puzzles'
---
<p class="lead">When you try to add a group from Active Directory in the Release Management Client in Visual Studio 2013 you get an unhandled exception.</p>
<p>When trying to add an Active Directory group to release management the other day I saw a little popup after adding the group that disappeared too quickly to action. I noticed that the group that I was trying to add did not end up in the list so I gave it another go.</p>
<p><img alt="" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2014/01/010714_0741_ReadyErrora1.png" /><br /><small>Figure: Some requested groups could not be added</small></p>
<blockquote>
<p>An unhandled exception has occurred in the application: Some requested groups could not be added. Either the groups are outside your domain, or it does not follow the LDAP protocol.</p>
</blockquote>
<h3>Applies to</h3>
<ul>
<li>Release Management Client for Visual Studio 2013</li>
</ul>
<h3>Findings</h3>
<p>The first annoying thing is the poor implementation of the error alerts. The toast notification is very time limited and there is no way to get top a list of errors that I can see. If you miss it its gone...</p>
<p>I tried adding different groups to make sure it was not an AD issue with that group and the error persisted. I don't have multiple Active Directory implementations so I can't try other configurations but it looks to be consistent. When you click "Administration | Manage Groups | New | New from AD" the "Select Groups" box initially has the local computer selected rather than the domain.</p>
<p><img alt="" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2014/01/010714_0741_ReadyErrora2.png" /><br /><small>Figure: New from Active Directory</small></p>
<p>Under normal circumstances you would select "Entire Directory" and enter the entire or partial name of the group, in this case "Domain Users".</p>
<p>Note: Never actually use Domain Users in a production system. I know that I only have 20 or so users in my entire AD system as it is only for testing. TFS has a limit of around 5k users, however I do not know what the Release Management Client has been tested to.</p>
<p><img alt="" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2014/01/010714_0741_ReadyErrora3.png" /><br /><small>Figure: Select the scope of the directory search</small></p>
<p>However if you have "Entire Directory" selected the result will be the Untangled Exception identified above. If you click "View Stack Trace" on that exception then you get the following details.</p>
<p><img alt="" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2014/01/010714_0741_ReadyErrora4.png" /><br /><small>Figure: Some requested groups could not be added</small></p>
<blockquote>
<p>An unhandled exception has occurred in the application: Some requested groups could not be added. Either the groups are outside your domain, or it does not follow the LDAP protocol.</p>
</blockquote>
<p>Obviously this is incorrect as I only selected a single group from Active Directory.</p>
<h3>Solution</h3>
<p>While this is annoying and should be easy to fix in the original code it obviously slipped through the test matrix and will likely be fixed on the next release. For now you can select the individual domain instead of the "Entire Directory" option.</p>
<p><img alt="" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2014/01/010714_0741_ReadyErrora5.png" /><br /><small>Figure: Select exact domain</small></p>
<p>In this case if I select "env.nakedalmweb.wpengine.com" as the exact domain that the group that I am trying to add exists in then the group is added with no issues.</p>