---
ID: 9469
post_title: >
  You are doing it wrong if you are not
  using test first
post_name: >
  you-are-doing-it-wrong-if-you-are-not-using-test-first
author: >
  Martin Hinshelwood (He/Him)
  nkdAgility.com
post_date: 2020-12-07 12:00:58
post_excerpt: '<p class="lead">Many teams are struggling with delivering modern software because they are not building with Test First principals. Test First gives us the assurance that we have built the correct thing, that what we built is what the customer asked for and that when we change things we don’t break anything inadvertently.</p>'
layout: post
link: >
  https://nkdagility.com/blog/you-are-doing-it-wrong-if-you-are-not-using-test-first/
published: true
tags:
  - ATDD
  - BDD
  - Develop
  - Developers
  - Operational
  - Practices
  - TDD
  - Test First
categories:
  - 'People &amp; Process'
  - 'Tools &amp; Techniques'
---
<p class="lead">Many teams are struggling with delivering modern software because they are not building with Test First Principals. Test First gives us the assurance that we have built the correct thing, that what we built is what the customer asked for and that when we change things we don’t break anything inadvertently.</p>

<h2>TL;DR;</h2>
While it takes time, effort, dedication and discipline to achieve Test First the return on investment is enormous. A common form of Test First is Test Driven Development (TDD) and we can use it to meet more of our customer's expectations, minimise our maintenance costs, and get fewer regressions and bugs in production. Ultimately without working in a test first culture, you will be <a href="https://nkdagility.com/continuous-deliver-sprint/">unable to do continuous delivery</a> with any confidence.

The only question for a <a href="https://nkdagility.com/training/courses/professional-scrum-developer-training/">Professional Development Team</a> is how to get started.
<h2>You are doing it wrong if you are not using test first</h2>
If you look up Test First on Wikipedia you will be redirected to the Test Driven Development (TDD) page and I believe this to be incorrect. While TDD is one, arguably the most effective, form of Test First it is by no means the whole thing. Can I achieve Test First with no automation at all: Yes. Can I do TDD with no automation at all: No. Do you see my conflict…
<blockquote><strong><em>If you are building applications without writing your tests first then you are doing it wrong. Your process will result in significant rework, be less maintainable and be less likely to meet the customers needs.</em></strong><small><strong>Scottish Software Proverb</strong> (just made it up, and I am Scottish)</small></blockquote>
Unfortunately, while the proverb above is absolutely true there are many fanatics that will not accept that you can do test-first without automation. Just like the <strong>Process Wars</strong>, the <strong>Practice Wars</strong> are being waged around us, and while we want to endeavour to be agnostic it is not possible to be an atheist.

You will hear a lot of different terms banded about in relations to test first:
<ul>
 	<li><strong>Test-Driven Development (TDD)</strong> – Automated tests created before the code is written to validate that we need that code.</li>
 	<li><strong>Acceptance Test Driven Development (ATDD)</strong> – Tests, either automated or manual, that validate business functionality</li>
 	<li><strong>Behaviour Driven Development (BDD)</strong> – An automated test that validates a particular behaviour that you want your application to have.</li>
 	<li>etc…</li>
</ul>
<blockquote>All of these topics, and more, are covered in the <a href="https://nkdagility.com/training/courses/professional-scrum-developer-training/">Professional Scrum Developer (PSD) training</a> that was build in combination with Scrum.org and Microsoft as the only official team training for Scrum &amp; DevOps.</blockquote>
These terms all fulfil a specific niche and the evolution of modern software development will sprout many more. Find that which solves your specific problem and adapt until you have something that works for you, your team and your organisation.
<h2>The essence of test first</h2>
Test First has two main goals, both of which are as important as each other.

The first is about professionally validating that which you have built. Software Development is complicated and one can easily create unintended results when that code is executed. This is not a quotient of poor programming but of the complexity of the task. In the eighteen hundreds, plumbers pumped smoke through the pipes to make sure that there were no leaks on the grounds that if it is good enough for the smoke it is good enough for water. This mentality has resulted in what we now call the ‘smoke test’ in software development and the result of its implementation is bugs in production. When compared to software development plumbing is simple; modern software is many times more complex than Software was even 10 years ago. We have accepted poor quality deliverables and expensive maintenance for far too long.

The second goal is to shorten your feedback loops. The closer our engineers are to when the problem was created the quicker they can find it and the cheaper it is to fix. Unfortunately, it is impossible to tell in most software what ‘right’ looks like and developers just take a guess. The attitude that a problem, if it exists, will be caught by Quality Assurance (QA) or User Acceptance Testing (UAT) is unprofessional at best and incompetence at worst. We want to <strong>know</strong> that what we have just written not only meets our customer's expectations but also does exactly what we intended for it to do under as many circumstances as we can think of.
<blockquote><strong><em>Test First allows us to mature from simply testing quality in towards building that quality in from the start</em></strong><small><strong>Jeff Levinson</strong>, Architect at Boeing</small></blockquote>
Fundamentally it is far cheaper to fix an issue closest to its source. The longer we leave the finding of that defect the more expensive it becomes. A bug found in production is <a href="http://www.scrum.org/About/All-Articles/articleType/ArticleView/articleId/644/Agile-Economics-The-Dollars-and-Sense-of-Scrum" target="_blank" rel="noopener noreferrer">10 times more costly</a> to fix than the same bug found in development.

The three virtues of Test First:
<ol>
 	<li>Validation of building what was asked for</li>
 	<li>Validation that what we have built works as we intended</li>
 	<li>Validation that changes have not broken original intent</li>
