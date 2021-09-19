---
ID: 10892
post_title: >
  Join a machine to your azure hosted
  domain controller
post_name: >
  join-machine-azure-hosted-domain-controller
author: >
  Martin Hinshelwood (He/Him)
  nkdAgility.com
post_date: 2014-12-31 15:01:12
post_excerpt: '<p class="lead">Now that you have finished <a href="http://nakedalmweb.wpengine.com/move-azure-vm-virtual-network/">moving your Domain Controller Azure VM to a Virtual Network</a>] you need to be able to join a machine to your azure hosted domain controller.  </p>'
layout: post
link: >
  https://nkdagility.com/blog/join-machine-azure-hosted-domain-controller/
published: true
tags:
  - Active Directory
  - Azure
categories:
  - 'Install &amp; Configure'
---
<p class="lead">Now that you have finished <a href="http://nakedalmweb.wpengine.com/move-azure-vm-virtual-network/">moving your Domain Controller Azure VM to a Virtual Network</a>] you need to be able to join a machine to your azure hosted domain controller.</p>
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; margin: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="clip_image001" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2014/11/clip-image0014.png" alt="clip_image001" width="800" height="395" border="0" /></p>
<p>You need to make sure that you have your machine within the correct virtual network, and <a href="http://nakedalmweb.wpengine.com/move-azure-vm-virtual-network/">move your Azure VM to a Virtual Network</a> if necessary. On top of that you need to have the your <a href="http://nakedalmweb.wpengine.com/configure-a-dns-server-for-an-azure-virtual-network/">domains DNS server configured for your virtual network</a> so that the guest machine knows where to look for the domain.</p>
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; margin: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="clip_image002" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2014/11/clip-image0024.png" alt="clip_image002" width="800" height="395" border="0" /></p>
<p>If everything is in order you should connect to the VM you want to join to the domain that you have created. On the Dashboard tab of the VM you should see a 'connect' button at the bottom of the screen. Clicking it will launch Remote Desktop and connect it to the server.</p>
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; margin: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="clip_image003" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2014/11/clip-image0034.png" alt="clip_image003" width="800" height="450" border="0" /></p>
<p>Once on the server the DBS setting should be correctly configured automatically as part of the DHCP for the Virtual Network that we configured before. This should make it fairly simple to join the machine to the domain. This is no different from local domains.</p>
<p><span class="label lable-info">Note</span> What I really want is to be able to join these machines to AAD so that I do not have to maintain a separate set of local domain controllers for this purpose. For me it gets a little more complex as I have no physical servers, only Azure and Office 365.</p>
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; margin: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="clip_image004" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2014/11/clip-image0043.png" alt="clip_image004" width="800" height="450" border="0" /></p>
<p>If you right-click on the start button and select "System" you will see the current machine name and domain affiliation. Most likely it will be "Workshop". To make the change we need to click "Change Settings" to open the dialogs.</p>
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="clip_image005" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2014/11/clip-image0053.png" alt="clip_image005" width="800" height="450" border="0" /></p>
<p>Set the radio-button to "Domain" and enter the name of the domain that you want to join. As I setup "env.nakedalmweb.wpengine.com" that is what I need to enter. Once you click "OK" you will be asked for a domain administrator account to join the machine.</p>
<p>After that a simple reboot will allow you to login to the domain with any of the domain accounts that you have configured.</p>