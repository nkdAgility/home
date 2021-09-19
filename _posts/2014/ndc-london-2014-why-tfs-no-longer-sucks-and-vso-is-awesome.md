---
ID: 10980
post_title: 'NDC London 2014: Why TFS no longer sucks and VSO is awesome'
post_name: >
  ndc-london-2014-why-tfs-no-longer-sucks-and-vso-is-awesome
author: >
  Martin Hinshelwood (He/Him)
  nkdAgility.com
post_date: 2014-12-10 16:23:00
layout: post
link: >
  https://nkdagility.com/blog/ndc-london-2014-why-tfs-no-longer-sucks-and-vso-is-awesome/
published: true
tags:
  - Agile Planning Tools
  - Feedback Client
  - Git
  - Microsoft Test Manager
  - NDC
  - Test Management
  - TFS
  - VSTeamServices
categories:
  - News and Reviews
---
<p class="lead">I was in London last week to do a talk&nbsp;on why TFS no longer sucks&nbsp;entitled “<a href="http://nakedalmweb.wpengine.com/ndc-london-second-look-team-foundation-server-vso/" target="_blank" rel="noopener noreferrer">Second Look, Team Foundation Server &amp; VSO</a>”.&nbsp;I had a tone of preparatory work to do too make the demos smooth. The great god Murphy was however not smiling, but he was not angry. Some errors occurred, but no blue screens.</p>
There are many folks that have used older versions of TFS and dismissed future versions on that basis. However I wanted to do an end to end demonstration (soup to nuts) to show what TFS can bring to the table since it was updated in 2012. TFS prior&nbsp;to 2010 was a cumbersome, enterprise only endeavour and now it really is not. I have done demos before with install and configure of a local TFS server in under 30 minutes, so that part is easy. With the launch of Visual Studio Online (VSO) which is effectively Team Foundation Server (TFS) on steroids in the cloud most of the issues are gone while the stigma remains.&nbsp;

[embed]https://vimeo.com/113604455[/embed]

All of my demos were in VSO so that I could leverage the latest and greatest features, and everything I did could also be done on a local network.

https://twitter.com/ebrucucen/status/540480195363602432

I opted to follow&nbsp;the bug workflow story and I managed to get through almost everything I wanted. I skipped the Agile Planning walkthrough and a bug prevented me from getting through the bug workflow. Irony at its best. Also,&nbsp;note that I am playing&nbsp;four parts during the demo. I&nbsp;really should have had three hats or some&nbsp;other indicator of identity, but I think it&nbsp;Here are my actual notes for the demo above:

<strong>Part 1</strong>
<ol>
 	<li>PO sends Feedback Request to Stakeholder[PO]</li>
 	<li>Customer provides feedback and reports bug as part of review [STAKEHOLDER]</li>
 	<li>Product Owner breaks feedback down into new Backlog Items [PO]</li>
 	<li>[WALKTHROUGH: Agile Planning]</li>
 	<li>Product Owner assigns Feedback Response to Tester and request that they verify bug [PO]</li>
</ol>
<strong>Part 2</strong>
<ol>
 	<li>Tester uses exploratory testing and creates bug and test case [TEST]</li>
 	<li>[WALKTHROUGH: Microsoft Test Manager]</li>
 	<li>Product Owner approves the bug and requests that the Development Team expedite [PO]</li>
</ol>
<strong>Part 3</strong>
<ol>
 	<li>Development Team agrees to expedite bug if Sprint commitment reduced [Coder+Tester]</li>
 	<li>Coder finds and fixes the bug [Coder]</li>
 	<li>[WALKTHROUGH: Code Lens and Git]</li>
 	<li>Coder uses the Test Case to verify that they have fixed the bug [Coder]</li>
 	<li>[WALKTHROUGH: Test Management]</li>
 	<li>Automated deployment to “nkd-ff-f1” environment [TFS]</li>
 	<li>Tester verifies fix in “nkd-ff-f1” environment [TEST]</li>
 	<li>[WALKTHROUGH: Action Recording]</li>
