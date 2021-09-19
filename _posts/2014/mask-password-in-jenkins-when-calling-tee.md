---
ID: 10538
post_title: >
  Mask password in Jenkins when calling
  TEE
post_name: >
  mask-password-in-jenkins-when-calling-tee
author: >
  Martin Hinshelwood (He/Him)
  nkdAgility.com
post_date: 2014-05-21 14:49:04
post_excerpt: '<p>When you use the release build plugin in Jenkins to create a new release the plugin inadvertently leaves your password in clear text in the log files. We need to be able to mask passwords in Jenkins when calling Team Explorer Everywhere (TEE) so that we meet security requirements.</p>'
layout: post
link: >
  https://nkdagility.com/blog/mask-password-in-jenkins-when-calling-tee/
published: true
tags:
  - Jenkins
  - Maven
  - TFS
  - TFS 2012
  - TFS 2012.4
categories:
  - 'Tools &amp; Techniques'
---
<p>When you use the release build plugin in Jenkins to create a new release the plugin inadvertently leaves your password in clear text in the log files. We need to be able to mask password in Jenkins when calling Team Explorer Everywhere (TEE) so that we meet security requirements.</p>
<p>As you can imagine working at a bank, they get a little…squirmy… when they see or hear about passwords being stored on viewable in the clear. If you are using TFS to do builds from Jenkins then you are likely using the command line tools that come with Team Explorer Everywhere.</p>
<p><img style="margin: 0px; border: 0px currentColor; padding-top: 0px; padding-right: 0px; padding-left: 0px; display: inline; background-image: none;" title="clip_image001" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2014/05/clip_image001.png" alt="clip_image001" width="800" height="466" border="0" /></p>
<p>If you are also using the Release Plugin and you create a release build then you will see the SCM password that you enter written in the clear in the log. Bit of a shock to my banking colleagues I can tell you. So much so that they called "critical blocker" for the migration to TFVC.</p>
<p><img style="margin: 0px; border: 0px currentColor; padding-top: 0px; padding-right: 0px; padding-left: 0px; display: inline; background-image: none;" title="clip_image002" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2014/05/clip_image002.png" alt="clip_image002" width="800" height="446" border="0" /></p>
<p>However during the… conversation… they did say that they had a plugin installed that was supposed to <a href="https://wiki.jenkins-ci.org/display/JENKINS/Mask+Passwords+Plugin">mask the passwords</a> when you do a build. Armed with that knowledge, and little other knowledge of Jenkins, I dived in to find a solution. Maybe it just needed more configuration…</p>
<p><img style="margin: 0px; border: 0px currentColor; padding-top: 0px; padding-right: 0px; padding-left: 0px; display: inline; background-image: none;" title="clip_image003" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2014/05/clip_image003.png" alt="clip_image003" width="800" height="422" border="0" /></p>
<p>So I looked through the documentation and found that you can set variables for passwords and send the variable instead. The plugin will then mask it correctly…. So I thought… that’s for me!</p>
<p><img style="margin: 0px; border: 0px currentColor; padding-top: 0px; padding-right: 0px; padding-left: 0px; display: inline; background-image: none;" title="clip_image004" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2014/05/clip_image004.png" alt="clip_image004" width="800" height="470" border="0" /></p>
<p>So I dutifully created a global password veriable called "MrHinshPas" (yes, I am testing with my own account) and once saved I should be able to use "$(MrHinshPass)" in places where I want the password replaced.</p>
<p><img style="margin: 0px; border: 0px currentColor; padding-top: 0px; padding-right: 0px; padding-left: 0px; display: inline; background-image: none;" title="clip_image005" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2014/05/clip_image005.png" alt="clip_image005" width="800" height="640" border="0" /></p>
<p>Running another build and, wohoo, the password gets replaced.</p>
<p>However why do I need to create a variable for this occurrence when it usually replaced things for other passwords in the list. So I went hunting around… I looked at server configuration. I looked at plugins and documentation.</p>
<p>Eventually I looked in the build configuration and I found this…</p>
<p><img style="border: 0px currentColor; padding-top: 0px; padding-right: 0px; padding-left: 0px; display: inline; background-image: none;" title="clip_image006" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2014/05/clip_image006.png" alt="clip_image006" width="800" height="474" border="0" /></p>
<p>So for each specific job you can activate the "Mask passwords" option in the Build Environment section and all passwords are magically hidden in your builds. Awesome! How did I miss that…</p>
