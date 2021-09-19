---
ID: 10579
post_title: >
  Maven release prepare fails with
  detected changes in Jenkins
post_name: >
  maven-release-prepare-fails-with-detected-changes-in-jenkins
author: >
  Martin Hinshelwood (He/Him)
  nkdAgility.com
post_date: 2014-07-09 14:03:50
post_excerpt: '<p>If you are using Team Explorer Everywhere 2012 or 2013 your Maven release prepare fails with detected changes, however it worked when you were using SVN.</p>'
layout: post
link: >
  https://nkdagility.com/blog/maven-release-prepare-fails-with-detected-changes-in-jenkins/
published: true
tags:
  - Jenkins
  - Maven
  - tfignore
categories:
  - 'Problems &amp; Puzzles'
  - 'Upgrade &amp; Maintenance'
---
<p>If you are using Team Explorer Everywhere 2012 or 2013 your Maven release prepare fails with detected changes, however it worked when you were using SVN.</p>
<p>As you may have noticed I have had a few posts on Jenkins integration with TFS recently. My current customer is migrating away from SVN and Jenkins to TFS 2012 to take advantage of the cool ALM feature however we need to stage in, taking one thing at a time. They have quite a few builds in Jenkins and moving them will take time. The idea is that we can move all of the source over and it is a fairly simple process to re-point Jenkins and Maven to TFS. This allows the teams to take advantage of relating their Source and Work Item while allowing us to create parallel builds and validate the output.</p>
<p> <a href="http://nakedalmweb.wpengine.com/wp-content/uploads/2014/06/image2.png"><img style="border-width: 0px; padding-top: 0px; padding-right: 0px; padding-left: 0px; display: inline; background-image: none;" title="image[2]" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2014/06/image2_thumb.png" alt="image[2]" width="800" height="640" border="0" /></a></p>
<p>Our initial problem was around <a href="http://nakedalmweb.wpengine.com/configuring-jenkins-talk-tfs-2013/">Configuring Jenkins to talk to TFS 2013</a> and then <a href="http://nakedalmweb.wpengine.com/mask-password-in-jenkins-when-calling-tee/">Mask password in Jenkins when calling TEE</a>. As with all migration projects you get past one problem and get hit by another. The next issue was that the Release builds would always fail. Looking at the logs it is obvious why.</p>
<pre>[INFO] Command line - /bin/sh -c cd /appl/data/ci-test/jenkins/jobs/TFS-TestProject/workspace &amp;&amp; tf status -login:username,********** -recursive -format:detailed '$/main/VisualStudioALM/JavaTestProject'
[DEBUG] line -
[DEBUG] line --------------------------------------------------------------------------------
[DEBUG] line -Detected Changes:
[DEBUG] line --------------------------------------------------------------------------------
[DEBUG] line -$/main/VisualStudioALM/JavaTestProject/release.properties
[DEBUG] line -  User:       Martin Hinshelwood (MrHinsh)
[DEBUG] line -  Date:       22-May-2014 14:33:52
[DEBUG] line -  Lock:       none
[DEBUG] line -  Change:     add
[DEBUG] line -  Workspace:  Hudson-TFS-TestProject-MASTER
[DEBUG] line -  Local item: [zsts490716.eu.company.com] /appl/data/ci-test/jenkins/jobs/TFS-TestProject/workspace/release.properties
[DEBUG] line -
[DEBUG] line -0 change(s), 1 detected change(s)
[INFO] err - 
[DEBUG] Iterating
[DEBUG] /appl/data/ci-test/jenkins/jobs/TFS-TestProject/workspace/release.properties:added
</pre>
<p>Here the release build is checking for changes after a get to validate the output and it finds a "release.properties" file sitting there. Now in the days of Server workspaces where you had to explicitly check out from the server you would not even see an issue. The file would not even be detected let alone pended to the server unless you ran a specific command. In the wonderful world of Local workspaces where changes to local workspaces are detected automatically this is an issue.</p>
<p>We need some way to tell TFS that we want it to ignore these release.properties files. Well, the TFS team thought of this and have added .tfignore files that operate just like the .gitignore one that you might be used to. However adding a .whatever files does not seem to be very easy in Widnows.</p>
<p> <a href="http://nakedalmweb.wpengine.com/wp-content/uploads/2014/06/image5.png"><img style="border-width: 0px; margin: 0px; padding-top: 0px; padding-right: 0px; padding-left: 0px; display: inline; background-image: none;" title="image[5]" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2014/06/image5_thumb.png" alt="image[5]" width="800" height="640" border="0" /></a></p>
<p>My first attempts to add the file resulted in a "you must type a file name" error and no matter what I did I could not get that .tfignore file created. I headed to the internet and eventually found that while you are blocked in Explorer you can open notepad and save a file of the required name. That’s a little poopy but needs must. I guess only power users really need to create files that begin with a dot and this protects the rest of them.</p>
<p> <a href="http://nakedalmweb.wpengine.com/wp-content/uploads/2014/06/image8.png"><img style="border-width: 0px; margin: 0px; padding-top: 0px; padding-right: 0px; padding-left: 0px; display: inline; background-image: none;" title="image[8]" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2014/06/image8_thumb.png" alt="image[8]" width="800" height="640" border="0" /></a></p>
<p>So we create and add a .tfignore file with a line that matches the pattern we want to ignore. Just listing the explicit file name will result in all instances, recursively, being ignored.</p>
<pre>######################################
# Ignore all release files from Maven release process
release.properties</pre>
<p>You can get quite complicated with this file but here I have very simple needs. To get the file into TFS the easyest way is to go to the folder where you want it in your local workspace and add it to the file system. We then need to right click in the empty space of the folder and select "Add Files to folder" which will pop the "Add to Source Control" dialog above with any files listed that it can't see already. If you have the Power Tools installed you can also just right-click the file and add it to source control right from Windows explorer.</p>
<p> <a href="http://nakedalmweb.wpengine.com/wp-content/uploads/2014/06/image11.png"><img style="border-width: 0px; margin: 0px; padding-top: 0px; padding-right: 0px; padding-left: 0px; display: inline; background-image: none;" title="image[11]" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2014/06/image11_thumb.png" alt="image[11]" width="800" height="640" border="0" /></a></p>
<p>There may be other files that you need to ignore and I ended up with:</p>
<pre>######################################
# Ignore all release files from Maven release process
release.properties
*.releaseBackup
target/
</pre>
<p>All we need to do now is execute a new build and see that light turn green. This is however a "dry run" build and we still have some work to do to get the rest of the process working, however this is progress. At least I don’t have generated files ruining my day.</p>