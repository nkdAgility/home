---
ID: 10865
post_title: >
  Configuring a DC in Azure for AAD
  integrated Release Management
post_name: >
  configuring-dc-azure-aad-integrated-release-management
author: >
  Martin Hinshelwood (He/Him)
  nkdAgility.com
post_date: 2014-11-14 15:24:52
layout: post
link: >
  https://nkdagility.com/blog/configuring-dc-azure-aad-integrated-release-management/
published: true
tags:
  - Active Directory
  - Azure
  - Azure Active Directory
  - Release Management
  - Release Management Server
categories:
  - 'Install &amp; Configure'
---
<p>I will be <a href="http://nakedalmweb.wpengine.com/ndc-london-second-look-team-foundation-server-vso/">speaking at NDC London: Second Look, Team Foundation Server &amp; VSO</a> and I am planning to be a little adventurous with the demo. For this I will be configuring a DC in Azure for AAD integrated Release Management so that I can do cloud demos.</p>
<p>While potentially similar to the <a href="http://blogs.msdn.com/b/briankel/archive/2013/08/02/visual-studio-2013-application-lifecycle-management-virtual-machine-and-hands-on-labs-demo-scripts.aspx">Brian Keller VM demos</a> I wanted a more end to end solution that was a little more real world. I decided to run everything in Azure after the success of <a href="http://nakedalmweb.wpengine.com/creating-training-virtual-machines-azure/">configuring the BKVM in Azure for Training</a>. I can make no guarantees that this will end up as the final demo, but it will be fun to build.</p>
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="clip_image001" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2014/11/clip-image001.png" alt="clip_image001" width="800" height="452" border="0" /></p>
<p>The first environment that I need is my permanent infrastructure. Top left in the diagram. I need to be able to join a bunch of computers to domain and sync that domain with AAD. All in the cloud.</p>
<div class="bs-callout bs-callout-info">
<h4>Note</h4>
<p>It would be far superior if I was able to just join any machine that I like to an AAD domain. However, currently, there is no support for a direct join. You need to have the traditional static domain for now.</p>
</div>
<h3>Creating the virtual machine in Azure for Active Directory</h3>
<p>Creating a new machine is almost the bread and butter of Azure. You can create as many machines as you can afford and anything from small, to large, to really enormous. There is the A series machines that are cheap and cheerful. They are the slowest options and good for low demand operations, like active directory.</p>
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="clip_image002" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2014/11/clip-image002.png" alt="clip_image002" width="800" height="431" border="0" /></p>
<p>You first need to have a cloud service to add your machine to. This is a little bit like a resource group as each cloud service is limited to a certain number of cores, with that defaulting to 20.</p>
<div class="bs-callout bs-callout-info">
<h4>Note</h4>
<p>You can send a support request to get the number of available cores increased as I did when I was <a href="http://nakedalmweb.wpengine.com/creating-training-virtual-machines-azure/">setting up training VM's</a> for my recent course.</p>
<p>So head from <a href="http://manage.microsoftazure.com">http://manage.microsoftazure.com</a> to "Cloud Services | New" to pop the menu and select "Quick Create" and fill out your details. You can't move region later so pick the right one now, closest to the consumers. In this case I want "West Europe".</p>
</div>
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="clip_image003" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2014/11/clip-image003.png" alt="clip_image003" width="800" height="437" border="0" /></p>
<p>We also need a storage location to store the hard disks for our VM's.</p>
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="clip_image004" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2014/11/clip-image004.png" alt="clip_image004" width="800" height="431" border="0" /></p>
<p>Now we have our cloud service we can get going creating the first VM that will be the Domain Controller (DC). Select "Virtual Machines | New" to pop the menu and choose "From Gallery".</p>
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="clip_image005" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2014/11/clip-image005.png" alt="clip_image005" width="800" height="431" border="0" /></p>
<p>Now, I'm a progressive kinda guy and there is already a listing for Windows Server Technical Preview and that’s what I will be using. This applies to all of my servers that I create and I would only use something else if I encounter a problem with an application. I feel that this is low risk as they are now on a cadence of making smaller changes more frequently. Much more likely to find and fix the issue in the integration the fewer things that you have changed at once.</p>
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="clip_image006" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2014/11/clip-image006.png" alt="clip_image006" width="800" height="431" border="0" /></p>
<p>For a domain controller you really don’t need much oomph… however to use the machine interactively you really don’t want it to lag… so for install and configuration I will run an A2 (2 cores and 3GB RAM), and then once I am done I will downgrade it to a A0 (shared core, 0.9GB RAM). That’s plenty for a domain controller. If I need to physically configure the machine later then more power is only a reboot away.</p>
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="clip_image007" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2014/11/clip-image007.png" alt="clip_image007" width="800" height="433" border="0" /></p>
<p>You should at this point go off and create a network to add your server to. That will save you having to [Move your Domain Controller Azure VM to a Virtual Network] at a later time. Alas I did not know that for now and so I just configured it for the West Europe data centre and all the trappings of storage and cloud service.</p>
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="clip_image008" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2014/11/clip-image008.png" alt="clip_image008" width="800" height="436" border="0" /></p>
<p>There are lots of cool options for managing your server and deploying bits to it if you want, but this is going to be a simple light weight DC.</p>
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="clip_image009" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2014/11/clip-image009.png" alt="clip_image009" width="800" height="422" border="0" /></p>
<p>Woo… after a few minutes I can then log onto my server and tinker. If you find it to slow you can head to the "Configure" tab and bump up the server. Like I said… I bumped to A2 for interactive configuring.</p>
<h3>Install Active Directory required components</h3>
<p>Installing active directory in your VM on Azure is uncannily identical to installing it on any other machine. That’s because it is! So if you know how to do this bit you can skip to the end.</p>
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="clip_image010" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2014/11/clip-image010.png" alt="clip_image010" width="800" height="450" border="0" /></p>
<p>Everything in Windows is added using the "add roles and features" wizard. To be honest it just build a little PowerShell and that does all the work… and I use PowerShell… but not when there is a perfectly servable UI.</p>
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="clip_image011" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2014/11/clip-image011.png" alt="clip_image011" width="800" height="450" border="0" /></p>
<p>Active Directory is a Server Roll and it’s a simple checkbox away. When you check it the wizard will ask you to add a bunch of other stuff. It’s a bunch of management tools and the PowerShell commandlets. Those might be useful later.</p>
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="clip_image012" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2014/11/clip-image012.png" alt="clip_image012" width="800" height="450" border="0" /></p>
<p>You also need to add the DNS role as active directory relies very heavily on dynamic dns for resolutions. The AD wizard will automatically populate this stuff for you so you will not need to configure it separately.</p>
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="clip_image013" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2014/11/clip-image013.png" alt="clip_image013" width="800" height="450" border="0" /></p>
<p>Whoh… can you even add a static IP in Azure? For a DNS server to work it needs to have the same IP address. It is the thing that is going to be providing resolution for your other servers and they need to known where to find it. Turns out you can easily <a href="http://nakedalmweb.wpengine.com/configure-a-dns-server-for-an-azure-virtual-network/?preview=true">configure a static ip for a dns server in your virtual network</a>.</p>
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="clip_image014" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2014/11/clip-image014.png" alt="clip_image014" width="800" height="450" border="0" /></p>
<p>Following the lead of the TFS team it looks like all of Microsoft products are moving to a model where you keep installation and configuration separate. This is a far less error prone model than the traditional all in one model.</p>
<p>Now that we have the bits installed we can move to configuration.</p>
<h3>Promote your Azure VM to be a domain controller</h3>
<p>With Active Directory we are doing a lot more than just adding a capability to our server. This is not the same as setting up IIS, we are changing the fundamental way that this server functions.</p>
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="clip_image015" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2014/11/clip-image015.png" alt="clip_image015" width="800" height="450" border="0" /></p>
<p>You should see a little triangle after the installation is complete prompting you to "promote this server to domain controller". So lets go ahead and give this server special powers.</p>
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="clip_image016" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2014/11/clip-image016.png" alt="clip_image016" width="800" height="450" border="0" /></p>
<p>As we are starting from scratch we need to create a whole new infrastructure. For this we need to "add a new forest" and give it a DNS name. I have been through this a few times and favour "env.mydomain.com" for this. If I was creating a primary production domain I would use the same name as my public domain, and I would never…ever… pick mydomain.local.</p>
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="clip_image017" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2014/11/clip-image017.png" alt="clip_image017" width="800" height="450" border="0" /></p>
<p>There are quite a few configuration screens and I am not going to bore you with them all you have to set your NetBIOS name ("nakedalm") and where you want your data to reside but most of the screens are fairly self-explanatory. However the DNS screen will give you an error if you ticked the DNS option, as I did, during the feature selection. The result of that wordy warning is that "no action is required" so we are good.</p>
<pre class="lang:default decode:true ">Import-Module ADDSDeployment
Install-ADDSForest `
-CreateDnsDelegation:$false `
-DatabasePath "C:\Windows\NTDS" `
-DomainMode "Win2012R2" `
-DomainName "env.nakedalmweb.wpengine.com" `
-DomainNetbiosName "nkdalm" `
-ForestMode "Win2012R2" `
-InstallDns:$true `
-LogPath "C:\Windows\NTDS" `
-NoRebootOnCompletion:$false `
-SysvolPath "C:\Windows\SYSVOL" `
-Force:$true</pre>
<p>&nbsp;<img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="clip_image018" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2014/11/clip-image018.png" alt="clip_image018" width="800" height="450" border="0" /></p>
<p>Check the configuration, ignore the warnings and away we go… I do however miss the "this will take some time… or considerably longer" message the old AD installation had, however it was pretty quick…</p>
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="clip_image019" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2014/11/clip-image019.png" alt="clip_image019" width="800" height="450" border="0" /></p>
<p>At some point you will be asked to sign out and your server will be restarted to be embowed with the powers of AD.</p>
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="clip_image020" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2014/11/clip-image020.png" alt="clip_image020" width="800" height="450" border="0" /></p>
<p>When it comes back up you will no longer be able to log into your server locally and will log into the domain. Your local accounts will have been converted to domains accounts and will be listed in Active Directory Users and Computers.</p>
<p>Now that you have completed the install you can drop the server down to the A0 machine level to save money.</p>
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="clip_image021" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2014/11/clip-image021.png" alt="clip_image021" width="387" height="452" border="0" /></p>
<p>We effectively drop down to 11p per day for the server. I am sure that if we started hitting it with loads of domain joined machines then I expect the price to go up, however this minimalist cost can be easily supported with your MSDN benefits…</p>
