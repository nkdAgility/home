---
ID: 10502
post_title: Migrating to office 365 from Google Mail
post_name: migrating-to-office-365-from-google-mail
author: >
  Martin Hinshelwood (He/Him)
  nkdAgility.com
post_date: 2014-04-30 15:38:04
post_excerpt: '<p class="lead">A few months ago I decided to make use of Office 365 but I have run into a bunch of roadblocks. It seams that Office 365 and Google Mail are not the best of friends. They seam to be in a state of cold war.</p>'
layout: post
link: >
  https://nkdagility.com/blog/migrating-to-office-365-from-google-mail/
published: true
tags:
  - Google
  - Google Mail
  - IMAP
  - Microsoft Office
  - Migration
  - Office 365
categories:
  - 'Tools &amp; Techniques'
---
<p class="lead">A few months ago I decided to make use of Office 365 but I have run into a bunch of roadblocks. Migrating to office 365 from Google Mail as it seams that Office 365 and Google Mail are not the best of friends. They seam to be in a state of cold war.</p>
<p>There are a number of options that are available for migrating / synching your email and data from one mail system to Office365.</p>
<ul>
<li>Add IMAP Account</li>
<li>Add POP account</li>
<li>Batch IMAP cutover</li>
</ul>
<p>Of these options I would prefer the first IMAP option. There is no way I am going through the trauma of POP so IMAP it is…</p>
<h2>Attempt 1:&nbsp; IMAP Subscription through the UI</h2>
<p>In an ideal world I want to use IMAP between Office 365 and Gmail for a time so that I can review the new service but maintain the ability to return to the old one if its promises are not met. Unfortunately if you try and configure IMAP with Gmail you will get a message saying that the server is not supported. What? Its just an IMAP server like I use in Outlook with no problems. Delving into the documentation results in:</p>
<blockquote>
<p>Outlook Web App supports IMAP access for most services, <strong>except</strong> Gmail. So please use POP instead. To allow POP access from Gmail, see <a href="http://help.outlook.com/en-US/140/dd181952.aspx">Turn on POP Access Before Connecting to Your Gmail Account</a>.<a href="http://community.office365.com/en-us/forums/158/t/1944.aspx">IMAP with Gmail not working?</a></p>
</blockquote>
<p>For some reason, and I am sure not a technical one, Office 365 will not support IMAP from Google.</p>
<h2>Attempt 2: IMAP Subscription through PowerShell</h2>
<p>So if it will not work through the UI maybe it is an advanced feature that can only be done through command line. Really I was just hoping that whomever implemented the feature added the block in the UI rather than in the actual system. I spent quite some time figuring out how to execute the required PowerShell.</p>
<pre class="lang:default decode:true " >Import-Module MSOnline
$O365Cred = Get-Credential
$O365Session = New-PSSession –ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.outlook.com/powershell -Credential $O365Cred -Authentication Basic -AllowRedirection
Import-PSSession $O365Session
Connect-MsolService –Credential $O365Cred
New-IMAPSubscription -Name "Gmail_IMAP_Subscription" -Mailbox "martin@nakedalm.com" -EmailAddress martin@nakedalm.com -IncomingUserName martin@hinshelwood.com -IncomingPassword (ConvertTo-SecureString -String 'notonyournelly' -AsPlainText -Force) -IncomingServer imap.gmail.com  -IncomingSecurity Ssl -IncomingPort 993
</pre>
<p>As with all PowerShell it is poorly documented but in the end I executed the above PowerShell and my hopes of a sucessfukll result were dashed.</p>
<p><img src="http://nakedalmweb.wpengine.com/wp-content/uploads/2014/04/041614_1437_Office365an1.png" alt="" border="0"/></p>
<p>So they did implement the block deep down in the software. Really I knew that they would have…</p>
<h2>Attempt 3: IMAP Migration through PowerShell</h2>
<p>The third option is to do a PowerShell IMAP Migration. Yes, that is using IMAP to do a one-time move from Google Mail to Office 365. While some of the previous PowerShell was reusable but figuring it out was even more of a pain than for a single account. Here instead of creating a single thing we have to create an async batch session that we can then hook into and see how it is going. This may take a large amount of time to run if you have a lot of mail. I have over 7GB of mail in Google.</p>
<pre class="lang:default decode:true " >Import-Module MSOnline
$O365Cred = Get-Credential
$O365Session = New-PSSession –ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.outlook.com/powershell -Credential $O365Cred -Authentication Basic -AllowRedirection
Import-PSSession $O365Session
Connect-MsolService –Credential $O365Cred
$IMAPMigrationEndPoint = New-MigrationEndpoint -IMAP -Name MrHinshIMAPMigration -MaxConcurrentMigrations 1 -RemoteServer imap.gmail.com -Port 993 -Security SSL
New-MigrationBatch -Name MrHinshIMAPMigration -SourceEndpoint $IMAPMigrationEndPoint.Identity -AutoRetryCount 4 -BadItemLimit 50 -CSVData ([System.IO.File]::ReadAllBytes(“C:\temp\test.csv”)) -AutoStart
</pre>
<p>Once you have executed this ommand Office 365 will connect to all of the accounts stored in the CSV and move them across to Office 365. Slowly… and because it is slowly you need some way to check up on its status.</p>
<pre class="lang:default decode:true " >#Get Status
Get-MigrationBatch | fl</pre>
<p>When you execute the command you get a list of sync's and the number of accounts it is migrating.</p>
<p><img src="http://nakedalmweb.wpengine.com/wp-content/uploads/2014/04/041614_1437_Office365an2.png" alt="" border="0"/></p>
<p>This is really the only way to move from Google Mail to Office 365 and it does work. I say mail coming in almost immediately and it took maybe a few days for all 7gb to come across.</p>
<h2>Conclusion</h2>
<p>Unfortunately Microsoft are not providing the service they should which results in my being unable to move more than just myself to Office365. I have a bunch of family member, only some of which will want to move… and I can't do a partial move.</p>
<p>I have now been over on Office 356 for about 3 months and I have been extremely happy with my business account. I would recommend Office 365 for both small and large organisations. I am using it for business and the integration of Lync, Outlook, and a SharePoint instance gives me lots of flexibility for only £40 for the year. Pretty good really and I believe it to be much cheaper for large organisations if they are running exchange properly.</p>
