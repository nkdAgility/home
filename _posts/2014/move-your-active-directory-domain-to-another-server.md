---
ID: 10334
post_title: >
  Move your Active Directory domain to
  another server
post_name: >
  move-your-active-directory-domain-to-another-server
author: >
  Martin Hinshelwood (He/Him)
  nkdAgility.com
post_date: 2014-01-20 11:40:43
post_excerpt: >
  Have you ever tried to move your Active
  Directory domain to another server? Its
  not as easy as it looks. Here is some of
  the things that you need to do and look
  out for,
layout: post
link: >
  https://nkdagility.com/blog/move-your-active-directory-domain-to-another-server/
published: true
tags:
  - Active Directory
  - Domain
  - Server 2012 R2
  - TF255435
categories:
  - 'Install &amp; Configure'
---
<p>I was trying to install TFS 2013 yesterday and I found that my local demo domain was not working. After a little investigation It looks like I was running Windows Server 2012 R2 Preview and it had just expired.</p>
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; margin: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="image" alt="image" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2014/01/image.png" width="800" height="450" border="0" /><br /><small>Figure: Can’t install TFS if your domain is not working</small></p>
<p>So for the second time I had to navigate the treacherous jungle that is moving an Active Directory domain from one server to another. Changing your primary domain controller (PDC) is no simple task but if you hunt around ling enough on the internet you can pull together enough information to get it done.</p>
<p>[youtube=http://www.youtube.com/watch?v=yrpAYB2yIZU]<br /><small>Install &amp; Configure 301 - Move your Active Directory domain to another server</small></p>
<p>Just so you don’t miss anything you need to move:</p>
<ul>
<li>Schema Master</li>
<li>Domain Naming Master</li>
<li>The relative identifier (RID) operations master</li>
<li>The primary domain controller (PDC) emulator operations master</li>
<li>The infrastructure operations master</li>
</ul>
<p>And lets not forget the Global Catalogue.</p>
<p>The video documents my journey of moving my demo domain from one server to another and it currently looks like everything is working. Job done…</p>
<p>How did you get on moving your domain?</p>