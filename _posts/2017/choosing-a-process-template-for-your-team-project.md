---
ID: 10356
post_title: >
  Choosing a Process Template for your
  Team Project
post_name: >
  choosing-a-process-template-for-your-team-project
author: >
  Martin Hinshelwood (He/Him)
  nkdAgility.com
post_date: 2017-05-16 11:40:46
post_excerpt: '<p class="lead">There was an interesting discussion on <a href="http://www.linkedin.com/groups/Team-Foundation-Server-TFS-2012-3386360.S.5828175548890763266?view=&amp;gid=3386360&amp;type=member&amp;item=5828175548890763266" target="_blank">Agile vs Scrum Template for TFS 2012</a> on LinkedIn that I was interested in however LinkedIn has a bug and will not let me comment on that open group. So I will add my answer here.</p>'
layout: post
link: >
  https://nkdagility.com/blog/choosing-a-process-template-for-your-team-project/
published: true
tags:
  - Microsoft Visual Studio Scrum
  - MSF
  - MSF for Agile Software Development
  - MSF for CMMI Process Improvement
  - Process Template
  - TFS
  - TFS 2012
  - TFS 2013
categories:
  - DevOps
  - 'Tools &amp; Techniques'
---
<p class="lead">Over the years I have had many discussions about Agile vs Scrum process templates with both TFS and VSTS and migrated many Team Projects from Agile or CMMI templates to the Scrum Template.</p>
<p><strong><i>TL;DR - Select the Scrum template if you have an agile team and want to reduce friction. Don't create unnecessary friction for your move to agility by selecting either the CMMI or Agile templates that suffer from the legacy of the Microsoft Solution Framework (MSF).</i></strong></p>
<p>When you create a new Team Project in VSTS or TFS you are asked which Process Template that you want to use. This is a decision that you need to make at the time you create your Team Project and you cant change it later. You want to choose the template that is closest to what you are actually doing, or more accurately what you want to be doing.</p>
<p><img class="alignright size-medium" src="http://nkdagility.com/wp-content/uploads/2014/01/image1.png" width="300" height="293" />Many teams and organisations make very good and seemingly rational arguments for choosing either the Agile or CMMI templates, however I feel that if you are trying to achieve any type of agile implementation for your team then this is the wrong choice. There are two key frictions that I think affect your choice:</p>
<ul>
	<li><b>Current Friction -</b> If you have a discrepancy between what you are doing now, and the process template you choose then you will have a harder time getting folks to work within the bounded environment that you are trying to create. However you may want some friction if folks are currently doing the wrong thing.</li>
	<li><b>Future Friction</b> - As your process implementation moves to match your strategic direction, and the template lags behind , then you will have a significant friction for folks who really want to do the old thing.</li>
</ul>
<p>Having the right rules to follow is valuable for figuring out the right path:</p>
<ul>
	<li>Create a Template for the Process that you want, not the process that you have.</li>
	<li>Make it easy to do the right thing, and hard to do the wrong thing.</li>
</ul>
<p>Making the wrong choice can cripple your teams ability to inspect and adapt by making their biggest problem trying to avoid the friction that your choice in template has created. While I also believe that anyÂ  team following any process could, with significant discipline, use any template,Â  if your team is an agile one then both the Agile and CMMI templates will create significant friction. Let me explain; there are three templates available out of the box:</p>
<ul>
	<li><b>CMMI</b> - This was called "MSF for CMMI Process Improvement" and was primarily focused on those teams that need to monitor change and are following CMMI.</li>
	<li><b>Agile</b> - Formally known as "MSF for Agile Software Development" and is designed to support Agile development for teams that don't want to be restricted by Scrum</li>
	<li><b>Scrum</b> - Also know as "Microsoft Visual Studio Scrum" was designed to allow Scrum teams a more familiar with Scrum.</li>
