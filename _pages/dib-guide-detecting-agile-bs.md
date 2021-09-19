---
ID: 45395
post_title: 'DIB Guide: Detecting Agile BS'
post_name: dib-guide-detecting-agile-bs
author: >
  Martin Hinshelwood (He/Him)
  nkdAgility.com
post_date: 2020-12-09 12:43:55
layout: page
link: >
  https://nkdagility.com/dib-guide-detecting-agile-bs/
published: true
tags: [ ]
categories: [ ]
---
[yoast-breadcrumbs]<p>Agile is a buzzword of software development, and so all DoD software development projects are, almost by default, now declared to be “agile.”</p>
<p>The purpose of this document is to provide guidance to DoD program executives and acquisition professionals on how to detect software projects that are really using agile development versus those that are simply waterfall or spiral development in agile clothing (“agile-scrum-fall”).</p>		
			<a href="/company/free-consultation/" role="button">
						Schedule a free 30 minute call
					</a>
		[wpv-post-body view_template="nkdagility-getintouch"]		
			<h4>Table of Contents</h4>					
		<!-- wp:paragraph --><!-- /wp:paragraph --><!-- wp:heading -->
<h2 id="h-principles-values-and-tools">Principles, Values, and Tools</h2>
<!-- /wp:heading --><!-- wp:paragraph -->
<p>Experts and devotees profess certain key “values” to characterize the culture and approach of<br />agile development. In its work, the DIB has developed its own guiding maxims that roughly map<br />to these true agile values:</p>
<!-- /wp:paragraph --><!-- wp:table -->
<figure>
<table>
<tbody>
<tr>
<td><strong>Agile value</strong></td>
<td><strong>DIB maxim</strong></td>
</tr>
<tr>
<td>Individuals and interactions over processes and<br />tools</td>
<td>“Competence trumps process”</td>
</tr>
<tr>
<td>Working software over comprehensive<br />documentation</td>
<td>“Minimize time from program launch to deployment<br />of simplest useful functionality”</td>
</tr>
<tr>
<td>Customer collaboration over contract negotiation</td>
<td>“Adopt a DevSecOps culture for software systems”</td>
</tr>
<tr>
<td>Responding to change over following a plan</td>
<td>“Software programs should start small, be iterative,<br />and build on success ‒ or be terminated quickly”</td>
</tr>
</tbody>
</table>
</figure>
<!-- /wp:table --><!-- wp:paragraph -->
<p>Key flags that a project is not really agile:</p>
<!-- /wp:paragraph --><!-- wp:list -->
<ul>
<li>Nobody on the software development team is talking with and observing the users of the software in action; we mean the actual users of the actual code.1 (The Program Executive Office (PEO) does not count as an actual user, nor does the commanding officer, unless she uses the code.)</li>
<li>Continuous feedback from users to the development team (bug reports, users assessments) is not available. Talking once at the beginning of a program to verify requirements doesn’t count!</li>
<li>Meeting requirements is treated as more important than getting something useful into the field as quickly as possible.</li>
<li>Stakeholders (development, test, ops, security, contracting, contractors, end-users, etc.)2 are acting more-or-less autonomously (e.g. ‘it’s not my job.’)</li>
<li>End users of the software are missing-in-action throughout development; at a minimum, they should be present during Release Planning and User Acceptance Testing.</li>
<li>DevSecOps culture is lacking if manual processes are tolerated when such processes can and should be automated (e.g. automated testing, continuous integration, continuous delivery).</li>
</ul>
<!-- /wp:list --><!-- wp:paragraph -->
<p>Some current, common tools in use by teams using agile development (these will change as<br />better tools become available):</p>
<!-- /wp:paragraph --><!-- wp:list -->
<ul>
<li><strong>Git, ClearCase, or Subversion </strong>- version control system for tracking changes to source code. Git is the de-facto open-source standard for modern software development.</li>
<li><strong>Azure Repos, BitBucket, GitHub</strong> - repository hosting sites. Also provide issues tracking, continuous integration “apps” and other productivity tools. Widely used by the open-source community.</li>
<li><strong>Azure Pipelines, Jenkins, Circle CI, Travis CI </strong>- continuous integration service used to build and test BitBucket and GitHub software projects</li>
<li><strong>Chef, Ansible, or Puppet</strong> - software for writing system configuration "recipes" and streamlining the task of configuring and maintaining a collection of servers</li>
<li><strong>Docker </strong>- a computer program that performs operating-system-level virtualization, also known as "containerization"</li>
<li><strong>Kubernetes or Docker Swarm</strong> - for container orchestration</li>
<li><strong>Azure Boards, GitHub, Jira, Pivotal Tracker</strong> - issues reporting, tracking, and management</li>
</ul>
<!-- /wp:list --><!-- wp:paragraph -->
<p>Graphical version:</p>
<!-- /wp:paragraph --><!-- wp:image {"id":45396,"sizeSlug":"large"} -->
<figure><img src="https://nkdagility.com/wp-content/uploads/2020/12/image-1.png" alt="" /></figure>
<!-- /wp:image --><!-- wp:heading -->
<h2 id="h-questions-to-ask-programming-teams">Questions to Ask</h2>
<p>For a team working on agile, the answer to all of these questions should be “yes.”</p>
<h3 id="h-questions-to-ask-programming-teams">Questions to Ask Programming Teams</h3>
<!-- /wp:heading --><!-- wp:list -->
<ul>
<li>How do you test your code? (Wrong answers: “we have a testing organization”, “OT&amp;E is responsible for testing”)
<ul>
<li>Advanced version: what tool suite are you using for unit tests, regression testing, functional tests, security scans, and deployment certification?</li>
</ul>
</li>
<li>How automated are your development, testing, security, and deployment pipelines?
<ul>
<li>Advanced version: what tool suite are you using for continuous integration (CI), continuous deployment (CD), regression testing, program documentation; is your infrastructure defined by code?</li>
</ul>
</li>
<li>Who are your users and how are you interacting with them?
<ul>
<li>Advanced version: what mechanisms are you using to get direct feedback from your users? What tool suite are you using for issue reporting and tracking? How do you allocate issues to programming teams? How to you inform users that their issues are being addressed and/or have been resolved?</li>
</ul>
</li>
<li>What is your (current and future) cycle time for releases to your users?
<ul>
<li>Advanced version: what software platforms to you support? Are you using containers? What configuration management tools do you use?</li>
</ul>
</li>
</ul>
<!-- /wp:list --><!-- wp:heading -->
<h3 id="h-questions-for-program-management">Questions for Program Management</h3>
<!-- /wp:heading --><!-- wp:list -->
<ul>
<li>How many programmers are part of the organizations that own the budget and milestones for the program? (Wrong answers: “we don’t know,” “zero,” “it depends on how you define a programmer”)</li>
<li>What are your management metrics for development and operations; how are they used to inform priorities, detect problems; how often are they accessed and used by leadership?</li>
<li>What have you learned in your past three sprint cycles and what did you do about it? (Wrong answers: “what’s a sprint cycle?,” “we are waiting to get approval from management”)</li>
<li>Who are the users that you deliver value to each sprint cycle? Can we talk to them? (Wrong answers: “we don’t directly deploy our code to users”)</li>
</ul>
<!-- /wp:list --><!-- wp:heading -->
<h3 id="h-questions-for-customers-and-users">Questions for Customers and Users</h3>
<!-- /wp:heading --><!-- wp:list -->
<ul>
<li>How do you communicate with the developers? Did they observe your relevant teams working and ask questions that indicated a deep understanding of your needs? When is the last time they sat with you and talked about features you would like to see implemented?</li>
<li>How do you send in suggestions for new features or report issues or bugs in the code? What type of feedback do you get to your requests/reports? Are you ever asked to try prototypes of new software features and observed using them?</li>
<li>What is the time it takes for a requested feature to show up in the application?</li>
</ul>
<!-- /wp:list --><!-- wp:heading -->
<h3 id="h-questions-for-program-leadership">Questions for Program Leadership</h3>
<!-- /wp:heading --><!-- wp:list -->
<ul>
<li>Are teams delivering working software to at least some subset of real users every iteration (including the first) and gathering feedback? (alt: every two weeks)</li>
<li>Is there a product charter that lays out the mission and strategic goals? Do all members of the team understand both, and are they able to see how their work contributes to both?</li>
<li>Is feedback from users turned into concrete work items for sprint teams on timelines shorter than one month?</li>
<li>Are teams empowered to change the requirements based on user feedback?</li>
<li>Are teams empowered to change their process based on what they learn?</li>
<li>Is the full ecosystem of your project agile? (Agile programming teams followed by linear, bureaucratic deployment is a failure.)</li>
</ul>
<!-- /wp:list --><!-- wp:paragraph --><!-- /wp:paragraph --><!-- wp:image {"id":45397,"sizeSlug":"large"} -->
<figure><img src="https://nkdagility.com/wp-content/uploads/2020/12/image-2.png" alt="" /></figure>
<h2>References</h2>
<!-- /wp:image --><!-- wp:paragraph -->
<p>More information on some of the features of DoD software programs are included in Appendix A<br />(<a href="https://media.defense.gov/2018/Apr/22/2001906836/-1/-1/0/DEFENSEINNOVATIONBOARD_TEN_COMMANDMENTS_OF_SOFTWARE_2018.04.20.PDF">DIB Ten Commandments on Software</a>), Appendix B (<a href="https://media.defense.gov/2018/Jul/10/2001940937/-1/-1/0/DIB_METRICS_FOR_SOFTWARE_DEVELOPMENT_V0.9_2018.07.10.PDF">DIB Metrics for Software Development</a>),<br />and Appendix C (DIB Do’s and Don’ts of Software [to be linked]).</p>
<!-- /wp:paragraph --><!-- wp:paragraph -->
<p> </p>
<!-- /wp:paragraph --><!-- wp:paragraph -->
<p> </p>
<!-- /wp:paragraph --><!-- wp:paragraph -->
<p> </p>
<!-- /wp:paragraph --><!-- wp:paragraph -->
<p> </p>
<!-- /wp:paragraph --><!-- wp:paragraph -->
<p> </p>
<!-- /wp:paragraph --><!-- wp:paragraph -->
<p> </p>
<!-- /wp:paragraph --><!-- wp:paragraph -->
<p> </p>
<!-- /wp:paragraph --><!-- wp:paragraph -->
<p> </p>
<!-- /wp:paragraph --><!-- wp:paragraph -->
<p> </p>
<!-- /wp:paragraph --><!-- wp:paragraph -->
<p> </p>
<!-- /wp:paragraph --><!-- wp:paragraph -->
<p> </p>
<!-- /wp:paragraph --><!-- wp:paragraph -->
<p> </p>
<!-- /wp:paragraph --><!-- wp:paragraph -->
<p> </p>
<!-- /wp:paragraph --><!-- wp:paragraph -->
<p> </p>
<!-- /wp:paragraph --><!-- wp:paragraph -->
<p> </p>
<!-- /wp:paragraph --><!-- wp:paragraph -->
<p> </p>
<!-- /wp:paragraph --><!-- wp:paragraph -->
<p> </p>
<!-- /wp:paragraph --><!-- wp:paragraph -->
<p> </p>
<!-- /wp:paragraph --><!-- wp:paragraph -->
<p> </p>
<!-- /wp:paragraph --><!-- wp:paragraph -->
<p> </p>
<!-- /wp:paragraph --><!-- wp:paragraph -->
<p> </p>
<!-- /wp:paragraph --><!-- wp:paragraph -->
<p> </p>
<!-- /wp:paragraph --><!-- wp:paragraph -->
<p> </p>
<!-- /wp:paragraph --><!-- wp:paragraph -->
<p> </p>
<!-- /wp:paragraph --><!-- wp:paragraph -->
<p> </p>
<!-- /wp:paragraph --><!-- wp:paragraph -->
<p> </p>
<!-- /wp:paragraph --><!-- wp:paragraph -->
<p> </p>
<!-- /wp:paragraph --><!-- wp:paragraph -->
<p> </p>
<!-- /wp:paragraph --><!-- wp:paragraph -->
<p> </p>
<!-- /wp:paragraph --><p>Adapted from <a href="https://media.defense.gov/2018/Oct/09/2002049591/-1/-1/0/DIB_DETECTING_AGILE_BS_2018.10.05.PDF">DIB_DETECTING_AGILE_BS_2018.10.05.PDF (defense.gov)</a></p>