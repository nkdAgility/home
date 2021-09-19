---
ID: 10811
post_title: 'NDC London: Second Look, Team Foundation Server &amp; VSO'
post_name: >
  ndc-london-second-look-team-foundation-server-vso
author: >
  Martin Hinshelwood (He/Him)
  nkdAgility.com
post_date: 2014-10-15 15:49:05
layout: post
link: >
  https://nkdagility.com/blog/ndc-london-second-look-team-foundation-server-vso/
published: true
tags:
  - Backlog Management
  - Code Sense
  - CodedUI
  - Feedback Client
  - My Work
  - Portfolio Management
  - Release Management
  - StoryBoarding
  - TFS 2013.3
  - VSTeamServices
categories:
  - 'Events &amp; Presentations'
---
<p>While I have spoken at many events in the USA while I lived there, and even did a few keynotes for the Visual Studio 2012 launch, I have been trying to figure out the scene here in Europe. As such I submitted to a few events and got accepted to speak at NDC London.</p>
<p><a href="http://www.ndcvideos.com/#/app/video/2641"><img class="alignnone wp-image-10977 size-medium" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2014/10/martin-hinshelwood-ndc-london-2014-tfs-vso-800x450.png" alt="martin-hinshelwood-ndc-london-2014-tfs-vso" width="800" height="450" /></a></p>
<p>My session, Second Look, Team Foundation Server &amp; VSO, will be aimed at those folks that have previously tried TFS and found it lacking. Most of those folks previously used a version of TFS prior to TFS 2012 where things started to get really interesting. Indeed if you are building an application using the Microsoft stack there is no better ALM platform.</p>
<p><img title="1030_image_thumb_0AF311DD" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2014/10/1030-image-thumb-0AF311DD.png" alt="1030_image_thumb_0AF311DD" width="392" height="450" border="0" /></p>
<p>The main reason that IBM scores a little higher on completeness is that they have better support for other platforms but at a loss of features for any specific one. While Visual Studio ALM has good support for any platform, the support for the Microsoft stack is second to none.</p>
<p>With the time constraint and the amount of things I want to show my session will need to be demo heavy. The type of person that I am gearing this session towards are the hard core who tried TFS prior to 2012 and don’t believe the marketing. Do demos it is… but I just looked back at what I submitted:</p>
<blockquote>
<p>You may have looked at Team Foundation Server before and if it was before 2012 then you should have another look. It is not the same product it used to be. Come and see Martin do an end to end walk through from Ideation through Coding, Testing and Release with monitoring and feedback. Martin will cover some of the new advances with Storyboarding, Agile Project Management, and Agile Portfolio Management. He will then delve into the new ALM features added since 2010 for coders like My Work, Code Sense, and Local Workspaces and even Git. With the new Test Management tools in the web complimented with Microsoft Test Manager your testers can easily manage, execute and report on your test plans. All the while we will be using the new Release Management tools to push our application to each environment and ultimately to production. Once there we can monitor our application for usage and performance with rich statistics.</p>
<p>All in all TFS is a world premier ALM solution that provides everything that you need to manage the Application Lifecycle of your application.</p>
</blockquote>
<p>Oh my… look what I signed myself up to!</p>
<p>Wana see this session? Sign up for a ticket at: <a href="http://ndc-london.com">http://ndc-london.com</a></p>
<p>So it's going to have to be 45+ minutes Demo, and I have two options. I can do everything in my local demo box, and that will be the backup scenario, or I can go Azure crazy. Between now and NDC London I will be blogging on setting up and configuring continuous everything with VSO and Azure. What do I mean by continuous everything?</p>
<p><a href="http://nakedalmweb.wpengine.com/wp-content/uploads/2014/10/clip-image0025.png"><img title="clip_image002" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2014/10/clip-image002-thumb.png" alt="clip_image002" width="800" height="451" border="0" /></a></p>
<p>Well, I want the full lifecycle with Azure Active Directory integration driving authentication and collaboration with Azure, Visual Studio Online, and Office 365. This would be a huge demo if I stopped to explain all the features along the way, so I am not going to. The audience at NDC is very smart and this is going to be a level 400 high-speed walkthrough of the core features added to TFS since 2012.</p>
<p>There will however need to be trade-offs so I am looking for your help to see what features to spend the most time on and what to just mention in passing. Are you going to NDC?</p>
<p><a href="https://www.surveymonkey.com/r/C2FCM79">Feedback Request - What Features do you most want to see?</a></p>
<p>I am not yet sure if I will be using green field or brownfield as each have their pros and cons. In my flying time deliberations I have been contemplating three main scenarios:</p>
<ol>
<li>Greenfield<br />Start with an empty team project and build everything up from scratch. That would mean getting the code in, creating a backlog, writing some code, followed by some testing and then an automated build. I would then get a few minutes while the build executes to create a release management pipeline and push to the environments.</li>
<li>Greenfield TFS / brownfield project<br />Again, start with an empty team project but import from somewhere else. Maybe pull in a Github project and do the same as above.</li>
<li>Brownfield<br />Have an existing end to end setup and just walk through adding a feature or fixing a bug and the interactions involved.</li>
</ol>
<p>I guess it depends how long my session is with brownfield being the easiest to pull off. A plan then would be to get brownfield working and then, if there is time, look into the other options. So let's see what the scenarios are that I plan on tackling:</p>
<h3>Brownfield Scenario 1 - The new Feature</h3>
<p>In this scenario we have a new feature and we are going to implement a single PBI to do with this feature. We need to have a Storyboard to go with the PBI for coder context and Test Cases prior to commencing the work. We then make two passes, the first with build and deploy of the new code. The second with automation of the now passing test case.</p>
<ol>
<li>Create new Feature in TFS</li>
<li>Create Storyboard to show feature</li>
<li>Create PBI's to reflect feature</li>
<li>Create Test Cases for one PBI</li>
<li>Code till test cases pass using TDD</li>
<li>Push to Repo</li>
<li>Build &amp; Test with Team Build</li>
<li>Deploy with Release Manager to Feedback01</li>
<li>Coder Validation</li>
<li>Deploy with Release Manager to Feedback02</li>
<li>Tester Validation &amp; Recording</li>
<li>Coder Automates Test Case</li>
<li>Deploy with Release Manager to Feedback01</li>
<li>Coder Validation of Automation</li>
<li>Deploy with Release Manager to Feedback02</li>
<li>Tester review of Results</li>
<li>Deploy with Release Manager to Feedback03</li>
<li>Product Owner Validation</li>
<li>Review of Application Analytics usage data</li>
</ol>
<h3>Brownfield Scenario 2 - The Bug</h3>
<p>In this scenario we have a user who, is the process of providing feedback, finds an issue. The Product Owner gets this bug verified by a Tester and a relevant test case created to prove that it exists. This is then prioritized and enters the current sprint, maybe with something dropping out the bottom. The coder then fixes it and the tester verifies it before automating the result to prevent regression.</p>
<ol>
<li>User Gets feedback request and actions</li>
<li>User Finds and reports bug as part of feedback</li>
<li>Product Owner breaks feedback down into PBI's</li>
<li>Product Owner reviews feature usage stats and notifies tester of possible important bug</li>
<li>Tester validates existence of bug and creates rich bug and Test Case</li>
<li>Bug prioritized and added to current sprint</li>
<li>Code till test cases pass using TDD</li>
<li>Push to Repo</li>
<li>Build &amp; Test with Team Build</li>
<li>Deploy with Release Manager to Feedback01</li>
<li>Coder Validation</li>
<li>Deploy with Release Manager to Feedback02</li>
<li>Tester Validation &amp; Recording</li>
<li>Coder Automates Test Case</li>
<li>Deploy with Release Manager to Feedback01</li>
<li>Coder Validation of Automation</li>
<li>Deploy with Release Manager to Feedback02</li>
<li>Tester review of Results</li>
<li>Deploy with Release Manager to Feedback03</li>
<li>Product Owner Validation and emails User</li>
</ol>
<h3>Scenario Choice</h3>
<p>As well as understanding what features you, as the audience on the day, want to hit I also want to know which scenario is more interesting.</p>
<p><a href="https://www.surveymonkey.com/r/CCN7ZR9">Feedback Request - Which scenario looks most desirable?</a></p>
<h2>Conclusion</h2>
<p>I am really looking forward to this session as it will give me a chance to directly target nay-sayers that are not really aware of the capabilities of the product. If you are building for .NET then there is no better platform.</p>
<p>Please provide me with some feedback on the polls above. I am very interested in focusing on what will solve the most problems for attendees. I will also be around for the full 3 days and would be happy to do add-hock demos and problem solving sessions… Unless there is a supper interesting session on the go I would be happy to provide free TFS consulting for any and all attendees of NDC London on the days.</p>
<p>If you are on a tight schedule I would be happy to have you pre-book some time. Email info@nakedalm.com to get some free TFS &amp; VSO consulting at NDC London.</p>