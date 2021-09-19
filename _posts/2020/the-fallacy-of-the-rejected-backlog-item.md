---
ID: 9876
post_title: The fallacy of the rejected backlog item
post_name: the-fallacy-of-the-rejected-backlog-item
author: >
  Martin Hinshelwood (He/Him)
  nkdAgility.com
post_date: 2020-07-13 09:55:00
post_excerpt: '<p class="lead">To my understanding there is a frustrating misunderstanding of reality when one thinks that the Product Owner can reject a single story at the Sprint Review. This is the fallacy of the rejected backlog item.</p>'
layout: post
link: >
  https://nkdagility.com/blog/the-fallacy-of-the-rejected-backlog-item/
published: true
tags:
  - Sprint Review
categories:
  - 'People &amp; Process'
---
<p class="lead">There is a frustrating misunderstanding of reality when one thinks that the Product Owner can reject a single story at the Sprint Review. This is the fallacy of the rejected backlog item and the misguided belief that this backlog item can just be left out of this delivery. That backlog item that was chosen by the Development Team at the Sprint Planning event to help them achieve the Sprint Goal. The Sprint Goal that created focus and has the entire Development Team working in the same area of the codebase.</p>
The fallacy is that without this single Backlog Item, one of many, the code will still function as intended.
<h2>TL;DR;</h2>
Since the Development Team is held accountable for quality, but not quantity, and they sure cant be held accountable for meeting expectation.
<ul>
 	<li><strong>DONE</strong> - If in the pursuit of the Sprint Goal the output of the Sprint is a DONE Increment of working software then the Development Team did everything they were required to do. Any gap between what was delivered and expectation is merely a learning opportunity. At the Sprint Review, the Scrum Team investigates this gap and updates the Product Backlog to reflect what is now needed next.</li>
 	<li><strong>NOT DONE</strong> - <span style="display: inline !important; float: none; background-color: transparent; color: #333333; cursor: text; font-family: -apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,Oxygen-Sans,Ubuntu,Cantarell,'Helvetica Neue',sans-serif; font-size: 16px; font-style: normal; font-variant: normal; font-weight: 400; letter-spacing: normal; orphans: 2; text-align: left; text-decoration: none; text-indent: 0px; text-transform: none; -webkit-text-stroke-width: 0px; white-space: normal; word-spacing: 0px;">If the Development Team is not “Done” at the end of the Sprint then there are some consequences:</span>
<ul>
 	<li><span style="display: inline !important; float: none; background-color: transparent; color: #333333; cursor: text; font-family: -apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,Oxygen-Sans,Ubuntu,Cantarell,'Helvetica Neue',sans-serif; font-size: 16px; font-style: normal; font-variant: normal; font-weight: 400; letter-spacing: normal; orphans: 2; text-align: left; text-decoration: none; text-indent: 0px; text-transform: none; -webkit-text-stroke-width: 0px; white-space: normal; word-spacing: 0px;">An increase in Technical Debt that is going to make future work slower</span></li>
 	<li>Removing the option for the Product Owner to release the product if they so choose.</li>
 	<li><span style="display: inline !important; float: none; background-color: transparent; color: #333333; cursor: text; font-family: -apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,Oxygen-Sans,Ubuntu,Cantarell,'Helvetica Neue',sans-serif; font-size: 16px; font-style: normal; font-variant: normal; font-weight: 400; letter-spacing: normal; orphans: 2; text-align: left; text-decoration: none; text-indent: 0px; text-transform: none; -webkit-text-stroke-width: 0px; white-space: normal; word-spacing: 0px;">With undone work, you have to fix it next Sprint and thus interfere with the next SPrint Goal and the Product Owners delivery expectations.</span></li>
 	<li>Remove any chance of <a href="https://nkdagility.com/release-planning-and-predictable-delivery/">predictability for future sprints</a> until the undone work is under control.</li>
</ul>
</li>
</ul>
<strong>But if its DONE.</strong> There is no rejection of the Backlog Item there is only feedback. There is just a learning opportunity that can be used to reduce the expectations gap for future Sprints. Reflect on that during the Sprint Review, engage with Stakeholders to better understand both their intent and their expectations.

Empirical process control is not about doing everything correctly, it's about transparency, inspecting, and adapting.
<h2>The fallacy of the rejected backlog item</h2>
Oh, the Product Owner can deny the assertion of the Development Team that they have completed it and had them re-estimate it and stick it back on the backlog. They can decide to postpone deployment until the next Sprint. They can even choose to reject the entire Sprint and lose all of the work done in that Sprint. My point is that it is neither physically nor technically possible to remove a single PBI from a Sprint without incurring significant rework.
<blockquote>A Sprint Review is held at the end of the Sprint to inspect the Increment and adapt the Product Backlog if needed. During the Sprint Review, the Scrum Team and stakeholders collaborate about what was done in the Sprint. Based on that and any changes to the Product Backlog during the Sprint, attendees collaborate on the next things that could be done to optimize value.
-<a href="http://www.scrumguides.org/scrum-guide.html#events-review" rel="noopener">Scrum Guide - Sprint Review</a></blockquote>
<strong>The <a href="https://www.scrum.org/Scrum-Guides" rel="noopener">Scrum Guide 2017</a> mentions nothing of rejecting anything at the Sprint Review. </strong>

