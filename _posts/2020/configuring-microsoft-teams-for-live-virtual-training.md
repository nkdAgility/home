---
ID: 44452
post_title: >
  Configuring Microsoft Teams for Live
  Virtual Training
post_name: >
  configuring-microsoft-teams-for-live-virtual-training
author: >
  Martin Hinshelwood (He/Him)
  nkdAgility.com
post_date: 2020-06-22 17:00:00
layout: post
link: >
  https://nkdagility.com/blog/configuring-microsoft-teams-for-live-virtual-training/
published: true
tags: [ ]
categories:
  - Agility
  - 'Tools &amp; Techniques'
---
<!-- wp:paragraph -->
<p>Like most tools, if you want to run successful training in Microsoft Teams you need to do some homework and some configuration before your class. You can just jump in and wing it, but that will not provide a good experience for your students. Currently, I have run more than 6 Live Virtual Training in Microsoft Teams and in a few hours, my 7th will start. I have also recently had to set up Microsoft Teams for my good friend and colleague <a rel="noreferrer noopener" href="https://nkdagility.com/training/trainers/russell-miller/" target="_blank">Russell Miller </a>so that he can also run classes on the platform.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>To date, I have facilitated a couple of Live Virtual F2F for the other trainers at Scrum.org to show them how it works, but we did not go into the configuration. This article will lead any Professional Scrum Trainer that wants to <a rel="noreferrer noopener" target="_blank" href="https://nkdagility.com/blog/delivering-live-virtual-classes-in-microsoft-teams-and-mural/">Deliver Live Virtual Classes in Microsoft Teams</a> through the configuration required to do so.</p>
<!-- /wp:paragraph -->

<!-- wp:image {"id":44461,"sizeSlug":"large"} -->
<figure class="wp-block-image size-large"><img src="https://nkdagility.com/wp-content/uploads/2020/06/Delivering-Live-Virtual-Classes-in-Microsoft-Teams-1280x347.jpg" alt="" class="wp-image-44461"/><figcaption>Professional Scrum Foundations for 20 Guests in Microsoft Teams</figcaption></figure>
<!-- /wp:image -->

<!-- wp:paragraph -->
<p>One of the common misconceptions in Teams is that you need a login to be able to participate in a meeting. This is incorrect and you can invite anyone you like to a meeting. For example, I am hosting a public event in Teams on Wednesday for Future of Work Scotland. No authentication required, except joining the meetup to get the URL just like Zoom or Webex.</p>
<!-- /wp:paragraph -->

<!-- wp:core-embed/meetup-com {"url":"https://www.meetup.com/the-future-of-work-in-Scotland/","type":"rich","providerNameSlug":"meetup","className":""} -->
<figure class="wp-block-embed-meetup-com wp-block-embed is-type-rich is-provider-meetup"><div class="wp-block-embed__wrapper">
https://www.meetup.com/the-future-of-work-in-Scotland/
</div><figcaption>Future of Work Scotland</figcaption></figure>
<!-- /wp:core-embed/meetup-com -->

<!-- wp:paragraph -->
<p>However, if you want access to Files, Chat, Channels, Breakout Rooms, Tabs, and Apps then participants need to be authenticated. They need to be a member and not just an external guest.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>For that we need:</p>
<!-- /wp:paragraph -->

<!-- wp:list -->
<ul><li>Azure Active Directory Tennant</li><li>Microsoft 365 Subscription</li><li>Guest Access Enabled</li><li>Gold Plating for a Professional Scrum Class Experience</li></ul>
<!-- /wp:list -->

<!-- wp:heading -->
<h2 id="h-creating-your-azure-ad">Creating your Azure AD </h2>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>The name that Microsoft gives to the container in all of its services for a specific entity is called a Tennant. Each Tennant has a unique ID, it has root authentication, and it has a bunch of services that use it.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>You as a member of Tennant1 can be a guest in Tennant2. This means that you use your corporate credential (assuming that Tennant1 is your employer), to access another corporate system. This is called <a rel="noreferrer noopener" href="https://docs.microsoft.com/en-us/azure/active-directory/b2b/what-is-b2b" target="_blank">Azure AD B2B</a> and is the basis upon which we invite Guests to access our Team.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>Just like Google Apps, this creates your security construct. You can have this created for you when you buy a subscription for Microsoft 365, but I always prefer to be explicit. Understanding how things go together will help you administer this in the future.</p>
<!-- /wp:paragraph -->

