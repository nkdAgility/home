---
ID: 10987
post_title: >
  Understanding TFS migrations from
  on-premise to Visual Studio Online
post_name: >
  understanding-tfs-migrations-premise-visual-studio-online
author: >
  Martin Hinshelwood (He/Him)
  nkdAgility.com
post_date: 2014-12-17 17:11:00
post_excerpt: '<p class="lead">I have recently been doing a lot of migrations and Willy asked me to write a white-paper about understanding TFS migrations from on-premise to Visual Studio Online.</p>'
layout: post
link: >
  https://nkdagility.com/blog/understanding-tfs-migrations-premise-visual-studio-online/
published: true
tags:
  - Migration
  - TFS
  - VSTeamServices
categories:
  - News and Reviews
---
<p class="lead">I have recently been doing a lot of migrations and <a href="http://blogs.msdn.com/b/willy-peter_schaub/" target="_blank">Willy </a>asked me to write a white-paper about understanding TFS migrations from on-premise to Visual Studio Online.</p>
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border: 0px;" title="clip_image001" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2014/12/clip_image0012.png" alt="clip_image001" width="392" height="258" border="0" /></p>
<p>On writing and understanding TFS migrations from on-premise to Visual Studio Online we found that the story was so poor that we broke it into two parts. The first part is ready and focuses on what the options are and the stories for migrating. Its interesting as many people believe that it is Microsoft's job to provide tools to migrate from any other product into their own product. While I would love to agree there are just way to many products out there to make that a realistic situation.</p>
<ul>
<li>PDF: <a href="https://vsarguidance.codeplex.com/releases/view/178488" target="_blank">Understanding TFS migrations from on-premise to Visual Studio Online</a></li>
</ul>
<p>We kind of looked at a number of scenarios:</p>
<ul>
<li><strong>Team Project to Team Project</strong> – While not common it is the simplest situation.<br /><img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border: 0px;" title="clip_image002" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2014/12/clip_image0022.png" alt="clip_image002" width="682" height="127" border="0" /></li>
<li><strong>Consolidating Team Projects</strong> – With the move to 2012+ this is the most common ask I have from customers. Wither on-premises or while moving to VSO, many folks are taking the time to pay back the technical cruft that has built up over the years.<br /><img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border: 0px;" title="clip_image003" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2014/12/clip_image0032.png" alt="clip_image003" width="716" height="164" border="0" /></li>
<li><strong>Splitting Team Projects</strong> – While not as common I have seen this as well. Splitting your data is an interesting situation and can be the result of selling parts of your portfolio or just some teams moving on or changing process. Maybe you use it as a staged migration to VSO.<br /><img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border: 0px;" title="clip_image004" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2014/12/clip_image0042.png" alt="clip_image004" width="664" height="209" border="0" /></li>
<li><strong>Consolidating Platforms on VSO</strong> - Many customers have Perforce, Git, TFS, SVN, or any of 50 different systems. I have customer that have one of everything.</li>
</ul>
<p>Like I said the story is not currently that good but you can read about each of the scenarios and see what the main issues are. We have also mapped tools to scenarios so that you can try to get started solving whatever your problems are:</p>
<ul>
<li>PDF: <a href="https://vsarguidance.codeplex.com/releases/view/178488" target="_blank">Understanding TFS migrations from on-premise to Visual Studio Online</a></li>
</ul>
<p>The ALM Rangers will also be releasing a walk-through for the simplest of migrations which is to use Excel for work items and do a tip migration of code. That will be coming real soon.</p>