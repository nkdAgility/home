---
ID: 10899
post_title: 'Could not find mappings for all states defined in &#8216;Test Suit&#8217; work item type'
post_name: >
  find-mappings-states-defined-test-suit-work-item-type
author: >
  Martin Hinshelwood (He/Him)
  nkdAgility.com
post_date: 2014-11-11 15:46:00
post_excerpt: |
  <p class="lead">After upgrading to TFS 2013.3 you get some reports of errors in MTM from your users. Specifically they get a "Could not find mappings for all states defined in 'Test Suit' work item type" error when connecting. I have also seen "TF400860: TestManagement: Version 19, MinVersion: 19" in some cases in the web access.</p>
layout: post
link: >
  https://nkdagility.com/blog/find-mappings-states-defined-test-suit-work-item-type/
published: true
tags:
  - Microsoft Test Manager
  - Test Management
  - TF400860
  - TFS 2010
  - TFS 2012
  - TFS 2013
categories:
  - 'Problems &amp; Puzzles'
---
<p class="lead">After upgrading to TFS 2013.3 you get some reports of errors in MTM from your users. Specifically they get a "Could not find mappings for all states defined in 'Test Suit' work item type" error when connecting. I have also seen "TF400860: TestManagement: Version 19, MinVersion: 19" in some cases in the web access.</p>
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; margin: 0px; display: inline; padding-right: 0px; border: 0px;" title="clip_image001" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2014/11/clip-image001.jpg" alt="clip_image001" width="590" height="452" border="0" /></p>
<p>This should only happen if you have customised the Test Suit or Test Plan work items but as they have just been created by the upgrade process it is a little confusing as to why it does not work.</p>
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border: 0px;" title="clip_image002" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2014/11/clip-image0025.png" alt="clip_image002" width="786" height="452" border="0" /></p>
<p>You might additionally find a similar error when trying to edit a Lab Template as it also queries the Test Data.</p>
<p>In these cases, if you look real closely at the error message you will see that while "Completed" and "In Planning" look good there is an issue with "In progress". The test team in their infinite wisdom decided that if you have not customised anything that the system defaults to a hard coded set of process configuration for Tests. This sounds reasonable unless you factor in organisations that make silly customisations to their process template.</p>
<p>In case you have not figured it out yet, the "In process" state should be "In Process". Yes, that’s a case sensitivity issue. When you are uploading work item types this is case-insensitive and is rationalised across work items. So if you have one work item in there with "In process" set and then you add another work item with "In Process" TFS will fix it for you on import. However the test teams hard coded the process configuration which is case sensitive.</p>
<p>I am pretty sure that the product team will go fix it, but for now you two solutions:</p>
<h3>Solution 1: Fix the configuration of your process</h3>
<p>You should be mindful to make sure that you get all of your casing right. In this case I would check all of my work items to make sure that they have the same case and that it is the correct and out-of-the-box "In Process" text.</p>
<h3>Solution 2: Add a custom process configuration override</h3>
<p>In your process configuration you need to add a little bit of customisation to continue to use the case you have configured.</p>
<pre class="lang:xhtml decode:true">    &lt;TestSuiteWorkItems category="Microsoft.TaskCategory"&gt;
      &lt;States&gt;
        &lt;State type="Proposed" value="In planning" /&gt;
        &lt;State type="InProgress" value="In progress" /&gt;
        &lt;State type="Complete" value="Completed" /&gt;
      &lt;/States&gt;
    &lt;/TestSuiteWorkItems&gt;
</pre>
<p>&nbsp;&nbsp;Once added you should not have an issue.</p>
<h3>Conclusion</h3>
<p>These entries are only required when connecting from older clients. From Visual Studio 2013.3 onwards this is a non-issue so it might be your chance to get all of your users to update to the latest and greatest.</p>
<p>Remember that this issue only affects older clients, and when you have miss typed the casing of the states in your custom process template. Most folks should not run into this and it is a simple fix if you do.</p>