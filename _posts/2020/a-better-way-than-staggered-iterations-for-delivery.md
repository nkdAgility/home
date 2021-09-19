---
ID: 9915
post_title: >
  A better way than staggered iterations
  for delivery
post_name: >
  a-better-way-than-staggered-iterations-for-delivery
author: >
  Martin Hinshelwood (He/Him)
  nkdAgility.com
post_date: 2020-12-10 09:00:00
post_excerpt: '<p class="lead">There is a better way than staggered iterations for delivery that will keep you on the path to agility.</p>'
layout: post
link: >
  https://nkdagility.com/blog/a-better-way-than-staggered-iterations-for-delivery/
published: true
tags:
  - Asynchronous development
  - Cross-functional teams
  - Culture
  - Cycle
  - Improve
  - Increment
  - Strategic
  - Test First
  - Working Software
categories:
  - 'People &amp; Process'
---
<p class="lead">There is a better way than staggered iterations for delivery that will keep you on the path to agility. Staggered iterations lead to more technical debt and lower quality software.</p>

<h2>TL;DR;</h2>
The expected result of staggered iterations would be an increase in rework and in technical debt. If you are moving from a 4-year iterative process to a 4-month one you will see the value, but your process will be opaque and will only reduce your ability to deliver working software.

Yes, your cycle time will be reduced, but you can do so much better. Move all requirements for shipping your software into your Sprint. If you need testing then it needs to be inside of the Sprint. A general rule is that:
<blockquote>If you need to validate something outside of the Sprint; User Acceptance, Security audit, regulatory aproval; Then you need to make sure that all of the work required to pass that outside validation is doing inside of the Sprint, with no further work required from the development team.
-<a href="https://nkdagility.com/company/about-martin-hinshelwood/">Martin Hinshelwood</a></blockquote>
For example, this means that if you have 6 weeks of animal trials, followed by 6 weeks of human trials to validate that your pacemaker firmware is good, you cant have those things happen inside of every 2 weeks Sprint. Instead, focus on what you can do to make those things pass. If they don't pass then do a full route-cause-analysis and bring that new information to your Sprint Retrospective and make sure you put measures in place to make sure it does not happen again.
<h2>A better way than staggered iterations for delivery</h2>
I have seen many companies that are trying to move towards greater agility get trapped in the past by creating artificial silos based on skills. They believe that by creating a timbox for planning, development and testing that we can get closer to agility and move away from our traditional models. Unfortunately, the actual result is to enshrine that traditional staged model and step sideways on the path to agility, not forwards. In many cases, it can be a significant step backwards that will take many painful years to rectify.

<img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="staggered-iterations-for-delivery" src="http://nakedalmweb.wpengine.com/files/2013/07/staggered-iterations-for-delivery.png" alt="staggered-iterations-for-delivery" width="629" height="366" border="0" />
Figure: Example of staggered iterations for delivery

I have heard this called many things. Water-Scrum-fall or maybe Scrummerfall but whatever you call it the reality is that this is just small waterfalls and in the case above not really that small at all. This is often how organisations respond when they are told to "do agile" and they end up figuring out how to not really change, and do the same thing that they have always done.

