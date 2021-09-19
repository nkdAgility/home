---
ID: 38238
post_title: >
  Getting started with a Definition of
  Done (DoD)
post_name: getting-started-definition-done-dod
author: >
  Martin Hinshelwood (He/Him)
  nkdAgility.com
post_date: 2020-12-14 13:03:00
layout: post
link: >
  https://nkdagility.com/blog/getting-started-definition-done-dod/
published: true
tags:
  - Agile
  - Definition of Done
  - Engineering Excellence
  - homepage
  - Scrum
  - Scrumble
categories:
  - Agility
  - DevOps
---
In my last post about Professional software teams creating working software David Corbin made a good point. How do you determining what "Free from fault or defect" means? Since that is different for each Product and may change over time you need to focus on Quality and reflecting that quality in a Definition of Done (DoD).
<h2>TL;DR;</h2>
Your Development Team is ultimately responsible for creating done increments of working software. Done Increments. Done.

Your Development Team needs to decide what Done means. They need to sit down and create a list of things that must be true for every Increment of software that they deliver. Working Software is not specific to a PBI; it's applied regardless of PBI to the entire delivery. Not just for each PBI.
<blockquote>"The increment must be in useable condition regardless of whether the Product Owner decides to release it."
-<a href="http://scrumguides.org">http://scrumguides.org</a></blockquote>
If you can't ship working software at least every 30 days then by its very definition, you are not yet doing Scrum. Since <a href="https://nkdagility.com/professional-scrum-teams-build-software-works/">Professional Scrum Teams build software that works</a>, stop, create a working increment of software that meets your definition of done (DoD), and then start Sprinting, and review what you mean by "working" continuously, and at least on a regular cadence.
<h2>What is a Definition of Done (DoD)</h2>
You need to start somewhere, and most often we don’t have a greenfield product. Either we are handed an existing product, or we are the team that built it and are switching to Scrum. Wherever your product originated, the code, and thus the product, will not currently be working software. How can it be when you don't have a definition of what working means? So what do you do?

Before you cut a single line of code, you need to decide what done means for your product and your company. It will be defined very differently if you are building firmware for pacemakers or if you are creating an e-commerce portal. Here are some characteristics of a Definition of Done:
<ul>
 	<li><b>A short, measurable checklist</b> - try and have things on your DoD that can be measured, that you can test the outcome, preferably in an automated fashion.</li>
 	<li><b>Mirrors shippable</b> - While you might not have shipped your product, <a href="https://nkdagility.com/continuous-deliver-sprint/">although we recommended it</a>, you should have that choice. Your Product Owner should be able to say, at the Sprint Review: "That’s Awesome… lets ship it.".</li>
 	<li><b>No further work</b> - There should be no further work required from the Development Team to ship your product. Any additional work means that you were not Done, and it takes away from the Product Owners capacity for the next iteration. Ideally, you have a fully automated process for delivering software, and <a href="https://nkdagility.com/a-better-way-than-staggered-iterations-for-delivery/">never use staggered iterations for delivery</a>.</li>
</ul>
Your short, measurable checklist that mirrors shippable and results in no further work required to ship your product needs to be defined. I find the best way to do this is to get the Scrum Team (the Product Owner plus the Development Team) into a facilitated DoD Workshop. Without a Defenition of Done we don't understand what working software means, and <a href="https://nkdagility.com/release-planning-and-predictable-delivery/">without working software we cant have predictable delivery</a>. Your <a href="https://nkdagility.com/the-fallacy-of-the-rejected-backlog-item/">Product Owner can't reject a Backlog Item</a>, only <span style="margin: 0px; color: black; font-family: 'Arial',sans-serif; font-size: 11pt;">whether</span> the Increment is working or not.
<h2>My first Definition of Done (DoD)</h2>
Your Definition of Done does not just magically appear, and your software does not magically comply. Making your Software comply with your definition of done is hard work, and while your definition of done should organically grow, you need to create the seed that you can build on.

I recommend that you run a workshop with the entire Scrum Team, and likely some other domain experts. If there are Stage Gates that your software has to pass after the Development Team is Done, then you need representatives from those Gates to participate in the workshop. Regardless of your product you likely need representatives with the following expertise; Code, Test, Security, UX, UI, Architecture, etc. You may have this expertise on your team, or you may need to bring in an expert from your organisation, or even external to your organisation.

