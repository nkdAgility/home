---
ID: 10019
post_title: 'What&#8217;s new in Visual Studio 2013 and TFS 2013 RC'
post_name: >
  whats-new-in-visual-studio-2013-rc-with-team-foundation-server
author: >
  Martin Hinshelwood (He/Him)
  nkdAgility.com
post_date: 2013-09-09 10:00:12
post_excerpt: '<p class="lead">As you may have noticed the Visual Studio team has just put out a Release Candidate to the log awaited Visual Studio 2013 and Team Foundation Server 2013.</p>'
layout: post
link: >
  https://nkdagility.com/blog/whats-new-in-visual-studio-2013-rc-with-team-foundation-server/
published: true
tags:
  - TFS
  - TFS 2013
  - Whats New
categories:
  - 'Products &amp; books'
  - 'Tools &amp; Techniques'
---
<p class="lead">As you may have noticed the Visual Studio team has just put out a Release Candidate to the log awaited Visual Studio 2013 and TFS 2013.</p>
<p>If you have been&nbsp;<a href="http://nakedalmweb.wpengine.com/unable-to-install-visual-studio-2013-rc-on-windows-8-1-preview/">unable to install Visual Studio 2013 RC on Windows 8.1 Preview</a> then you want to immediately get to grips with the new features. I would recommend that you have a look at <a href="http://nakedalmweb.wpengine.com/get-visual-studio-2013-team-foundation-server-while-its-hot/">What's new in Visual Studio 2013 Team Foundation Server Preview</a> for two reasons. I am going to assume that you have seen the aforementioned features and it should give you some idea of the pace of features improvement you get by being on the same cadence as the TFS product team.</p>
<p>These are just my initial observations from conducting a little exploratory testing on features that we saw in the TFS 2013 Preview and those things that I knew and suspected were coming down the line. The best way to get a heads up is still to create an account on <a href="http://tfs.visualstudio.com">http://tfs.visualstudio.com</a> as it is already ahead of the Release Candidate.</p>
<h2>Visual Studio 2013 Team Explorer Enhancements</h2>
<p>There have been repeated and increasing enhancements to the Team Explorer. Some of these enhancements have been small experiments and others have been large. Some have been successful and some result is continuous change as the product team evolve things trying to meet our needs. If only every team building software would innovate as often. If like me you take the latest drop at all times you will see the bounding progression of features and enhancements. If you don’t you will see the usual big leaps.</p>
<h3>Visual Studio 2013 Team Explorer remembers your TFS Servers</h3>
<p>I was surprised when I opened the connection dialog on my brand new OS with Visual Studio 2013 RC installed and saw a list of TFS servers that I recognised.</p>
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="image" alt="image" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2013/08/image16.png" width="720" height="450" border="0" /><br /><small>Figure: Visual Studio 2013 Team Explorer remembers your TFS Servers</small></p>
<p>It looks like the team has populated my list of servers with all of the instances from <a href="http://tfs.visualstudio.com">http://tfs.visualstudio.com</a> that I have permission for, and that's a lot. I am not sure what happens when this list gets bigger than my screen but that's for another day. I had forgotten that I had connected to some of these servers. What would be a nice enhancement to this would be to have local servers that are synched as well. That way I can easily select local servers when I go onsite at customers.</p>
<h3>New Team Explorer Home page</h3>
<p>The new layout for the Team Explorer homepage is much more flexible and has way better extension points.</p>
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; margin: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="image" alt="image" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2013/08/image17.png" width="720" height="450" border="0" /><br /><small>Figure: The new Team Explorer in 2013</small></p>
<p>Again we have the context of a single Team Project. While administrators may have preferred the old tree view users found it confusing and slow. The new interface added with 2012 has been streamlined and enhanced with a years worth of usability data.</p>
<h3>The Project Section</h3>
<p>The project session is topped with a set of useful links:</p>
<ul>
<li><strong>Configure Workspace</strong> – This takes you to the the configuration page for the Workspaces that you have associated with your Team Project.</li>
<li><strong>Web Portal</strong> – The Web Portal is THE way to access and work with much of the data in TFS 2013. Even more than in 2010 and in 2012 as we now have Test management right there in the web. In addition to Test Case management there are hubs for Agile Planning, Agile Portfolio Management, Work Item Tracking, Build Management, Code Management and now Reporting.</li>
<li><strong>Task Board</strong> – Part of the Agile Planning Tools feature that was introduced in TFS 2012 the Task Board provides you a Scrum style board where Requirement types sit on the left and tasks flow through states associated with the Requirement from left to right. Typical states are To-do –> Doing –> Done.</li>
<li><strong>Team Room</strong> – Each Team gets their own persistent chat and notification room where users can interact and be notified of Builds and work item changes dynamically. Way better than email.</li>
</ul>
<p>Although Web Access is now the preferred way to access much of the data in TFS that does not mean that there are no other options. The following sections have been incrementally updated individually but here each of the important nodes use a flow layout so that they are just as accessible regardless of the size of the window. They are each subtly colour coded but the new piece is that many of them have a little ellipse in the bottom right of the button \ panel. If you click the ellipse you you get a drop down of menu options for that feature. Indeed these panels dynamically change depending on which source control you selected when you created your Team Project. TFS 2013 supports both TFVC and Git.</p>
<ul>
<li><strong>My Work</strong> – The My Work section gives you access to the up level features like Code Reviews, Suspend Resume and Task switching and focus features that you need to be on Premium or ultimate SKU’s to get. Few of these features yet work of your pick Git as your source control.</li>
<li><strong>Pending Changes </strong>– A new view on the standard pending changes with a docked panel instead of a floating model dialog. You can now break it out of the UI and stick it anywhere you want.</li>
<li><strong>Source Control Explorer</strong> – Only available for TFVC projects this gives you folder and branch access to your code. I have yet to delve into that UI</li>
<li><strong>Work Items </strong>– Gives you access to the standard tree of queries. You can create flat, dependant or tree queries that show whatever columns that you like. There are some Team Explorer only features like opening queries in Excel or MS Project and turning Queries into reports.</li>
<li><strong>Build</strong> – Want continuous delivery? This is your stop. Create both compilation, test and deployment builds that execute on demand, timed or triggered. A special feature added way back in 2010 allows you to pre-moderate your builds which lets you build first and reject check-ins for failed builds.</li>
<li><strong>Reports</strong> – Your gateway to the Reporting Services reports that are available for your Process Template</li>
<li><strong>Settings</strong> – The new settings page now seams like a Launchpad for the Web Portal. I will not miss those model dialog boxes….more power to the web…</li>
</ul>
<p>These same features, well mostly, are available in Eclipse as well.</p>
<h3>The Solution Section</h3>
<p>The solution section, new in 2013, is awesome. It looks at the scope of your currently selected Workspace and lists all of the Solutions available in Source Control to open. Here I have nothing in source yet and I don’t have my workspace configured. I do believe that there is a limit to the number of solutions that will be listed, but I am not sure what that it.</p>
<h2>Visual Studio 2013 Team Foundation Server Enhances</h2>
<p>While the new features in Visual Studio are awesome I sometimes forget what they look like these days. Apart from the projects that I work on myself with the other MVP’s, the Rangers and just for fun I rarely get to play in Visual Studio. (sniff)I do miss it, they even (shock) have me coding in c# these days, but I never stop complaining about that.</p>
<p>So where do I play, well… sometimes in PowerShell but mostly in Team Foundation Server when I am doing technical stuff. Helping teams and organisations improve their processes is mostly not about tools. However when I need a tool I always turn to TFS. As the TFS Product Team are moving more and more towards agile themselves the product itself is getting better and better at delivering value in the agile space. Although there are many features that are based on reportability that is no longer the focus of the team and the new features concentrate on making your development process as slick as possible.</p>
<h3>Team Rooms</h3>
<p>Team Rooms are brand new in TFS 2013 and provide a kina cross between email notifications and persistent chat.</p>
<p>You can configure notification for various things including Build results and work item changes. The results pop into the window with a little ‘ding’ for other to be notified. If you are unable to get everyone in a physical team room then this is the next best thing. Those of you out there thinking ‘what's the use of that crap’ should give it a try. Find it valuable or don’t as you like but the ability to chat and tag work items just by mentioning #2354 or a person with the usual @Youname mechanism makes the experience much more interactive.</p>
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border: 0px;" title="image" alt="image" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2013/08/image18.png" width="633" height="500" border="0" /><br />Figure: Configure events for Team Rooms in 2013</p>
<p>I am looking forward to innovations and experiments here.</p>
<h3>Agile Portfolio Management Enhancements</h3>
<p>When I looked at <a href="http://nakedalmweb.wpengine.com/get-visual-studio-2013-team-foundation-server-while-its-hot/">What's new in Visual Studio 2013 Team Foundation Server Preview</a> I spent a lot of time on the Agile Portfolio Management features and even created a <a href="http://nakedalmweb.wpengine.com/video-new-with-visual-studio-2013-manage-portfolio-backlogs-to-understand-the-scope-of-work/" target="_blank">video walkthrough</a>. Here I just want to go back and visit some of the areas that&nbsp; have been improved.</p>
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="image" alt="image" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2013/08/image19.png" width="720" height="450" border="0" /><br /><small>Figure: Backlog View Pick list</small></p>
<p>First up is that pick list list that lets you ‘look up’ and ‘look down’. In the earlier version it was not colour coded, it did not have the current level first and the text was just the name of the Work Item in question. The new list is eminently more usable and understandable. Here we get more context; we get the colour of the work item type that we can subconsciously relate. There is also a subtle separator between the ‘current view’ and the alternative views. It was previously easy to forget which level you were at and thus where one had to go to get back to the orderable view. We had the ‘Backlog Items’ highlight on the left, but we had to look way the other side of the screen to figure it out. Now we can easily see where we are and where we are looking. Even the addition of the simple “to [other work item type]” test gives us much more of that context.</p>
<p>This to me is an embodiment of a small simple but extremely valuable enhancement to an existing feature that is only really valuable in short release cycles. In a long cycle it would never make it above the cut line.</p>
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; margin: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="image" alt="image" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2013/08/image20.png" width="720" height="450" border="0" /><br /><small>Figure: Subtle directional chevron on Backlogs</small></p>
<p>If you do select another option, in this case I am looking up from ‘Backlog items to Features’ you get a subtle indication on the left as well as to where you are. The little colour coded chevron for "’Backlog items’ narrows at the top to signify that we are looking up. This gives other side of the screen the same information in a subtle enough manor as to not interrupt or clutter the display, but still conveying necessary information.</p>
<h3>Mapping from Backlog Items to Features</h3>
<p>Another incremental improvement is the ability to easily associate backlog Items with Feature (or whatever you have above the backlog that you are viewing).</p>
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; margin: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="image" alt="image" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2013/08/image21.png" width="720" height="450" border="0" /><br /><small>Figure: Mapping from Backlog to Parent</small></p>
<p>Here we can turn on Mapping and a list of the parent items are listed on the right. You can then drag and drop your backlog items onto the required feature to create the associations that you want. This makes it way easier and more intuitive to work with the hierarchy.</p>
<h3>Charting from Queries</h3>
<p>One of the awesome features in TFS in the reporting, even if it is just incidental reporting when you are not actively trying to get traceability. In Visual Studio you can right click on a Query and select “Generate Report”. This feature would look at the fields that were available on the query and determine what sort of reporting was possible with those options. It would then let you build out both static and trend reporting in Excel using a macro. Well, as we move towards more of a cloud based infrastructure we need the same features but unfortunately, or fortunately, there is no Analysis Services in Azure. So what can we do?</p>
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="image" alt="image" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2013/08/image22.png" width="720" height="450" border="0" /><br /><small>Figure: Static Analysis reports in TFS 2013</small></p>
<p>The product team in superb incremental style have implemented the easy part first; Static Charting. They have created the ability to add charts to you query. To find the options head over to your work item queries and when you select a query you will note an extra tab added to the UI. Where we had only Results and Edit we now get Charts. Once on the charts tab you can create a new chart and select the chart type:</p>
<ul>
<li>Pie</li>
<li>Bar</li>
<li>Column</li>
<li>Stacked bar</li>
<li>Pivot table</li>
</ul>
<p>While this will never have parity with Excel there is much more value in this being just available in the UI. One you have selected your chart type you get to give it a name and then customise the data displayed. You need to first select the Grouping. This is the field (dimension) that you want to display the data by. After that you select the values (metric) to display.&nbsp; I don’t hold out hopes for getting trend analysis by RTM of 2013 but if we are lucky some future sprint will bring that functionality.</p>
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; margin: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="image" alt="image" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2013/08/image23.png" width="720" height="450" border="0" /><br /><small>Figure: Adding lots of charts</small></p>
<p>You can go ahead and add a bunch of charts giving you different views of the same data and creating a dashboard based on your query data. I love this option…</p>
<h3>Multi-reorder of Column Options</h3>
<p>As I was clicking through I notices a little nugget that I have no idea when it was added.</p>
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; margin: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="image" alt="image" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2013/08/image24.png" width="720" height="450" border="0" /><br />Figure:</p>
<p>Maybe this was added in 2012 and I never noticed but you can, when ordering columns, select multiple columns and change their order together. I don;t know how many times I have moved each one individually and I hope this is a new feature if only to save face…</p>
<h3>Creating Test Plans from the Web Portal</h3>
<p>Although web based Testing was added in one of the updates to 2012 there were some serious limitations. We could not create Test Plans and needed to jump into MTM to perform many of those tasks.</p>
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; margin: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="image" alt="image" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2013/08/image25.png" width="720" height="450" border="0" /><br /><small>Figure: Creating Test Plans from the Web Portal</small></p>
<p>Now with 2013 you can create a Test Plan directly in the web UI. You can add a name and configure the Area Path and Iteration Path that is relevant. If you want to edit the Test Plan you have to jump into MTM but the team have added a little bottom on the far right off the highlight above to jump strait to that page in the application.</p>
<h3>Create Test Cases in a Grid view</h3>
<p>Power users of Microsoft Test Manager have always called for productivity improvements. They were always used to working in Excel before MTM came along and some things are just easier there. Well the MTM team has been listening and they have added some new features to the web to make things easier.</p>
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; margin: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="image" alt="image" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2013/08/image26.png" width="720" height="450" border="0" /><br /><small>Figure: Create test Cases in Grid View</small></p>
<p>You can now create Test Cases just like you once did in Excel. You can modify and add new at the same time and save as you go along. If you use to, or currently, create Test Cases in Excel and then port them to MTM you can now copy and paste them into here and save.</p>
<h3>Open the Test Plan or Run Test in Microsoft Test Manager Client from Web</h3>
<p>The last feature I want to highlight is the “Run using client” bottom that sends the selected tests to MTM for execution.</p>
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; margin: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="image" alt="image" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2013/08/image27.png" width="720" height="450" border="0" /><br />Figure: Launching MTM from the Web UI</p>
<p>In MTM you get data collectors like Video, Intellitrace, Event Log scraping, Code Coverage and Test Impact Analysis. Sometimes you want those things and this lets you jump into the right part of MTM and back to the web access making the integration a little bit more seamless.</p>
<h2>Conclusion</h2>
<p>Although I knew where some of them were, or where I expected them to exist these were just the few highlights of features that I feel that are important based on my customer engagements. There are a plethora of features in Visual Studio like Code Sense (kind of a heads up display for coding) that go to ALM productivity but I have not yet used them.</p>
<p>Remember that <a href="http://nakedalmweb.wpengine.com/team-foundation-server-2013-is-production-ready/" target="_blank">Team Foundation Server 2013 is production ready</a>.</p>
<p>If you have the Preview you should upgrade and anyone on 2010or 2012 should seriously consider the features available. Remember also that you can still use VS 2010 and VS 2012 with TFS 2013.</p>
<p><small>Originally posted on <a hre3f="http://blogs.msdn.com/b/mvpawardprogram">The Microsoft Award Program Blog</a> as Visual Studio 2013 RC Released (<a href="http://blogs.msdn.com/b/mvpawardprogram/archive/2013/09/09/visual-studio-2013-rc-released.aspx" target="_blank">source</a>)</small></p>