</ol>
Ideally, we want our tests to be as close to the code as possible, but also as easily understood by the customer as possible. Ideally, all of our code is automated and we have an executable specification. It's a balancing act…
<h3>Business Validation – We have built what was asked for</h3>
Getting validation that we are building the right thing is key to actually being able to build the right thing. This sounds like a no-brainer but what do we usually do?

Well, we usually take our requirements, in whatever form we generally make them, and give them to our coders to turn into working software. Quite separately we give the same requirements to our testers and they create a bunch of tests to validate what we have built.

Did you notice the problem with this workflow?
<blockquote><strong><em>The worst that can happen is that we built exactly what the customer asked for!</em></strong></blockquote>
How can we ever build to meet the measure if we don’t build to what is to be measured? We need to flip that on its head and instead have the tests created first (the measure) and then Code to make the tests pass. Now that we have removed the inevitable time-consuming rework we can take that time and use it to create even more value for our customers.

In addition, we are far more likely to be able to meet our customers expectations now we have an additional level of focus provided by those tests.
<h3>Developer Validation – What we have built works as we intended</h3>
Its now 2017 and gone are the cowboy days of the late nineties and <a href="http://en.wikipedia.org/wiki/Naughties" target="_blank" rel="noopener noreferrer">early naughties</a>. Along with <a href="https://nkdagility.com/getting-started-with-modern-source-control-system-and-devops/">using modern source control</a>, software engineers can no longer hide behind their management as "not giving the approval to do Unit Testing", or changing what "unit testing" means to allow them to bypass the requirement. This is <a href="https://nkdagility.com/scrum-tapas-importance-professionalism/">about professionalism</a> and all developers, no matter what they are working on, should be validating the work that they do.
<blockquote><strong><em>You are not a professional if you do not do the due diligence necessary to validate what you have created works as intended and continuous to do so.
-<a href="https://nkdagility.com/professional-scrum-teams-build-software-works/">Professional Scrum teams build software that works</a>
</em></strong></blockquote>
There are two main value-adds here. The first is that when a coder creates functionality it does exactly what he intended and we have a record, and executable specification, of what that intent was. The second comes later. When we go to add functionality later we know when we have broken existing functionality and that is one of the most valuable parts of this endeavour.

<strong>Can you imagine how amazing it would be if you could use this executable specification to validate all future changes don’t break your application?</strong>

&nbsp;
<h3>Resources</h3>
These resources should help you start down a journey to building better applications:
<ul>
 	<li><a title="Agile Economics- The Dollars and Sense of Scrum" href="http://www.scrum.org/About/All-Articles/articleType/ArticleView/articleId/644/Agile-Economics-The-Dollars-and-Sense-of-Scrum" target="_blank" rel="noopener noreferrer">Agile Economics- The Dollars and Sense of Scrum</a> (Scrum.org)</li>
 	<li><a href="http://www.scrum.org/About/All-Articles/articleType/ArticleView/articleId/642/Adopting-Test-First-Development" target="_blank" rel="noopener noreferrer">Adopting Test-First Development</a> (Scrum.org)</li>
 	<li><a href="http://pluralsight.com/training/courses/TableOfContents?courseName=outside-in-tdd&amp;highlight=mark-seemann_outside-in-tdd-m2-spiking*2!mark-seemann_outside-in-tdd-m1-walking-skeleton*7#outside-in-tdd-m2-spiking" target="_blank" rel="noopener noreferrer">Outside-In Test-Driven Development</a> (Pluralsight $)</li>
 	<li><a href="http://pluralsight.com/training/courses/TableOfContents?courseName=test-first-development-1&amp;highlight=david-starr_tfd-01-m01-introduction*10,12,13!scott-allen_tfd-writing-unit-tests-i*5,7!david-starr_tfd-01-m06-isolation*11,2#tfd-01-m01-introduction" target="_blank" rel="noopener noreferrer">Test First Development - Part 1</a>(Pluralsight $)</li>
</ul>
<h2>Who is naked Agility Limited - Martin Hinshelwood</h2>
<a href="https://nkdagility.com/company/about-martin-hinshelwood/">Martin Hinshelwood</a> is the <a href="https://nkdagility.com/" target="_blank" rel="noopener noreferrer" data-cke-saved-href="https://nkdagility.com/">Founder/CEO of naked Agility Limited</a> and has been their Principal Consultant and Trainer on DevOps &amp; Agility for four years. Martin is a <a href="https://www.scrum.org/martin-hinshelwood" target="_blank" rel="noopener noreferrer" data-cke-saved-href="https://www.scrum.org/martin-hinshelwood">Professional Scrum Trainer</a>, <a href="https://mvp.microsoft.com/en-us/PublicProfile/4021815?fullName=Martin%20John%20Hinshelwood" target="_blank" rel="noopener noreferrer" data-cke-saved-href="https://mvp.microsoft.com/en-us/PublicProfile/4021815?fullName=Martin%20John%20Hinshelwood">Microsoft MVP: Visual Studio and Development Technologies</a>, and has been Consulting, Coaching, and Training in DevOps &amp; Agility with Visual Studio, Azure, Team Services, and Scrum since 2010 and has been delivering software since 2000.
Martin is available for <a href="https://nkdagility.com/consulting/" target="_blank" rel="noopener noreferrer" data-cke-saved-href="https://nkdagility.com/consulting/">private consulting and training worldwide</a> and has many <a href="https://nkdagility.com/training/" data-cke-saved-href="https://nkdagility.com/training/">public classes across the globe</a>.