Some examples of things to put on your definition of done:
<ul>
 	<li><b>Increment Passes SonarCube checks with no Critical errors</b> - You will be increasing over time, so maybe you need to say "<i>Code Passes SonarCube checks with no more than 50 Critical errors</i>" then work on it over time.</li>
 	<li><b>Increment's Code Coverage stays the same or gets higher</b> - Looking at a specific measure, like 90%, of code coverage is a read hearing and tells you nothing of code quality. However, it might be advantageous to monitor and measure for adverse change in code coverage, and we <a href="https://nkdagility.com/you-are-doing-it-wrong-if-you-are-not-using-test-first/">always advocate for TDD practices</a>.</li>
 	<li><b>Increment meets agreed engineering standards</b> - You should decide rules for naming of methods, tests, variables and everything in-between. Start small and add over time. Link to your agreed standards on a Wiki and continuously improve and expand your rules. Automate if possible.</li>
 	<li><b>Acceptance Criteria for Increment pass</b> - Making sure you at least meet the prescribed criteria is a laudable goal and <a href="https://nkdagility.com/you-are-doing-it-wrong-if-you-are-not-using-test-first/">automating them with ATDD practices</a> is even better.</li>
 	<li><b>Acceptance Tests for Increment are Automated</b> - Make sure that you automate all of your tests. If you think something will break, then you should have a test for it.</li>
 	<li><b>Security Checks Pass on Increment</b> - Use an automated tool as part of your build and check for known security vulnerabilities. You will not find all of your security issues, but at least don’t do things we know to be reflective of poor Security.</li>
 	<li><b>Increment meets agreed UX standards</b> - Again, have a Wiki page and make sure that you check it twice. If you are not using an automated DoD entry, then you need to agree as a Team that you have met the criteria.</li>
 	<li><b>Increment meets agreed Architectural Guidelines</b> - Wiki's are fantastic for this, but automate what you can.</li>
</ul>
Whatever Definition of Done you come up with it is unlikely that your entire Product currently meets the criteria. You are not yet doing Scrum. Before you start Sprinting, you need to focus on making sure that your current Increment meets your new Definition of Done. Focus on Quality, which is what the Development Team is accountable for, and make sure that your Increment meets that new quality bar before you start. The next Increment can only reach the quality bar of all those that came before do.

Create a Working Increment of Software that meets your definition of done and then start sprinting. Keeping your software in a working state <a href="https://nkdagility.com/getting-started-with-modern-source-control-system-and-devops/">will require a modern source control system that provides you with the facility to implement good DevOps</a> practices.
<h2>Growing your Definition of Done (DoD)</h2>
It's super important that quality is always increasing, and that means that you will need to at least reflect on your Definition of Done on a regular cadence. In Scrum, this cadence is defined by your Sprint length, and you have a Kaizen moment at the Sprint Retrospective. That does not mean that you don’t reflect on your DOD all the time, you do. You reflect continuously on <span style="margin: 0px; color: black; font-family: 'Arial',sans-serif; font-size: 11pt;">whether </span>your increment currently meets your DoD, and what you need to do to get it there. You should always be reflecting on <span style="margin: 0px; color: black; font-family: 'Arial',sans-serif; font-size: 11pt;">whether</span> your DoD fits your needs. If your Development Team finds that something is missing from the DoD halfway through the Sprint, then they should go ahead and add it, making sure that they are not endangering the Sprint Goal.

You may discover that you have a performance problem with your product as David Corbin pointed out in my previous post. How do we make sure that we fix that issue? As I see it there are two pieces to this once you are in flight. You can Scrumble (stop Sprinting because of poor quality), and fix it, or you can integrate this new knowledge into your product cycle.

If it is a significant issue that results in you not having working software, then you need to stop and fix. In Scrum, this is called a Scrumble, as a reflection that the Development Team stumbled because something is missing. You should stop adding new features and create Working Software before you continue Sprinting and adding new features. Once you have repaired the issue, you can increase your Definition of Done to make sure that all future Increments meet the new requirements.

If it is less significant, you might want to keep working and add what you need to your Product Backlog. You can then deliver improvements over the next few Sprints that mitigate and then resolve the identified issue. Once you have resolved it, you can then pin the outcome by adding something to your DoD.

<b>Always look for ways that you can increase your quality. What does your definition of done look like today?</b>