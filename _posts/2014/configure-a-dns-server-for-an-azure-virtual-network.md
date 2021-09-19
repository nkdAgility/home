---
ID: 10878
post_title: >
  Configure a DNS server for an Azure
  Virtual Network
post_name: >
  configure-a-dns-server-for-an-azure-virtual-network
author: >
  Martin Hinshelwood (He/Him)
  nkdAgility.com
post_date: 2014-11-26 15:53:34
post_excerpt: '<p class="lead">I just got done <a href="http://nakedalmweb.wpengine.com/configuring-dc-azure-aad-integrated-release-management/">configuring a DC in Azure for AAD integrated Release Management</a> and I need to now Configure a DNS server for an Azure Virtual Network</p>'
layout: post
link: >
  https://nkdagility.com/blog/configure-a-dns-server-for-an-azure-virtual-network/
published: true
tags:
  - Azure
  - DNS
  - Virtual Network
categories:
  - 'Install &amp; Configure'
---
<p class="lead">I just got done <a href="http://nakedalmweb.wpengine.com/configuring-dc-azure-aad-integrated-release-management/">configuring a DC in Azure for AAD integrated Release Management</a> and I need to now Configure a DNS server for an Azure Virtual Network. This will tell Azure that any servers that are added to this virtual network should use this DNS server. This should allow any machine added to this virtual network to be able to join the domain that we have configured.</p>
<p>Before we can set a DNS server default we need to have a fixed IP Address for the server. Although DNS provides name resolutions so that we do not need to use IP's all the time you need a place to start. In the big bad internet there are 'name servers' that start the ball rolling that exist at a well known level. Within our virtual network we need to create our own well known starting point.</p>
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; margin: 0px; display: inline; padding-right: 0px; border: 0px;" title="clip_image001" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2014/11/clip-image0012.png" alt="clip_image001" width="800" height="356" border="0" /></p>
<p>There is a simple command to give your server a fixed IP within your virtual network. You can apply it to any server and it allows the internal virtual network IP to persist even if you turn off the server. This does not affect the external IP.</p>
<pre class="lang:default decode:true ">Get-AzureVM -ServiceName nkd-infra -Name nkd-inf-svrdc01 | Set-AzureStaticVNetIP -IPAddress 10.0.0.4 | Update-AzureVM</pre>
<p>&nbsp;There is also a 'check IP' command that, as I only currently have a single server is a little pointless. I just set the servers current IP as the fixed IP for the future.</p>
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; margin: 0px; display: inline; padding-right: 0px; border: 0px;" title="clip_image002" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2014/11/clip-image0022.png" alt="clip_image002" width="800" height="395" border="0" /></p>
<p>We first need to create a DNS server definition that we can select later. Here we simply set the name and IP of the DNS server to create a registration of that DNS server.</p>
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border: 0px;" title="clip_image003" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2014/11/clip-image0032.png" alt="clip_image003" width="800" height="395" border="0" /></p>
<p>We then need to go to the virtual network that we created and tell it that the DNS server should be the one to use. If we had a large network we may set more than one DNS server, but in this case we are just pottering around with the configuration for demos. Select the network and go to the configuration tab. Here we can select our pre-created DNS server.</p>
<p>If you create new machines, or reboot the existing machines in the virtual network, they will then be given this DNS server when DHCP assigns configuration. In this way you can create quite complicated network configurations and even create backup domains controllers to allow you to extend your local network to the cloud.</p>
