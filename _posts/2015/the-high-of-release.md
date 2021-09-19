---
ID: 11398
post_title: The High of Release
post_name: the-high-of-release
author: >
  Martin Hinshelwood (He/Him)
  nkdAgility.com
post_date: 2015-12-05 14:49:00
layout: post
link: >
  https://nkdagility.com/blog/the-high-of-release/
published: true
tags:
  - Developers
categories:
  - News and Reviews
---
<p>Just a week or so ago I was at Microsoft Future Decoded event in London to talk about the new Release Management tools that will be made available at <a href="https://channel9.msdn.com/Events/Visual-Studio/Connect-event-2015/" target="_blank">Connect()</a> and that might make it in to TFS 2015 Update 2. Here is hoping! The focus of the track was on DevOps and the focus of my session was on both Build and Release.</p><p>Microsoft have created a rich set of web based tooling that can allow you to build reliable release pipelines that meet the needs of your teams striving towards engineering excellence. My favourite thing about the new tooling is that rather than focus on building full stack tools, they are focusing on orchestration and integration. If you want to use Chef, Puppet, or Docker to physically release your software then that's up to you. If you want to use PowerShell DSC, or just plain old PowerShell, then you can do that as well. And if you just want to build a custom task to deploy your software using PowerShell, ShellScript, or anything else you desire, then you can do that to.</p><p>They are getting out of the game of forcing you to use their tachtical toolset while providing a versatile tool to help orchastrate your strategic vision. In short... its awesome! Check out my video below for a full demo...</p><p><iframe width="960" height="540" src="https://channel9.msdn.com/Events/FutureDecoded/Future-Decoded-2015-UK/15/player?format=html5" allowfullscreen="allowfullscreen" frameborder="0"></iframe></p><p>The new Release Management tools are completely web based and allow you to create a professional release pipeline right inside VSTS without the need for any other tools. The new Release Management tools are now in Public Preview on Visual Studio Team Services (VSTS) and you can use them to deploy from your on-premises TFS servers as well.</p><p>Many of my larger customers might still be working on being able to put their code in the cloud, but they have no problems with deploying the output of their builds to cloud environments on Azure or elsewhere.</p><p>Over the next few months I am hoping to get some local build output deployed to Azure where I can spin up 100 servers to deploy my application for the local testers. I will let you know how I get on...</p>