<!-- wp:group {"textColor":"very-light-gray","style":{"color":{"background":"#621a75"}}} -->
<div class="wp-block-group has-very-light-gray-color has-text-color has-background" style="background-color:#621a75"><div class="wp-block-group__inner-container"><!-- wp:heading {"level":4,"textColor":"very-light-gray"} -->
<h4 class="has-very-light-gray-color has-text-color" id="h-task-1-create-azure-ad-tennant"><strong>TASK 1: Create Azure AD Tennant</strong></h4>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>The First Step is to create an Azure AD Tennant. This is free and will be the foundation of all the rest of the setup.</p>
<!-- /wp:paragraph -->

<!-- wp:list -->
<ul><li><a rel="noreferrer noopener" href="https://azure.microsoft.com/en-gb/services/active-directory/" target="_blank">Create your first Active Directory</a></li><li><a href="https://portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade" target="_blank" rel="noreferrer noopener">Administer your existing Active Directory</a></li></ul>
<!-- /wp:list --></div></div>
<!-- /wp:group -->

<!-- wp:heading -->
<h2 id="h-getting-setup-with-a-microsoft-365-subscription">Getting Setup with a Microsoft 365 Subscription</h2>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>Since Teams is part of Microsoft 365 and relies on a bunch of underlying services you first need to get a Subscription.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>The lowest subscription to Microsoft 365 that includes Teams is "<strong><a href="https://www.microsoft.com/en-gb/microsoft-365/business/microsoft-365-business-basic" target="_blank" rel="noreferrer noopener">Microsoft 365 Business Basic</a></strong>" and at $5/user/month it gives you unlimited Guests which is the bit we care about, as well as the services that back Teams:</p>
<!-- /wp:paragraph -->

<!-- wp:list -->
<ul><li><strong>Exchange </strong>- This gives you a domain and email address. I run my business on this service so martin[at]nkdagility.com is my main account, and it is a full exchange server hosted by Microsoft. Teams are built on Groups, and Groups are in Exchange. Since they are backed by Azure AD they can be used for Security, Membership, and distribution.</li><li><strong>OneDrive </strong>- OneDrive provides the storage for all of the services in Microsofts world, and that also means Sharepoint. When you shave a file onto SharePoint it ends up in OneDrive. One of the really powerful features is that both you and your guests can sync the files locally using OneDrvie and edit them locally with dynamic collaboration to the cloud. OneDrive provides that storage, and collaborative editing capability.</li><li><strong>SharePoint </strong>- Sharepoint has been much maligned the past, and rightly so. I had to install and administer Sharepoint 2007, and Sharepoint 2010 back in the day and it traumatized me so much that I don't even put it on my CV. However, Sharepoint Online is a totally different beast. It's fast and powerful, and provide a web view to your Group with web access to files, calendar, OneNote, and other features. Very Nice.</li><li><strong>Teams </strong>- Teams is the icing on the cake and provides a space similar to Slack, but with all of the features above combine to give you an unbelievable amount of power. On top of it, you can add apps from both Microsoft, and 3rd parties, like Zoom, that add more.</li></ul>
<!-- /wp:list -->

<!-- wp:paragraph -->
<p>These things together as a single package give you the ability to create Groups that have all of the features that your Students need to collaborate.</p>
<!-- /wp:paragraph -->

<!-- wp:image {"id":44455,"sizeSlug":"large"} -->
<figure class="wp-block-image size-large"><img src="https://nkdagility.com/wp-content/uploads/2020/06/image-15-841x720.png" alt="" class="wp-image-44455"/><figcaption>Class Group in Azure AD</figcaption></figure>
<!-- /wp:image -->

<!-- wp:paragraph -->
<p>Its really important to note that once you pick the name of your Microsoft 365 Organisation the URL can no longer be changed. I have changed the name of my business from nakedALM to nkdAgility to naked Agility and still have nakedalm.sharepoint.com as my core URL. At some point Microsoft will fix this, but at the moment... not so much. So choose wisely!</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>You will end up with "yourname.onmicrosoft.com" and the "yourname" part will be appended to SharePoint permanently. </p>
<!-- /wp:paragraph -->

<!-- wp:group {"textColor":"very-light-gray","style":{"color":{"background":"#621a75"}}} -->
<div class="wp-block-group has-very-light-gray-color has-text-color has-background" style="background-color:#621a75"><div class="wp-block-group__inner-container"><!-- wp:heading {"level":4,"textColor":"very-light-gray"} -->
<h4 class="has-very-light-gray-color has-text-color" id="h-task-2-add-microsoft-365-subscription"><strong>TASK 2: Add Microsoft 365 Subscription</strong></h4>
<!-- /wp:heading -->

