---
ID: 11047
post_title: Create a Build vNext build definition
post_name: >
  create-a-build-vnext-build-definition-on-vso
author: >
  Martin Hinshelwood (He/Him)
  nkdAgility.com
post_date: 2015-03-04 17:37:00
post_excerpt: '<p class="lead">I am going to show how to create a Build.vNext build definition on VSO. Microsoft recently announced the creation of a brand new build system for TFS and VSO at the Connect event last year. This new build system will eventually replace the current one and be much more modular and friendly. Happily I am in the early adopter program and the product team just made an early alfa of the service available for that program and I have been giving it a spin.  </p>'
layout: post
link: >
  https://nkdagility.com/blog/create-a-build-vnext-build-definition-on-vso/
published: true
tags:
  - Android
  - Build
  - CMake
  - Jake
  - MSBuild
  - PowerShell
  - Preview
  - TF Build
  - TFS
  - TFS 2015
  - vNext
  - VS
  - VSTeamServices
  - VSTest
  - Xcode
categories:
  - 'Install &amp; Configure'
  - 'Tools &amp; Techniques'
---
<p class="lead">I am going to show how to create a Build vNext build definition on VSO. Microsoft recently announced the creation of a brand new build system for TFS and VSO at the Connect event last year. This new build system will eventually replace the current one and be much more modular and friendly. Happily I am in the early adopter program and the product team just made an early alfa of the service available for that program and I have been giving it a spin.</p>
<div class="bs-callout bs-callout-info">
<h4>Download Team Foundation Server 2015 today</h4>
<p>Microsoft has released a CTP of TFS 2015 that includes the vNext build system. You can <a href="https://www.visualstudio.com/en-us/downloads/visual-studio-2015-ctp-vs" target="_blank">download TFS 2015</a> and try it out today. Remember that this is <em>not</em> a go-live version and you should <em>not </em>install it in production.</p>
</div>
<p>Now that we have <a href="http://nakedalmweb.wpengine.com/configure-a-build-vnext-agent-on-vso/">configured a Build vNext agent</a> we can get on with the job of creating a build. I had hoped that for my <a href="http://nakedalmweb.wpengine.com/ndc-london-2014-why-tfs-no-longer-sucks-and-vso-is-awesome/">demo at NDC London last month</a> that I would have been able to use this but it took an extra month for the product team to get the Alfa ready. This is really just part of the realities of software development that we can't know how long something will take until its done.</p>
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="Create a vNext Build on VSO" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2015/01/clip_image001.png" alt="Create a vNext Build on VSO" width="762" height="418" border="0" /></p>
<p>There are a number of out-of-the-box templates available and I believe that there will be more by launch. For my FabirikamFiber site I will be using the standard "Visual Studio" definition.</p>
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="clip_image002" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2015/01/clip_image002.png" alt="clip_image002" width="762" height="418" border="0" /></p>
<p>You will get dropped out at Build tab of the "New Visual Studio definition 1" definition that has been created for you. Here you can add new tasks and configure them, which we will discuss in a moment.</p>
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="clip_image003" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2015/01/clip_image003.png" alt="clip_image003" width="762" height="418" border="0" /></p>
<p>This has not yet been saved, so the first thing I am going to do is save my detention with a little more memorable name.</p>
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="clip_image004" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2015/01/clip_image004.png" alt="clip_image004" width="661" height="418" border="0" /></p>
<p>Back at the "Task" list you can click "Add new task" to get a list of all of the available tasks. This is probably pretty close to the list of tasks that we will see initially when the preview becomes more generally available and it is extensive:</p>
<ul>
<li><b>Android Build</b> - Run an Android build using Gradle and optionally start the emulator for unit tests.
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="clip_image005" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2015/01/clip_image005.png" alt="clip_image005" width="400" height="157" border="0" /></p>
</li>
<li><b>CMake</b> - Cross platform build system. I have never used it but it really does sound handy.
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="clip_image006" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2015/01/clip_image006.png" alt="clip_image006" width="400" height="111" border="0" /></p>
</li>
<li><b>Cmd Script</b> - Run a Windows cmd or batch script and optionally allow it to change the environment
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="clip_image007" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2015/01/clip_image007.png" alt="clip_image007" width="400" height="151" border="0" /></p>
</li>
<li><b>Jake</b> - Javascript build tool, similar to Make or Rake. Built to work with Node.js
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="clip_image008" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2015/01/clip_image008.png" alt="clip_image008" width="400" height="125" border="0" /></p>
</li>
<li><b>MSBuild</b> - Build with MSBuild; In the pre-2010 builds everything was done in MSBuild and in 2010+ (XAML Builds) these build types were only supported in the legacy build template, "UpgradeTemnplate.xaml". You do not need Visual Studio installed to execute this, but your compilation might.
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="clip_image009" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2015/01/clip_image009.png" alt="clip_image009" width="400" height="217" border="0" /></p>
</li>
<li><b>Visual Studio Build</b> - This build is executed through Visual Studio and should run in the same way that it would locally.
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="clip_image010" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2015/01/clip_image010.png" alt="clip_image010" width="400" height="238" border="0" /></p>
</li>
<li><b>VSTest</b> - You can run tests using the Visual Studio Test Runner. This runner will load tests from any framework that has a test adapter so it supports; MS Test, jUnit, xUnit, mbUnit, and others.
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="clip_image011" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2015/01/clip_image011.png" alt="clip_image011" width="400" height="108" border="0" /></p></li>
<li><b>Xcode Build</b> - This task allows you to build an Xcode project with the xcodebuild tool. Microsoft has had a new strategy for a while to support everyone else's stuff and as they release new versions of their products is it becoming more and more obvious that this is no longer a case of lip service.
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="clip_image012" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2015/01/clip_image012.png" alt="clip_image012" width="400" height="197" border="0" /></p>
</li>
<li><b>PowerShell</b> - Need to run a PowerShell? In TFS 2013 the build workflows were simplified to allow PowerShell both post and pre build as well as post and pre-test. Now you can insert a task any place you like in the build process. PowerShell will let you do anything from moving files around to manipulating the build numbers.
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="clip_image013" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2015/01/clip_image013.png" alt="clip_image013" width="400" height="128" border="0" /></p>
</li>
<li><b>Process Runner</b> - Is the logic that you need to run wrapped up in an executable? Use the Process Runner to execute any executable process.
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="clip_image014" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2015/01/clip_image014.png" alt="clip_image014" width="400" height="170" border="0" /></p>
</li>
<li><b>Azure Cloud Service Deployment via PowerShell</b> – Just like the old Xaml templates to do the same job here is a pre-configured PowerShell command to do the deployment. You can always create a customer PowerShell is you need it, but this is a helper.
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="clip_image015" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2015/01/clip_image015.png" alt="clip_image015" width="400" height="240" border="0" /></p>
</li>
<li><b>Azure PowerShell</b> – Do you ever feel the need to run some PowerShell on one of your servers as part of a build? I don't, as I use Release Management for environmental bits, but if you have an immature build process you may need this.
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="clip_image016" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2015/01/clip_image016.png" alt="clip_image016" width="400" height="124" border="0" /></p>
</li>
<li><b>Azure Web Site Deployment via PowerShell</b> – I just want to deploy my website to azure! Well here you you go.
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="clip_image017" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2015/01/clip_image017.png" alt="clip_image017" width="400" height="141" border="0" /></p>
</li>
</ul>
<p>This is just the list that is available in the preview, which is alfa. The plan, as I currently understand it, is to make this extensible so that you can create any sort of tasks that you like and have them listed in the system. At the moment however there is no way to do this and I am not sure when this will happen.</p>
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="clip_image018" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2015/01/clip_image018.png" alt="clip_image018" width="762" height="418" border="0" /></p>
<p>The second tab is the "Options" tab. This is a list of general options that applicable to any build that you would run. Here we can select:</p>
<ul>
<li><strong>MultiConfiguration</strong> - This allows us to build more than one configuration as part of the same pass. You can even elect to run them in parallel. You just enter the same name that you have in the configuration pick-list in Visual Studio to either build more than one, or something other than the default. I have used this before to have websites built locally use different parameters than those built on the server. That way I can have my local developer setting built by default, and then have things like the connection string replaced at compilation time with a generic "__connectionStrong__" value for Release management.</li>
<li><strong>Copy to Staging Folder</strong> - In previous versions of Team Build this was more or less a non-optional step as the VS Test platform needed all of the files copied to the staging location for testing. Now you can control both what files are picked up and where to. This will be very useful for output that is not the traditional "bin" output.</li>
<li><strong>Create Build Drop</strong> - You might ask why you would not want to have a build drop created but I have seen this for teams with large output and many CI's. I may not need all the output. The traditional option here is to drop everything onto a network share with a UNC path. However TFS 2012 introduced the concept of a "Server drop". This is where the build output is stored as a zip files inside TFS. The advantage to this is that you have one location to backup as the build output is an organisational asset. I prefer server drops every time.</li>
</ul>
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="clip_image019" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2015/01/clip_image019.png" alt="clip_image019" width="762" height="418" border="0" /></p>
<p>Currently the new Team Build vNext system only support Git as the source repository, but you can also select Github and point to any repository that you like. Although I have not tried it I believe that it will support any Git repository that uses the same protocols as GitHub. Nice…</p>
<p>Info: VSO Build vNext has built in support for GitHub builds</p>
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="clip_image020" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2015/01/clip_image020.png" alt="clip_image020" width="762" height="418" border="0" /></p>
<p>In addition to where to get the source code from you may need to create some custom variables that will be available as part of the build. These would be available in your scripts and any other location. There are some enforced variables and most are configurable.</p>
<p>You may use this to inject an option like "HardenPlatfrorm" that takes a Boolean option and you can then use that in your scripts and commands to choose wither you apply your application hardening techniques for piracy protection. Allows you to easily turn it off and on per build...</p>
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="clip_image021" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2015/01/clip_image021.png" alt="clip_image021" width="762" height="418" border="0" /></p>
<p>At the moment the only trigger available is "Continuous Integration" or CI. I would expect in the future to maintain the ability to Schedule builds as well and I really like the fact that you select it with a check-box rather than a radio-button. That bodes well for the future.</p>
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="clip_image022" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2015/01/clip_image022.png" alt="clip_image022" width="762" height="418" border="0" /></p>
<p>"General" configuration contains the last few nuggets of usefulness. First is the pre-defined default queue and maybe a description for the build. I am hoping that we can dynamically update the build number from within the tasks as this is what the majority of my customers want. It just makes sense, to me, to be able to have the build number reflect the version of the code that is being built.</p>
<p>For TFVC I normally change the build number to be something like "1.3.$(YY)$(DayofYear)$(rev:.r)" which would produce something like "1.3.15001.1" as the build number. I would then have a PowerShell that stripped that build number and used it for the DLL's and the Nuget packages that are produced as part of the build. This works great when we have a single build definition per branch.</p>
<p>However, for Git we need something a little different. With Git builds we build all branches (potentially) with the same build definition. So here we want to have a file checked into the branch that has the filter above so that it can be different per branch. That means that the first thing that we need to do as part of the build is to have a PowerShell execute that reads that file and changes the build name in TFS to match. We will see if that is possible in the new build system as it was hard, but not impossible, in the old one.</p>
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="clip_image023" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2015/01/clip_image023.png" alt="clip_image023" width="762" height="418" border="0" /></p>
<p>Finally, a much requested feature. Most folks want to do a little bit of audit on their build configuration as from some reason folks go in there and change stuff. Now you will know not only who did the change but what they changed. Just above the entry is a little "Diff" button…</p>
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="clip_image024" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2015/01/clip_image024.png" alt="clip_image024" width="762" height="418" border="0" /></p>
<p>…Where you get a full diff of the configuration changes that were made between edits. This makes it really easy to see what was changed and the comment should give you an idea of why. Here you can see that I added a trigger of type 2 (CI).</p>
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border-width: 0px;" title="clip_image025" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2015/01/clip_image025.png" alt="clip_image025" width="661" height="418" border="0" /></p>
<p>You now have a build definition configured and you can queue a new build. You can see the Associated commits and other information coming in immediately and there is a new real-time (kinda) command window where it shows the status of the build as it executes.</p>
<h3>Conclusion</h3>
<p>All in all I am very impressed with the current system. My only issue, as you see the build failed above, is that I get a PowerShell version miss match during execution. This may be due to me using Windows Server Technical Preview as by build platform and I have reached out to the awesome build guys to find out what the issue is. In the mean time I will likely build out a Server 2012 R2 to do more testing…</p>