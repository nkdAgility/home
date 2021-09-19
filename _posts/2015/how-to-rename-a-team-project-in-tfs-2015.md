---
ID: 11317
post_title: How to rename a Team Project in TFS 2015
post_name: how-to-rename-a-team-project-in-tfs-2015
author: >
  Martin Hinshelwood (He/Him)
  nkdAgility.com
post_date: 2015-04-30 09:39:56
post_excerpt: "<p>TAG:Ever since TFS 2005 shipped we have been asking ourselves why, oh, why, can't we rename a Team Project. As each version of the product shipped we hoped beyond hope that this would change and we would get rid of those ugly code names, or that old corporate identity that no longer exists. </p>"
layout: post
link: >
  https://nkdagility.com/blog/how-to-rename-a-team-project-in-tfs-2015/
published: true
tags:
  - Team Project
  - TFS
  - TFS 2015
categories:
  - 'Install &amp; Configure'
---
<p>By the launch of TFS 2010 we had given up on getting rename in TFS. 5 years of no rename had taken its toll. Now, as a surprise present with TFS 2015 (and on VSO) and I have a bunch of projects to "zz". Did you know that you should always "zz" something before you delete it. If you delete something then its gone. If you prefix it with "zz" then it falls to the bottom of any list and you can ignore it until later… but if someone complains… you can easily recover it.</p>
<p>[pl_button type="info" link="https://www.visualstudio.com/en-us/downloads/visual-studio-2015-downloads-vs.aspx" target="blank"]Download 2015 today[/pl_button]</p>
<p>Renaming your Team Project is easy. You will need to be a Team Project Administrator, and there are some caveats and advanced instructions, but …</p>
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; margin: 0px; display: inline; padding-right: 0px; border: 0px;" title="clip_image001" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2015/04/clip_image0011.png" alt="clip_image001" width="773" height="450" border="0" /></p>
<p>You need to first access the admin page for your Team Project first. Make sure that you are currently selected on the Default Team in your team project. You are on the default team if it just says the "Team Project" name at the top of your browser rather than "Team Project \ Team" if you are on a non-default team.</p>
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; margin: 0px; display: inline; padding-right: 0px; border: 0px;" title="clip_image002" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2015/04/clip_image0021.png" alt="clip_image002" width="718" height="450" border="0" /></p>
<p>Once in the admin you can see the name below the profile picture, and up until now that was not editable. Now however you can change the team project name by simply selecting the team project name and changing the text.</p>
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; margin: 0px; display: inline; padding-right: 0px; border: 0px;" title="clip_image003" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2015/04/clip_image0031.png" alt="clip_image003" width="718" height="450" border="0" /></p>
<p>Once you start editing it you will have a "save" and "undo" button. Click "save" to start the Process to change the team project name.</p>
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; margin: 0px; display: inline; padding-right: 0px; border: 0px;" title="clip_image004" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2015/04/clip_image0041.png" alt="clip_image004" width="718" height="450" border="0" /></p>
<p>You will be warned that there is an impact to this. Remember that the name is used in a lot of the URL's and not all clients will support this gracefully. By the time TFS 2015 RTM's Visual Studio 2010 will be out of mainstream support and there will be no requirement for the product team to make sure that Visual Studio 2010 supports renaming a team project. To get the best compatibility and easiest transition you should make sure that all the clients are updated to Visual Studio 2013 Update 5 or Visual Studio 2015. However Visual Studio 2012 and other versions will be supported, it just might not be without a little tinkering… like clearing the cache or reconfiguring your TFS connection.</p>
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; margin: 0px; display: inline; padding-right: 0px; border: 0px;" title="clip_image005" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2015/04/clip_image0051.png" alt="clip_image005" width="773" height="450" border="0" /></p>
<p>If you have a busy TFS server then it may have to wait a while for the task to complete, but in the 5 renames I have done so far all of them took less than 10 seconds to complete. I have only currently renamed the team projects that are no longer needed and not yet hit an in-use project, but that is the plan for later in the week.</p>
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; margin: 0px; display: inline; padding-right: 0px; border: 0px;" title="clip_image006" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2015/04/clip_image0061.png" alt="clip_image006" width="718" height="450" border="0" /></p>
<p>Once you click "close" the page will refresh and the new team project name will be presented. At this point the old name will still work. If you hit it you will get the right page an all of the links from there will be the new name. This 'redirect' will be there until he old name is reused. So from the web access there should be minimal impact.</p>
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border: 0px;" title="clip_image007" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2015/04/clip_image0071.png" alt="clip_image007" width="718" height="450" border="0" /></p>
<p>You can see the four renames I have done so far and the additional three proposed for the end of the week. We will be picking a lightly used one first so that we can gauge the impact, and then roll on with the rest.</p>
