---
ID: 38300
post_title: Work can flow across the Sprint boundary
post_name: work-can-flow-across-sprint-boundary
author: >
  Martin Hinshelwood (He/Him)
  nkdAgility.com
post_date: 2018-01-30 20:12:00
layout: post
link: >
  https://nkdagility.com/blog/work-can-flow-across-sprint-boundary/
published: true
tags:
  - Developers
  - Flow
  - Scrum
  - The Sprint
categories:
  - News and Reviews
---
There is nothing in the Scrum Guide that says that you can't have workflow across the Sprint boundary. I'm going to suggest that not only can you, but you should as long as you don't endanger the Sprint Goal.
<h2>TL;DR;</h2>
The <a href="https://nkdagility.com/getting-started-definition-done-dod/">definition of Done</a> is an instrumental part of maintaining transparency of the past work and is not optional. The Sprint Goal provides focus and direction. In order to maintain flow we need to be able to reduce the batch size of the work, thus we must allow for work to flow across the Sprint boundary. If you have a Professional Scrum Team that is adept at creating <a href="https://nkdagility.com/professional-scrum-teams-build-software-works/">Done increments of working software</a> then introducing flow can improve the value delivered by increasing the throughput of the team.
<h2><img class="alignnone size-medium wp-image-38301" src="https://nkdagility.com/wp-content/uploads/2018/01/nkdagility-cross-sprint-boundary-800x390.png" alt="" width="800" height="390" /></h2>
Always remember that the Sprint is a container for Planning and not always for Delivery. Just like you can do Continuous Delivery in Scrum, so you can also introduce flow and Kanban. Less skilled teams can also benefit as long as you make sure that you meet the Sprint Goal and Done Increments are created to provide transparency of the past and build trust for the future.
<h2>Starting Work that the Development Team knows that it can't finish</h2>
Although you will not find anything in the Scrum Guide that prevents you from flowing work across Sprints you should consider it an advanced technique. Most teams that I work with are not even at the point where they have Working Software at the end of the Sprint and they are often only just achieving their Sprint Goal.

I also believed the myth that we could not flow work across the Sprint boundary. It took a long conversation with Steve and Daniel to kindle a different idea, and long discussions over a beer to make it concrete. My argument went; "If you have to be Done by the end of the Sprint then how can you have any unfinished work?" My argument was wrong! I was confusing the need to have a Done Increment with all of the PBI's being finished.

If you as a Development Team are practising Continuous Delivery (CD) then they always have working software. I would expect that a team doing CD would have every single element of their Definition of Done (DOD) automated and every Checkin/Pull Request meets the DOD. If that's true, then when you get to your Sprint Review you just show the work that you have finished.

<b>If you want Flow then <a href="https://nkdagility.com/continuous-deliver-sprint/">CD is no longer optional for a Software Team let along a Professional Scrum Team</a>.</b>
<h2>Shipping software with Unfinished work can still be Scrum</h2>
There are a number of Engineering consideration that a Development Team will need to take into account if they want to focus on Flow. With CD comes the need to validate early and often, with automation, so that you don’t have to stop and check everything manually. There are a number of practices that can help:
<ul>
 	<li><b>Feature Flags</b> - Often referred to as Feature Toggles this is a way to insert a switch into the code so that something is visible or not to the customer based on a switch. Advanced toggles might support "controlled Exposure" to customers, as well as A/B testing, and other features. Regardless it is generally accepted that you can't leave all of your toggles in the code indefinitely. Once you have completed the PBI / Feature or tested your hypothesis you need to remove the flag through Refactoring.</li>
 	<li><b>Refactoring</b> - The act of restructuring or rewriting code for clarity of purpose and future maintenance. One would never write a book or article and then just published it. You would normally do your first pass… re-read it and update for clarity. Maybe get someone else to take a look, and incorporate feedback. Same for code…</li>
 	<li><b>Test Driven Development (TDD)</b> - Part of the general Test First movement TDD allows an engineer to prove that the code that they wrote fulfils some pre-defined purpose. It’s the only way that a coder can prove that code does at least what they intended. This practice also supports refactoring since I can continue to prove that the code after I change it, does what was originally intended.</li>
 	<li><b>Many more</b>…</li>
</ul>
All of these are optional complimentary practices that help you achieve CD but it is not an exhaustive list. There are many other practices that will help, try them and see what works for your team.

While the Scrum Guide does not say that you need to do CD let alone the practices I have listed above, it does require that you create an Increment of Working Software at least once per Sprint. Anything less and you have no transparency of what was done. With no transparency, you lose your empirical process control, and without empiricism, you are not doing Scrum.

<b>Unfinished Backlog Items are not the same as Undone work.</b>
<h2>How does this impact Scrum elements</h2>
Within the bounds of the Scrum Framework, you are allowed to flow work from one Sprint to another. The Result is still Scrum if we have working software, and we meet the Sprint Goal.
<ul>
 	<li><b>Sprint Review</b> - the purpose of the Sprint Review is to inspect what was just created, review and analysis it, and update the Product Backlog to be an accurate reflection of future work based on this new Increment. At the Sprint Review, we show the work that was completed and discuss what was not completed. It's not a failure if the team did not finish something, software development is complex and that will happen, often. As long as we have an Increment of Done work we have fulfilled our obligation to Empirical process control.</li>
 	<li><b>Sprint Planning</b> - The purpose of the Sprint Planning event is to inspect the Product Backlog and create a Sprint Goal, Forecast, and Sprint Backlog for this Sprint. Nothing prevents Stories flowing over into the next Sprint unless it prevents the team cresting a Done Increment, or endangers the Sprint Goal.</li>
 	<li><b>Sprint Goal</b> - The Sprint Goal provides purpose and direction for the team. And that does not mean that we can't have work outside that Sprint Goal inside of the Sprint. We may have production issues, leftover work, or just something super important to the Product Owner that turns up. As long as the team believes that they can achieve the Sprint Goal they can take on any additional work that makes sense.</li>
</ul>
I have found that reading the Scrum Guide carefully, turns up all sorts of miss conceptions that we all have as we interpret and use Scrum. If you are not sure, re-read the Scrum Guide, maintain the Scrum Values, focus on empirical process control and maintain transparency.

At the end of every Sprint, you should have working Software that meets your definition of Done and you should have meat your Sprint Goal.