This is the reality of product development that gets in the way of the idea of the rejected backlog item. The software that we are producing is complex. If we are creating a Sprint Goal and selecting backlog items that help us achieve that Sprint Goal then they are probably inter-related. These inter-related items will likely build on and reference each other’s functionality. If we then decide to rip one of the nodes out of this complex web of classes and methods, then we are increasing risk, and we are also unlikely to have working software at the end of the Sprint. Oh, I am sure that there are exceptions, but it will take time to remove no matter how good the team's engineering practices.

Just to be clear, this is not about Done. I expect every team to produce work that meets whatever definition of done that they have agreed with the Product Owner. If the Development Team calls Done when they are not then that is a wholly separate problem… because <a href="https://nkdagility.com/professional-scrum-teams-build-software-works/">Professional Scrum Teams build software that works</a>.
<h2>Rejecting a Backlog Item is missing the point</h2>
Not only that but you may be missing the whole point of the Sprint Review. It is not about acceptance or rejection of the increment by the Product Owner, but instead, it is about discovery and understanding between the Product Owner, the Development Team, and Stakeholders. It is one of the keys inspect and adapts points for the Product Backlog. The Product Owner, being human, perhaps had a picture of what they wanted in their head that does not match what the Development team has produced. In this case, the Development Team need to work with the Product Owner to update the backlog with the changes that now need to make it that which the Product Owner envisaged. So it meets “done”, it <a href="https://nkdagility.com/you-are-doing-it-wrong-if-you-are-not-using-test-first/">meets the acceptance criteria</a>, and it is still not what the Product Owner wanted. Is this the Development Teams fault? Of course not… it is a learning point, and inspect and adaption of understanding between the Product Owner and the Development Team. The Product Owner learned how the Development Team interprets their words and the Development Team learned something about the Product Owners intent. This is intensely valuable learning for the Scrum Team as a whole.

There are only three actions open to the Product Owner at the Sprint Review:
<ol>
 	<li>Update the Product Backlog to reflect what we now need to do to achieve the vision</li>
 	<li>Choose to ship the current increment or not</li>
 	<li>Choose to end the project or continue</li>
</ol>
<h2>Making it easier with feature flags or toggles</h2>
All of that being said it is the job of the Development Team to make things as flexible for the Product Owner as possible. They should implement what capabilities that they need into each increment to make it possible for them to turn a new feature off and still ship. This will not only make the Product Owner happy; it will get the newly built features in front of the Stakeholders as quickly as possible for feedback.

There are a few things that can make this as easy as possible:
<ul>
 	<li><strong>Communication</strong> – Good communication between the Product Owner and the Development Team can help alleviate these sorts of issues. However, continued interfering in the Development Team by the Product Owner will make it harder to deliver what was estimated. The Development Team should deliver their understanding of what the Product Owner presented to them at the Sprint Planning meeting while collaborating where timely and appropriate.</li>
 	<li><strong>INVEST</strong>– Making sure that your PBI’s are all following the INVEST [Independent | Negotiable | Valuable | Estimable | Sized appropriately | Testable] model. If you follow this guide, then you can minimise any misunderstanding between the Product Owner and the Development Team.</li>
 	<li><strong>Feature Flippers/toggles/flags</strong> – The single most valuable thing in your developer's arsenal is the ability to turn the things that you are adding on and off at will. This should be applied both to a feature and the multiple layers of that feature that are added to each pass delivering PBI’s. You may think of each PBI’s as requiring a switch to be able to turn it on or off. It is usually not perfect as there are some things that are iterations of the same feature. More advanced implementations may allow you to enable or disable features by account or user.</li>
</ul>
If you can do all of these things as they will all add value by making it easier to give the Product Owner flexibility.
<h2>Who is naked Agility Limited - Martin Hinshelwood</h2>
<a href="https://nkdagility.com/company/about-martin-hinshelwood/">Martin Hinshelwood</a> believes that every company deserves high-quality software delivered on a regular cadence that meets its customer's needs. His goal is to help you reduce your cycle time, improve your time to market, and minimise any organisational friction in achieving your goals. Martin is the <a href="https://nkdagility.com">Founder/CEO of naked Agility Limited</a> and is both a <a href="https://www.scrum.org/martin-hinshelwood" rel="noopener">Professional Scrum Trainer</a> and a <a href="https://mvp.microsoft.com/en-us/PublicProfile/4021815?fullName=Martin%20John%20Hinshelwood" rel="noopener">Microsoft MVP: Visual Studio and Development Technologies</a>. He has been delivering software since 2000 and has been Consulting, Coaching, and Training in DevOps &amp; Agility with Visual Studio, Azure, Team Services, and Scrum since 2010. You can reach Martin on <a href="mailto:hello@nkdagility.com?subject=Scrum.org%20Blog%20Post%20Enquiry">hello@nkdagility.com</a>.