<!-- wp:paragraph {"textColor":"very-light-gray","style":{"color":{"background":"#621a75"}}} -->
<p class="has-very-light-gray-color has-text-color has-background" style="background-color:#621a75">In order to get set up the first task is to head over to the Microsoft 365 Portal and purchase a subscription. You can also peruse the other subscription levels and their contents as well.</p>
<!-- /wp:paragraph -->

<!-- wp:list -->
<ul><li><a href="https://www.microsoft.com/en-gb/microsoft-365/business/microsoft-365-business-basic" target="_blank" rel="noreferrer noopener">Create a Microsoft 365 Business Basic Subscription </a></li><li><a href="https://admin.microsoft.com" target="_blank" rel="noreferrer noopener">Administer your existing Microsoft 365</a></li></ul>
<!-- /wp:list --></div></div>
<!-- /wp:group -->

<!-- wp:heading -->
<h2 id="h-enabling-guest-access">Enabling Guest Access</h2>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>Before you get started in Microsoft Teams for Live Virtual Classrooms you need to <a rel="noreferrer noopener" href="https://docs.microsoft.com/en-us/microsoftteams/teams-dependencies" target="_blank">Authorize guest access in Microsoft Teams</a>. This has a lot of moving parts as you change the default security stance from "internal only" to "Allow Guests" for all of the services that Guests need to interact with as part of a Teams Team.</p>
<!-- /wp:paragraph -->

<!-- wp:image {"id":44457,"sizeSlug":"large"} -->
<figure class="wp-block-image size-large"><img src="https://nkdagility.com/wp-content/uploads/2020/06/image-17-986x720.png" alt="" class="wp-image-44457"/></figure>
<!-- /wp:image -->

<!-- wp:paragraph -->
<p>This is by far the most complex part of this to set up as there are options in many parts of the system. The link below leads you through how to <a rel="noreferrer noopener" href="https://docs.microsoft.com/en-us/microsoftteams/teams-dependencies" target="_blank">Authorize Guest access in Microsoft Teams</a> and start adding guests. Please note that there is currently a 24h hiatus between enabling guests and it is available in Teams. This is due to the extra load that everyone working from home has added. </p>
<!-- /wp:paragraph -->

<!-- wp:group {"textColor":"very-light-gray","style":{"color":{"background":"#621a75"}}} -->
<div class="wp-block-group has-very-light-gray-color has-text-color has-background" style="background-color:#621a75"><div class="wp-block-group__inner-container"><!-- wp:heading {"level":4,"textColor":"very-light-gray"} -->
<h4 class="has-very-light-gray-color has-text-color" id="h-task-3-enable-guest-access"><strong>TASK 3: Enable Guest Access</strong></h4>
<!-- /wp:heading -->

<!-- wp:paragraph {"textColor":"very-light-gray","style":{"color":{"background":"#621a75"}}} -->
<p class="has-very-light-gray-color has-text-color has-background" style="background-color:#621a75">In order to get set up the first task is to head over to the Microsoft 365 Portal and purchase a subscription. You can also peruse the other subscription levels and their contents as well.</p>
<!-- /wp:paragraph -->

<!-- wp:list -->
<ul><li><a rel="noreferrer noopener" href="https://www.microsoft.com/en-gb/microsoft-365/business/microsoft-365-business-basic" target="_blank"></a><a rel="noreferrer noopener" href="https://docs.microsoft.com/en-us/microsoftteams/teams-dependencies" target="_blank">Authorize Guest access in Microsoft Teams</a></li><li><a href="https://docs.microsoft.com/en-us/sharepoint/turn-external-sharing-on-or-off" target="_blank" rel="noreferrer noopener">Manage sharing settings in Sharepoint</a></li></ul>
<!-- /wp:list --></div></div>
<!-- /wp:group -->

<!-- wp:heading -->
<h2 id="h-enable-external-identities">Enable External Identities</h2>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>In the past everyone connecting to a Team (not merely a meeting) required to have either an Azure AD (corporate identity) or a Microsoft Account (personal identity) in order to get access. If your email had neither then you were prompted to configure a Microsoft Account.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>However recently Microsoft have made this a lot easier with the ability to enable folks to sign in with their existing <a rel="noreferrer noopener" href="https://docs.microsoft.com/en-gb/azure/active-directory/b2b/google-federation" target="_blank">Google Credentials</a> (G Suite or Personal) which covers a very large amount of the guest that I may be adding. But what if the email you add has none of those identities? </p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>There is a feature that is currently in preview called <a rel="noreferrer noopener" href="https://docs.microsoft.com/en-gb/azure/active-directory/b2b/one-time-passcode" target="_blank">one-time passcode authentication</a> that replaces the default flow of being prompted to create a Microsoft Account with a simple passcode.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>If a guest has not accepted the invitation when they hit one of your authenticated URL's, for example, the Team URL, then they are instead sent a one-time passcode to their email address and they can use that to log in for 30 minutes. After which they will automatically be sent a new passcode. Simples!</p>
<!-- /wp:paragraph -->