</ol>
<strong>Part 4</strong>
<ol>
 	<li>Development Team agrees that the bug is DONE</li>
 	<li>Automated deployment to “nkd-ff-f2” environment [TFS]</li>
 	<li>Product Owner verifies bug and asks customer to check.</li>
</ol>
While almost everything went well I had two SNAFU’s during the demos that I did a little follow up on later.

<img style="background-image: none; padding-top: 0px; padding-left: 0px; margin: 0px; display: inline; padding-right: 0px; border: 0px;" title="image" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2014/12/image.png" alt="image" width="758" height="537" border="0"/>

First was that the Action Recording data collector in Microsoft Test Manager failed to start. It looks like while Windows 10 9860 was in sync the new update that got pushed out broke MTM. In Windows 10 9879 the version of .NET is slightly older than a bugfix that shipped just as Visual Studio 2015 Preview did. Unfortunately as .NET is bound to the OS and especially in a Preview OS I am stuck with MTM not working for now. I have also tested and verified in Visual Studio 2013 that the same issue occurs, but meh… preview bits on preview bits… can’t complain.

<img style="background-image: none; padding-top: 0px; padding-left: 0px; margin: 0px; display: inline; padding-right: 0px; border: 0px;" title="image" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2014/12/image1.png" alt="image" width="804" height="508" border="0"/>

The second error cam in the flavour of a release failure. As it turned out the simple deployment script that I created was a little too simple. IIS was hanging onto a file handle and this resulted in the first command not being able to delete all of the files. Even when logging onto the server I was unable to manually delete and someone, thanks by the way, shouted out to do an IIS Reset. Well that let me remove the lock and empty the folder. After doing a retry on the failed deployment all went as expected… So your simple deployment should really stop IIS, then update, before enabling it.

As part of prepping for this demo I did a bunch of work around release management and creating the release pipeline:
<ul>
 	<li><a href="http://nakedalmweb.wpengine.com/create-release-management-pipeline-professional-developers/" target="_blank" rel="noopener noreferrer">Create a Release Management pipeline for Professional Developers</a></li>
 	<li><a href="http://nakedalmweb.wpengine.com/create-standard-environment-release-management-azure/" target="_blank" rel="noopener noreferrer">Create a Standard Environment for Release Management in Azure</a></li>
 	<li><a href="http://nakedalmweb.wpengine.com/configure-a-dns-server-for-an-azure-virtual-network/" target="_blank" rel="noopener noreferrer">Configure a DNS server for an Azure Virtual Network</a></li>
 	<li><a href="http://nakedalmweb.wpengine.com/move-azure-vm-virtual-network/" target="_blank" rel="noopener noreferrer">Move your Azure VM to a Virtual Network</a></li>
 	<li><a href="http://nakedalmweb.wpengine.com/configuring-dc-azure-aad-integrated-release-management/" target="_blank" rel="noopener noreferrer">Configuring a DC in Azure for AAD integrated Release Management</a></li>
 	<li><a href="http://nakedalmweb.wpengine.com/create-log-entries-release-management/" target="_blank" rel="noopener noreferrer">Create log entries in Release Management</a> (coming <abbr>2014/12/12)</abbr></li>
 	<li><a href="http://nakedalmweb.wpengine.com/join-machine-azure-hosted-domain-controller/" target="_blank" rel="noopener noreferrer">Join a machine to your azure hosted domain controller</a> (coming <abbr>2014/12/17</abbr>)</li>
</ul>
Most of which became irrelevant when Release Management for VSO became available and I no longer had to configure a release management server myself. With the new release cadence from the TFS team, things can only get better…

My slides are available on Slide Share: <a href="http://www.slideshare.net/MrHinsh/ndclondon2014" target="_blank" rel="noopener noreferrer">http://www.slideshare.net/MrHinsh/ndclondon2014</a>