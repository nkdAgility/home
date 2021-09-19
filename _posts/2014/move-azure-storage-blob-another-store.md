---
ID: 10778
post_title: >
  Move an Azure storage blob to another
  store
post_name: move-azure-storage-blob-another-store
author: >
  Martin Hinshelwood (He/Him)
  nkdAgility.com
post_date: 2014-10-14 15:15:29
post_excerpt: '<p class="lead">Move an Azure storage blob to another store took a little bit longer than I thought that it would. All I wanted to do was move a VHD from one storage account to another. However this is a little more complicated than it seems on the surface.</p>'
layout: post
link: >
  https://nkdagility.com/blog/move-azure-storage-blob-another-store/
published: true
tags:
  - Azure
  - Blob
  - Start-AzureStorageBlobCopy
  - Storage
  - VHD
categories:
  - 'Install &amp; Configure'
  - 'Problems &amp; Puzzles'
---
<p class="lead">Move an Azure storage blob to another store took a little bit longer than I thought that it would. All I wanted to do was move a VHD from one storage account to another. However this is a little more complicated than it seems on the surface.</p>
<p>I am working on teaching the <a href="http://nakedalmweb.wpengine.com/training/courses/managing-projects-microsoft-visual-studio-team-foundation-server-2013/">Managing Projects with Microsoft Visual Studio Team Foundation Server 2013</a> course in Cheltenham this week and have been <a href="http://nakedalmweb.wpengine.com/creating-training-virtual-machines-azure/">creating training virtual machines in Azure</a>. My template is 80GB and it is quite an arduous task to upload it. I now want to move it to a new, less temporary, home.</p>
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; margin: 0px; display: inline; padding-right: 0px; border: 0px;" title="clip_image001" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2014/10/clip-image0012.png" alt="clip_image001" width="800" height="314" border="0" /></p>
<p>I want to move my training VM from the "trainingeu" storage account to the "almtrainingvm" one. This is really just a refactor now that I have everything working and have thought about a new home. The copy process however is a little bit convoluted, especially as both containers are marked as private.</p>
<p>What I really want to be able to do is just call "Copy-AzureStorageBlob -source <a href="https://trainingeu.blob.core.windows.net/vhds/bkvm-2013-3.vhd">https://trainingeu.blob.core.windows.net/vhds/bkvm-2013-3.vhd</a> -destination <a href="https://almtrainingvm.blob.core.windows.net/vhds/bkvm-2013-3.vhd">https://almtrainingvm.blob.core.windows.net/vhds/bkvm-2013-3.vhd</a>" and be done with it. But alas… this is not to be as we need to authenticate to both storage accounts separately even though we are authenticated against the main account.</p>
<p>So… we need a little more PowerShell than I wanted:</p>
<pre class="lang:default decode:true ">Select-AzureSubscription "Pay-As-You-Go"

### Source VHD

$sourceUri = "https://trainingeu.blob.core.windows.net/vhds/bkvm-2013-3.vhd"

$sourceStorageAccount = "trainingeu"

$sourceStorageKey = "bla"

$sourceContext = New-AzureStorageContext –StorageAccountName $srcStorageAccount `

-StorageAccountKey $srcStorageKey

### Target VHD

$targetName = "bkvm-2013-3.vhd"

$targetStorageAccount = "almtrainingvm"

$targetStorageKey = "bla"

$targetContainerName = "vhds"

$targetContext = New-AzureStorageContext –StorageAccountName $targetStorageAccount `

-StorageAccountKey $targetStorageKey

$blob1 = Start-AzureStorageBlobCopy -srcUri $sourceUri -SrcContext $sourceContext -DestContainer $targetContainerName -DestBlob $targetName -DestContext $targetContext
</pre>
<p>&nbsp;</p>
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; margin: 0px; display: inline; padding-right: 0px; border: 0px;" title="clip_image002" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2014/10/clip-image0022.png" alt="clip_image002" width="800" height="70" border="0" /></p>
<p>Why we can't do this with URL's and an authenticated account I do not know… but this is what we got and we have to roll with it.</p>
<p><img style="background-image: none; padding-top: 0px; padding-left: 0px; display: inline; padding-right: 0px; border: 0px;" title="clip_image003" src="http://nakedalmweb.wpengine.com/wp-content/uploads/2014/10/clip-image0032.png" alt="clip_image003" width="800" height="312" border="0" /></p>
<p>Now that I have my VHD over here I can change my default store and create my Virtual Machines from this VHD instead of the other one. Not the easiest task, but now I have some lovely PowerShell I should be able to move VHD's between Azure Storage Accounts any time I like.</p>