</ul>
<p>However every single one of these templates supports both "agile" and "CMMI", however only one embodies agility and minimises prescription and constraints, and its not the "Agile" template.</p>
<h2>Why you should not select the Agile template</h2>
<p>I have had a number of...<del> arguments</del> discussions with the folks that own "MSDN: Work with team project artefacts, choose a process template" about its inaccuracies and false choices and some changes have been made. However I have issue with one particular statement in there:</p>
<blockquote>
<p>The Agile template is designed to support Agile development for teams that don't want to be restricted by Scrum.</p>
</blockquote>
<p>Lets forget for a moment about Scrum and look singly at the contents and expected use of the templates. I completely disagree that the "Agile" template is suitable for agile teams and I vehemently disagree that the Scrum template is restrictive. I believe that the opposite is true.</p>
<p>I believe that the "Agile" template (as well as the "CMMI" template) is in fact not agile and enshrines many common anti-patterns for agile teams. Its not really a surprise as the "Agile" template was not designed by agilest for agile teams. The "Agile" template is properly called the "MSF for Agile Software Development" template and the MSF part is important.</p>
<p>Microsoft Solution Framework (MSF) was designed by Microsoft Consulting Services (MCS) to help them deliver software to customers when consulting. The MSF for Agile template was originally an attempt to implement that non-agile methodology (don't let the word Framework fool you) in a more agile manor and it failed (oh it gave managers a false sense of agile; vanity agile. Lets call things agile and do the same old thing we have always done.)</p>
<p>There are main issues with the Agile template:</p>
<ul>
	<li><b>Bugs are not on the backlog</b> - As any good consulting team (sarcasm) knows you must hide your bugs from the customer and this template promotes that bugs are triaged separately to Stories. Yes you can change this to add bugs to the backlog, however the expected happy path is that you triage your bugs separately. From TFS 2015+ we can choose how bugs are handled on the UI.</li>
	<li><b>Resolved (Code Complete and Unit Tests passes) </b>- Yes I know that many teams still like to create a wall between Code and Test but to enshrine it in the template forces all teams to follow that line. Making this the path of least friction encourages users to do the wrong thing. You really cant be agile and throw bugs or features over the wall to Test.</li>
</ul>
<p>In addition to the main issues there are a great number of paper cuts as well. While individually small they add up to significant friction:</p>
<ul>
	<li><b>Story Points</b> - Why are people encouraged to only use Story Point? Are they the right practice for everyone, on every software? No, Story Points are just a complimentary practice that can be applied to any process. While I am a supporter of Story Points and I encourage teams that I work with to use them they are by no means the only method of estimating in agile. This should have a more generic name, like maybe Effort that allows the team, or organisation, to collectively decide how they are going to do estimation.</li>
	<li><b>User Story</b> - Is the only way to write backlog items to do so as User Stories? What about Use Cases? Should you struggle to write even constraints or non-functional requirements as User Stories? No, again User Stories are merely another complimentary practice. While user stories are an effective tool to help you decompose your work they are by no means the be all and end all. Having the Requirement type called User Story makes folks feel that every one should have a "As a | I want | so that" which is just not the case in any of the agile processes. Would it not be better to have a more generic term, a base class if you will, from which you can form any sort of definition of our work?</li>
</ul>
<p>Forcing people into using these complimentary practices is silly and creates that friction. These practices are not required to be successful at agile however being able to break walls between departments and triage bugs with the rest of our backlog I would argue is. Don't get me wrong, I like practices like Story Points and User Stories and they are right for some teams, although not all.</p>
<p>If you really want to be able to "let the team decide" on the practices that suit their circumstance, experience, technology and choice then you need to stay away from MSF templates entirely.</p>
<p>So what is the answer? What if I am not doing Scrum, but there are only two other choices, both of them MSF based. Well I would recommend that you use the Scrum Template anyway, and create your own agile process with this as the foundation. For folks that really want to have the Agile template, because they hate the word Scrum and anything associated with it. I kind of lie. I download the Scrum Process Template from TFS and change the same to "Agile for Company X" then reload it.</p>
<h2>Why you should use the Scrum Template</h2>
<p>Rather like the Scrum Framework itself the Scrum template was designed to be as light as possible while still embodying the common lexicon of Agile. Wither you like Scrum or not, it is an implementation of Agile and uses the same terminology. The thing that differentiates Scrum from other agile implementations is the Sprint and the Sprint is not really part of the Scrum template. You can easily change the Iterations to be any flavour you like.</p>
<p>Bugs are on the backlog, one state for the team working on something, no push to a particular practice.Â  Almost universally the terminology and workflow of the Scrum framework is understood by teams doing any flavour of agile. And if you have a team that needs a little legacy love you can easily add a column to the Kanban boards without enshrining dysfunctions in the template.</p>
<p>I always recommend that folks start with the Visual Studio Scrum template as a base and customise from there. There are a few customising that I like to see teams make if they need them, especially to help adoption:</p>
<ul>
	<li><b>Completed &amp; Original Estimate</b> - The Scrum template only has Remaining Work on a Task as this is the only metric that Scrum requires. However there are many teams that gain value through other metrics and the Scrum Guide does not say anything about not using them. I often add these two fields to the Scrum template for teams, and I never feel bad about it.</li>
	<li><b>Requirement Type Field</b> - Often organisations like to differentiate between Functional , Technical, or Regulatory PBI's and this is another field to add. Making sure of course that it becomes a dimension in the Cube. Luckily the out-of-the-box template from TFS 2015+ has this field already, just put the values that you need.</li>
	<li><b>Team Field Mode</b> - Often the case for long term users of TFS is that they already have made good use of the Area Path field. Now they need to use it for team? Well, no. Create a Team drop down and with a little out-of-box wiring you remove the relationship between Team and Area Path. This feature is currently unavailable in VSTS and the product team are looking to make it unnecessary.</li>
</ul>
<p>These customisations are non-intrusive and have a limited impact on reporting and upgradability. I spend a lot of time at customers migrating them from the Agile and CMMI templates to the Scrum template and while it is not that hard to do it does take time and money.</p>
<h2>Conclusion</h2>
<p>Choose the Microsoft Visual Studio Scrum process template if you don't want to be limited by MSF. What other customisations do you make to your Scrum template to support your lean-agile process?</p>