<!-- wp:quote -->
<blockquote class="wp-block-quote"><p>One-time passcodes are valid for 30 minutes. After 30 minutes, that specific one-time passcode is no longer valid, and the user must request a new one. User sessions expire after 24 hours.</p><cite><a rel="noreferrer noopener" href="https://docs.microsoft.com/en-gb/azure/active-directory/b2b/one-time-passcode" target="_blank">one-time passcode authentication</a></cite></blockquote>
<!-- /wp:quote -->

<!-- wp:paragraph -->
<p>When one of your guests try's to use either the invitation link that was sent to them or the link to the secure resource and:</p>
<!-- /wp:paragraph -->

<!-- wp:list -->
<ul><li>They do not have an Azure AD account</li><li>They do not have a Microsoft account</li><li>The inviting tenant did not set up Google federation for @gmail.com and @googlemail.com users</li></ul>
<!-- /wp:list -->

<!-- wp:paragraph -->
<p>Then the fall-back authentication method will be the one-time passcode. </p>
<!-- /wp:paragraph -->

<!-- wp:group {"textColor":"very-light-gray","style":{"color":{"background":"#621a75"}}} -->
<div class="wp-block-group has-very-light-gray-color has-text-color has-background" style="background-color:#621a75"><div class="wp-block-group__inner-container"><!-- wp:heading {"level":4,"textColor":"very-light-gray"} -->
<h4 class="has-very-light-gray-color has-text-color" id="h-task-4-enable-external-identities"><strong>TASK 4: Enable External Identities</strong></h4>
<!-- /wp:heading -->

<!-- wp:paragraph {"textColor":"very-light-gray","style":{"color":{"background":"#621a75"}}} -->
<p class="has-very-light-gray-color has-text-color has-background" style="background-color:#621a75">This is fantastic and vastly simplifies the experience for students accessing your training class. Both Google and one-time passcode are a must to configure!</p>
<!-- /wp:paragraph -->

<!-- wp:list -->
<ul><li><a rel="noreferrer noopener" href="https://docs.microsoft.com/en-gb/azure/active-directory/b2b/google-federation" target="_blank">Add Google as an identity provider for B2B guest users</a></li><li><a href="https://docs.microsoft.com/en-gb/azure/active-directory/b2b/one-time-passcode" target="_blank" rel="noreferrer noopener">Email one-time passcode authentication</a></li></ul>
<!-- /wp:list --></div></div>
<!-- /wp:group -->

<!-- wp:heading -->
<h2 id="h-gold-plating-for-a-professional-scrum-class-experience">Gold Plating for a Professional Scrum Class Experience</h2>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>While you are now good to go for running Professional Scrum classes there is some cream that you can use to create a more professional experience for your students:</p>
<!-- /wp:paragraph -->

<!-- wp:image {"id":44459,"sizeSlug":"large"} -->
<figure class="wp-block-image size-large"><img src="https://nkdagility.com/wp-content/uploads/2020/06/image-19-1034x720.png" alt="" class="wp-image-44459"/><figcaption>Branding and Custom Domain in action</figcaption></figure>
<!-- /wp:image -->

<!-- wp:list -->
<ul><li><a href="https://docs.microsoft.com/en-us/azure/active-directory/fundamentals/customize-branding" target="_blank" rel="noreferrer noopener">Add branding to your organization's Azure Active Directory sign-in page</a></li><li><a href="https://docs.microsoft.com/en-us/microsoft-365/admin/setup/add-domain?view=o365-worldwide" target="_blank" rel="noreferrer noopener">Add a domain to Microsoft 365</a></li><li><a href="https://docs.microsoft.com/en-us/microsoft-365/admin/manage/release-options-in-office-365?view=o365-worldwide" target="_blank" rel="noreferrer noopener">Get new Features Earlier</a></li></ul>
<!-- /wp:list -->

<!-- wp:heading -->
<h2 id="h-conclusion-to-configuring-microsoft-teams-for-live-virtual-training">Conclusion to Configuring Microsoft Teams for Live Virtual Training</h2>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>While there is a lot of setup and configuration before you can run your first class the holistic experience for students is far better than any of the other platforms that I have used or participated in.</p>
<!-- /wp:paragraph -->