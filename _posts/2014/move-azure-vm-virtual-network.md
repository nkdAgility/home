---
ID: 10874
post_title: Move your Azure VM to a Virtual Network
post_name: move-azure-vm-virtual-network
author: >
  Martin Hinshelwood (He/Him)
  nkdAgility.com
post_date: 2014-11-19 15:49:20
layout: post
link: >
  https://nkdagility.com/blog/move-azure-vm-virtual-network/
published: true
tags:
  - Azure
  - Release Management
  - virtual machines
  - Virtual Network
categories:
  - 'Install &amp; Configure'
---
<p>When I first completed <a href="http://nakedalmweb.wpengine.com/configuring-dc-azure-aad-integrated-release-management/">configuring a DC in Azure for AAD integrated Release Management</a> I did not add my virtual machine to a virtual network. And I really should have and in the usual poopyness that is servers you can't move it. You effectively need to delete your VM leaving the disks and create a new machine definition that is correctly configured.</p>
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; margin: 0px; display: inline; padding-right: 0px; border: 0px;" title="clip_image001" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2014/11/clip-image0011.png" alt="clip_image001" width="800" height="395" border="0" /></p>
<p>First we need to configure the virtual network. Create a new virtual network in the correct region. The region should be the same as the one that you want to create the vm's in, in my case western Europe fits that bill.</p>
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; margin: 0px; display: inline; padding-right: 0px; border: 0px;" title="clip_image002" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2014/11/clip-image0021.png" alt="clip_image002" width="800" height="395" border="0" /></p>
<p>Then the poopy part, we need to delete the Virtual Server that we created and promoted to be a domain controller. Make sure that you do not delete the disks.</p>
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; margin: 0px; display: inline; padding-right: 0px; border: 0px;" title="clip_image003" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2014/11/clip-image0031.png" alt="clip_image003" width="800" height="395" border="0" /></p>
<p>We now need to create a new VM in the correct domain. Give it a few minutes to clear the name in the tubes of Azure so that we can reuse it and then create a new VM but select the Gallery.</p>
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; margin: 0px; display: inline; padding-right: 0px; border: 0px;" title="clip_image004" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2014/11/clip-image0041.png" alt="clip_image004" width="800" height="395" border="0" /></p>
<p>In the gallery you should find a "my disks" section at the very bottom that lists all of your free floating disks that are not attached to a VM. I found that one of my servers did not exist and I had to wait a few more minutes for it to show up. Select your disks and click next…</p>
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; margin: 0px; display: inline; padding-right: 0px; border: 0px;" title="clip_image005" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2014/11/clip-image0051.png" alt="clip_image005" width="800" height="395" border="0" /></p>
<p>Give the machine the same name and pick the A0 instance size that we wanted before. We should not have to log into the server at this time.</p>
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; margin: 0px; display: inline; padding-right: 0px; border: 0px;" title="clip_image006" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2014/11/clip-image0061.png" alt="clip_image006" width="800" height="395" border="0" /></p>
<p>On the second screen we need to make sure that we select the virtual network that we just created. This will alter the other options that we can select but it is very simple to configure. On the next screen you need only pick what additional bits that you want and I only really want the VM tools for an AD box, but for other boxes you may want more.</p>
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border: 0px;" title="clip_image007" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2014/11/clip-image0071.png" alt="clip_image007" width="800" height="395" border="0" /></p>
<p>You should now see your domain controller as part of your virtual network that we just created. Even if we have many cloud services we can add their containing machines to this network and allow communication between them.</p>
<p><strong>Useful links:</strong></p>
<ul>
<li><a href="http://azure.microsoft.com/en-us/documentation/articles/active-directory-new-forest-virtual-machine/#createvnet" target="_blank">http://azure.microsoft.com/en-us/documentation/articles/active-directory-new-forest-virtual-machine/#createvnet</a></li>
<li><a href="http://msdn.microsoft.com/library/azure/dn630228.aspx" target="_blank">http://msdn.microsoft.com/library/azure/dn630228.aspx</a></li>
<li><a href="http://blogs.msdn.com/b/walterm/archive/2013/05/29/moving-a-virtual-machine-from-one-virtual-network-to-another.aspx" target="_blank">http://blogs.msdn.com/b/walterm/archive/2013/05/29/moving-a-virtual-machine-from-one-virtual-network-to-another.aspx</a></li>
</ul>