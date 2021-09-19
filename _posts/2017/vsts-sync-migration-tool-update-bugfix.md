---
ID: 11944
post_title: >
  VSTS Sync Migration Tool Update and
  Bugfix
post_name: vsts-sync-migration-tool-update-bugfix
author: >
  Martin Hinshelwood (He/Him)
  nkdAgility.com
post_date: 2017-06-21 14:08:00
layout: post
link: >
  https://nkdagility.com/blog/vsts-sync-migration-tool-update-bugfix/
published: true
tags:
  - Migration
  - Sync
  - TFS
  - vsts
categories:
  - DevOps
---
<p>The <a href="https://marketplace.visualstudio.com/items?itemName=nkdagility.vsts-sync-migration" target="_blank" rel="noopener noreferrer">VSTS Sync Migration tools</a> have been updated with new features and bug fixes for common issues reported by users.</p>
<p><a href="https://chocolatey.org/packages/vsts-sync-migrator/"><img src="https://camo.githubusercontent.com/30eda87c074e892c7b2126ffd0e6b1d3da7f710d/68747470733a2f2f696d672e736869656c64732e696f2f63686f636f6c617465792f762f767374732d73796e632d6d69677261746f722e737667" alt="Chocolatey" /></a></p>
<p>For those that are using TFS and VSTS since the demise of the TFS Integration Tools there has been a gap that has only been filled by commercial tools. For a while I have been shipping the <a href="https://marketplace.visualstudio.com/items?itemName=nkdagility.vsts-sync-migration" target="_blank" rel="noopener noreferrer">VSTS Sync Migration tool</a> as a stop gap measure until more features are available out of the box. If you are looking to:</p>
<ul>
	<li>Bulk update thousands of work items with regex pattern matches, and other field mappings.</li>
	<li>Migrate a partial or entire Team Project from one location to another, Collection, Account, or Server</li>
	<li>Merge two or more Team Projects that should not have been separated</li>
</ul>
<p>We have also had a number of awesome contributions from the community of users that have been using this tool to push work items around…and that has resulted in a number of new features in the last few months:</p>
<ul>
	<li><strong>Work Item History</strong> – Now you can migrate revisions as well as just the tip with the new <strong>WorkItemRevisionReplayMigrationContext</strong>  [<a href="https://github.com/hkoestin" target="_blank" rel="noopener noreferrer">Harald Koestinger</a>]</li>
	<li><strong>Query Migration</strong> - Migrate you Work Item Queries from one Team Project to another with the <strong>WorkItemQueryMigrationContext</strong> [<a href="https://github.com/rfennell" target="_blank" rel="noopener noreferrer">Richard Fennell</a>]</li>
	<li><strong>Closed Date on Tasks</strong> – Fixed a serious bug with the Closed Date that has been blocking a number of users [<a href="https://github.com/darryljamesheath" target="_blank" rel="noopener noreferrer">Darryl James Heath</a>]</li>
	<li><strong>Update Notification</strong> – When a new version is published through our automated DevOps pipeline you will be notified when you run the tool.</li>
</ul>
<p>We are working on the documentation, and folks struggle with the concept of the ReflectedWorkItemId that we use for tracking what you have already processed. Hopefully we can make some changes to fix this in the future.</p>
<p><a href="https://chocolatey.org/packages/vsts-sync-migrator/"><img src="https://camo.githubusercontent.com/30eda87c074e892c7b2126ffd0e6b1d3da7f710d/68747470733a2f2f696d672e736869656c64732e696f2f63686f636f6c617465792f762f767374732d73796e632d6d69677261746f722e737667" alt="Chocolatey" /></a></p>
<p>Install the latest version from chocolate and have it notify you when a new version comes out.</p>