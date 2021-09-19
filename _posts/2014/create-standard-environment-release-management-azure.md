---
ID: 10923
post_title: >
  Create a Standard Environment for
  Release Management in Azure
post_name: >
  create-standard-environment-release-management-azure
author: >
  Martin Hinshelwood (He/Him)
  nkdAgility.com
post_date: 2014-12-04 11:30:00
post_excerpt: '<p class="lead">Next week I will be <a href="http://nakedalmweb.wpengine.com/ndc-london-second-look-team-foundation-server-vso/">speaking at NDC London 2014</a> and I have been working on my demo. Since Connect() everything for a little bit easier and I need to create an environment for Release Management for Visual Studio 2013.</p>'
layout: post
link: >
  https://nkdagility.com/blog/create-standard-environment-release-management-azure/
published: true
tags:
  - Application Insights
  - Azure
  - Cloud Service
  - Continious Value Delivery
  - IAAS
  - Release Management
  - Resource Group
  - Standard Environments
  - Virtual Network
  - VSTeamServices
categories:
  - 'Install &amp; Configure'
  - 'Tools &amp; Techniques'
---
<p class="lead">Next week I will be <a href="http://nakedalmweb.wpengine.com/ndc-london-second-look-team-foundation-server-vso/">speaking at NDC London 2014</a> and I have been working on my demo. Since Connect() everything for a little bit easier and I need to create an environment for Release Management for Visual Studio 2013.</p>
<p>I have been working on a new end to end (soup to nuts) demo for Visual Studio ALM that [tells a story] and shows what it can do. My presentation at NDC London is aimed at those folks that have used older versions of TFS in the past and kinda think it sucks. I think they are wrong, and I want to prove it. So for the last week I have been creating a demo using:</p>
<ul>
<li><strong>Visual Studio Online (VSO)</strong> - TFS hosted by Microsoft so zero hassle.</li>
<li><strong>Release Management for VSO</strong> - Hosted Release Management that connects to Visual Studio Online, again with the zero hassle.</li>
<li><strong>Visual Studio 2015 Preview</strong> - coz, well, its out and it works.</li>
<li><strong>Git </strong>- for source control there is no better platform</li>
<li><strong>Application Insights</strong> - free way to gather swim data for your applications.</li>
</ul>
<p>The idea is to show an end to end resolution of a bug from it being reported to is being fixed using all of the tools that come, out of the box, with Visual Studio ALM. I will be using the Fabrikam Fiber code, imported into a Git repo and linked to work items in TFS.</p>
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; margin: 0px; display: inline; padding-right: 0px; border: 0px;" title="clip_image001[6]" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2014/12/clip_image0016.png" alt="clip_image001[6]" width="804" height="502" border="0" /></p>
<p>I have already configured an automated deployment to one of my environments and every check-in is magically deployed to the server. This, while sitting in Azure, is just a Virtual Machine. I picked VM, or Standard Environment, so that I can emulate as closely as possible what you can do on premises.</p>
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; margin: 0px; display: inline; padding-right: 0px; border: 0px;" title="clip_image002[6]" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2014/12/clip_image0026.png" alt="clip_image002[6]" width="804" height="389" border="0" /></p>
<p>For this I need a Feedback 2 environment and for that I need to configure it in Azure. Many of the steps and capabilities are just the same as for an on-premises environment but for Azure I don’t need to configure a domain, TFS, or Release Management servers. Indeed I don’t even need any hardware. I just need a credit card :).</p>
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; margin: 0px; display: inline; padding-right: 0px; border: 0px;" title="clip_image003[6]" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2014/12/clip_image0036.png" alt="clip_image003[6]" width="804" height="488" border="0" /></p>
<p>For my currently existing Feedback 1 (nkd-FF-F1) environment I have spent only £3.34 of my £99 MSDN Ultimate allotment and the expected total cost is less than £2 per day for a VM with 2 cores and 3.5GB of RAM. Merger but adequate for this purpose.</p>
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; margin: 0px; display: inline; padding-right: 0px; border: 0px;" title="clip_image004[6]" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2014/12/clip_image0046.png" alt="clip_image004[6]" width="804" height="488" border="0" /></p>
<p>If you are like me and you like things to be in order I recommend that you first create the Resource Group (Cloud Service) in the old portal (<a href="http://manage.windowsazure.com">http://manage.windowsazure.com</a>). The new portal does not give you good control over naming and as you can't rename stuff your resource group has a DNS name of the first resource added… poopy…</p>
<p>However if you create a Cloud Service in the old portal you get to name it and it becomes an empty container in the new portal. Simple, but effective. I actually find that I jump a lot between portals as the new one has a bunch of functionality that the old one does not. Its kinda fragmented just now and I know that Microsoft want just one, but the new portal is taking a while.</p>
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; margin: 0px; display: inline; padding-right: 0px; border: 0px;" title="clip_image005[6]" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2014/12/clip_image0056.png" alt="clip_image005[6]" width="804" height="488" border="0" /></p>
<p>Now that I have an empty Resource Group I want to add a server. Again the new portal is not going to cut it as you can't select a template: you can only select from the bits there. So… back to the old portal.</p>
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; margin: 0px; display: inline; padding-right: 0px; border: 0px;" title="clip_image006[6]" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2014/12/clip_image0066.png" alt="clip_image006[6]" width="647" height="537" border="0" /></p>
<p>The first task is to create a storage location. I want to be able to isolate all of the data so I will have a "nkdfff2" storage account. I really wish that the Azure team was consistent with naming as you can't use a "-" here. Might be a small issue but it peeves me off every time I hit it. It’s a stupid issue to have at all.</p>
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; margin: 0px; display: inline; padding-right: 0px; border: 0px;" title="clip_image007[6]" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2014/12/clip_image0076.png" alt="clip_image007[6]" width="619" height="537" border="0" /></p>
<p>Then comes the custom Virtual Network. If you want to have more than one server in your environment then you probably want to have a Virtual Network. Even though I only have one here, it’s a good exercise to create this. Ultimately you would want to script this out once you have a flow defined. I am only doing this twice, so scripting is a little bit of overkill at this point. But if I wanted many feedback environments I would want this scripted.</p>
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; margin: 0px; display: inline; padding-right: 0px; border: 0px;" title="clip_image008[6]" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2014/12/clip_image0086.png" alt="clip_image008[6]" width="781" height="537" border="0" /></p>
<p>We need somewhere to deploy out application. AS I am emulating Standard Environments I will be using a simple VM rather than a "Azure Website". This will better reflect a local instance of RM and TFS for folks. Unfortunately in the new portal you can't use the template gallery, or at least I could not figure out how. But on the old/current portal I can easily do this.</p>
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; margin: 0px; display: inline; padding-right: 0px; border: 0px;" title="clip_image009[6]" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2014/12/clip_image0096.png" alt="clip_image009[6]" width="804" height="514" border="0" /></p>
<p>You might ask why I would pick the Windows Server Technical Preview but I would say, why not :).</p>
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; margin: 0px; display: inline; padding-right: 0px; border: 0px;" title="clip_image010[6]" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2014/12/clip_image0106.png" alt="clip_image010[6]" width="804" height="512" border="0" /></p>
<p>Here I am using the same naming convention as for my other feedback environments and keeping to the A2 server size.</p>
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; margin: 0px; display: inline; padding-right: 0px; border: 0px;" title="clip_image011[6]" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2014/12/clip_image0116.png" alt="clip_image011[6]" width="804" height="495" border="0" /></p>
<p>We then get asked to select all of those little things that we just created. Pick the cloud service so that you have the right URL and address space. We have a network and storage account that we created earlier which, while overkill, emulates more accurately how you would actually create an environment. Due diligence recommends that you always run your environments, especially if they are multi server, in isolated vlans so that you can prevent any sort of cross access between them.</p>
<p>Large companies are really good at this but smaller ones usually just take the risks. If you are small however, Azure provides simple cheap isolation.</p>
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; margin: 0px; display: inline; padding-right: 0px; border: 0px;" title="clip_image012[6]" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2014/12/clip_image0126.png" alt="clip_image012[6]" width="804" height="495" border="0" /></p>
<p>Almost done; we have the VM running our favourite flavour of windows, or at least it will be once the provisioning has completed. Now to round out our Resource Group I want to bind some data collection for analytics.</p>
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; margin: 0px; display: inline; padding-right: 0px; border: 0px;" title="clip_image013[6]" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2014/12/clip_image0136.png" alt="clip_image013[6]" width="804" height="446" border="0" /></p>
<p>We should use the Application Insights for our application analytics even if we are building an on-premises application. Have you ever wondered what and how Microsoft gathers their "provide us feedback", well AI is an attempt to commercialise that capability for the rest of us.</p>
<p>You can track feature usage within your application be it Web, Windows, or Java. For some it is easier than others but both server and client data can be gathered.</p>
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; margin: 0px; display: inline; padding-right: 0px; border: 0px;" title="clip_image014[6]" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2014/12/clip_image0146.png" alt="clip_image014[6]" width="804" height="446" border="0" /></p>
<p>Again we need to give the resource, in this case the Application Insights data collector, a name so that we can refer to it later. Under the covers it gets a GUID that we will be using later.</p>
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border: 0px;" title="clip_image015[6]" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2014/12/clip_image0156.png" alt="clip_image015[6]" width="804" height="446" border="0" /></p>
<p>I now have a Resource Group (Cloud Compute) that is a representation of my Standard Environment that I can use for my application. Using Azure this is easy to configure and fast. Indeed I can extend the capabilities with more servers at almost the drop of a hat.</p>
<p>This environment contains:</p>
<ul>
<li><strong>Domain Name (nkd-ff-f2)</strong> - remember we had to use the old portal otherwise the new portal gives it a domain name of the first resource that requires one.</li>
<li><strong>Virtual Machine (nkd-ff-f2-svr01)</strong> - This is where we will be deploying our application and as it is IAAS (Infrastructure as a Service) it is identical to an on-premises instance.</li>
<li><strong>Application Insights (nkd-ff-f2-AI)</strong> - Collects the application analytics that we will push into our application. If you are deploying multiple applications on the same hardware you may want to separate the data.</li>
</ul>
<p>Next time I will be deploying an application to this environment that we created.</p>