This is not the action of a <a href="https://nkdagility.com/scrum-tapas-importance-professionalism/">Professional Scrum Team</a>, but that of, at best amateurs and at worst cowboys.
<h2>The problem with staggered iterations for delivery</h2>
In the diagram above we have an 18 week cycle from inception to delivery. That’s more than 4 months between ideation and delivery with a lag of 2 months to even get feedback with a 2 month lag for all subsequent feedback. Worse this is the most expensive kind of feedback as the Coding and Testing teams have already moved on from the thing that is getting feedback and the result of that feedback will be more expensive to implement. Indeed worse yet if QA finds something that needs fixed we have maximised not only the cost to fix but the mean time to repair as the developers have moved on. And what do they do with that feedback? How is it prioritised? Do they quit what they are doing immediately and fix the previous iteration or do they wait until after they deliver this one? What if they are blocking QA? Does QA sit around till the end of the iteration after the one they reported the problem in?
<h2>The solutions to staggered iterations for delivery</h2>
We need to foster teams over individuals and make those teams responsible for the delivery of working software. To get that we need cross-functional teams that can turn ideas into that working software. And we need to do it often.
<ul>
 	<li><strong>Cross-functional teams</strong> – We need to have everyone on the Development Team that is required to turn the Backlog Item into working software. If you were a property developer you would have access to joiners, plumbers, plasterers and electricians. You would create a team of individuals that was sufficient to complete the daily work on site with experts on hand as needed. This is the same process for a Development Team. You should have all of the skills that you require on each team to turn the forecast backlog items into working software each  and every iteration. Have experts on hand for those tricky items but minimise the dependency that you have on them.</li>
 	<li><strong>Asynchronous development</strong> -  Ideally you want all of the disciplines that you need to complete each backlog item to work together to deliver the software. This is more than handing off between disciplines but moving towards everyone always working at any point in time. This is a hard one to achieve but is the responsibility of the team to figure out how; <a href="https://nkdagility.com/getting-started-with-modern-source-control-system-and-devops/">To achieve asynchronous development you will need a modern source control system</a>.</li>
 	<li><strong>Test first</strong> – Test first is about not doing any work unless there is a measurable test that elicits that work. Creating tests from acceptance criteria will make sure that your team is working on and understands the next most relevant thing to be worked on and that you have built what the customer wants. Additionally, creating unit tests before code will make sure that your coders are working on the most relevant problem, and that each line of code that they complete does exactly what they intended. The long term benefit of this is that we now have an executable specification that will result in an error if a future change breaks existing functionality. <a title="http://nakedalmweb.wpengine.com/you-are-doing-it-wrong-if-you-are-not-using-test-first/" href="https://nkdagility.com/you-are-doing-it-wrong-if-you-are-not-using-test-first/">You are doing it wrong if you are not using test first.</a></li>
 	<li><strong>Working software each iteration</strong> – If you don’t create working software at the end of each iteration you have no way of knowing what really needs to be done to create a working increment. If you do four iterations of two weeks before you think about creating a working increment, how much work (re-work really) is left that you need to complete to really be done? To really have shippable quality? If you don’t have working software at the end of each iteration you are making sure that your business can’t ship out of band, no matter how much it wants to; <a href="https://nkdagility.com/professional-scrum-teams-build-software-works/">Professional Scrum Teams build software that works</a>.</li>
 	<li><strong>Quality Assurance requires no testing</strong> – If you consider that all testing is done as part of the sprint, then the only thing that needs to be done as part of the QA gate is to review the test results and coverage and determine the sufficiency of those results and coverage. If you are taking more than four hours to QA two weeks of Development then I would suggest that the Development Teams work is not sufficient.</li>
</ul>
These things will all individually help and if you are doing all of them together your value delivery and quality should start to increase over time. Make sure that you focus on automating everything from the moment a Software Engineer checks in code, to it being <a href="https://nkdagility.com/continuous-deliver-sprint/">continuously delivered to production</a>. In the age of agility giving you a competitive advantage in whatever marketplace you are in, any manual work is a risk.
<h2>Who is naked Agility Limited - Martin Hinshelwood</h2>
<a href="https://nkdagility.com/company/about-martin-hinshelwood/">Martin Hinshelwood</a> is the <a href="https://nkdagility.com/" target="_blank" rel="noopener noreferrer" data-cke-saved-href="https://nkdagility.com/">Founder/CEO of naked Agility Limited</a> and has been their Principal Consultant and Trainer on DevOps &amp; Agility for four years. Martin is a <a href="https://www.scrum.org/martin-hinshelwood" target="_blank" rel="noopener noreferrer" data-cke-saved-href="https://www.scrum.org/martin-hinshelwood">Professional Scrum Trainer</a>, <a href="https://mvp.microsoft.com/en-us/PublicProfile/4021815?fullName=Martin%20John%20Hinshelwood" target="_blank" rel="noopener noreferrer" data-cke-saved-href="https://mvp.microsoft.com/en-us/PublicProfile/4021815?fullName=Martin%20John%20Hinshelwood">Microsoft MVP: Visual Studio and Development Technologies</a>, and has been Consulting, Coaching, and Training in DevOps &amp; Agility with Visual Studio, Azure, Team Services, and Scrum since 2010 and has been delivering software since 2000.
Martin is available for <a href="https://nkdagility.com/consulting/" target="_blank" rel="noopener noreferrer" data-cke-saved-href="https://nkdagility.com/consulting/">private consulting and training worldwide</a> and has many <a href="https://nkdagility.com/training/" data-cke-saved-href="https://nkdagility.com/training/">public classes across the globe</a>.