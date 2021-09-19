---
ID: 467
post_title: >
  Adding ToolStripPanel UI Adapter support
  to the Composite UI Application Block
post_name: >
  hinshelm-on-composite-ui-application-block
author: >
  Martin Hinshelwood (He/Him)
  nkdAgility.com
post_date: 2006-06-22 06:30:00
layout: post
link: >
  https://nkdagility.com/blog/hinshelm-on-composite-ui-application-block/
published: true
tags:
  - Code
  - Tools
categories:
  - 'Code &amp; Complexity'
---
I was very supprised to find that CAB did not support a higher level the the ToolStrip in its basic implementation. I resolved to solve this and I have added an adapter and factory for the ToolStripPanel initialy, but I have been having trouble with the ToolStripContainer. So, as my first post, here is the ToolStripPanel code.

There are two parts to this. And two ways to do it. The first is to edit the existing ToolStrip UI factory to include the new code. But I do not like to do this as I may update CAB in the future and do not want to rely on havign to implement the adaptions again.

The second is to inherit from the current classes in you own assembly and to adapt the class to support both. That way you are extending, not replacing.

Here is the code for the new ToolStripUIAdapterFactory factory:

<pre class="csharpcode"> <span class="kwrd">Public</span> <span class="kwrd">Class</span> ToolStripPanelUIAdapter : <span class="kwrd">Inherits</span> UIElementAdapter(Of ToolStrip)
        <span class="kwrd">Private</span> innerToolStripPanel <span class="kwrd">As</span> ToolStripPanel
        <span class="kwrd">Public</span> <span class="kwrd">Sub</span> <span class="kwrd">New</span>(<span class="kwrd">ByVal</span> objToolStripPanel <span class="kwrd">As</span> ToolStripPanel)
            Guard.ArgumentNotNull(objToolStripPanel, <span class="str">"objToolStripPanel"</span>)
            <span class="kwrd">Me</span>.innerToolStripPanel = objToolStripPanel
        <span class="kwrd">End</span> <span class="kwrd">Sub</span>
        <span class="kwrd">Protected</span> <span class="kwrd">Overrides</span> <span class="kwrd">Function</span> Add(<span class="kwrd">ByVal</span> uiElement <span class="kwrd">As</span> ToolStrip) <span class="kwrd">As</span> ToolStrip
            <span class="kwrd">If</span> <span class="kwrd">Me</span>.innerToolStripPanel <span class="kwrd">Is</span> <span class="kwrd">Nothing</span> <span class="kwrd">Then</span>
                <span class="kwrd">Throw</span> <span class="kwrd">New</span> InvalidOperationException()
            <span class="kwrd">End</span> <span class="kwrd">If</span>
            <span class="kwrd">Me</span>.innerToolStripPanel.Join(uiElement, 3)
            <span class="kwrd">Return</span> uiElement
        <span class="kwrd">End</span> <span class="kwrd">Function</span>
        <span class="kwrd">Protected</span> <span class="kwrd">Overrides</span> <span class="kwrd">Sub</span> Remove(<span class="kwrd">ByVal</span> uiElement <span class="kwrd">As</span> ToolStrip)
            <span class="kwrd">If</span> <span class="kwrd">Me</span>.innerToolStripPanel.Controls.Contains(uiElement) <span class="kwrd">Then</span>
                <span class="kwrd">Me</span>.innerToolStripPanel.Controls.Remove(uiElement)
            <span class="kwrd">End</span> <span class="kwrd">If</span>
        <span class="kwrd">End</span> <span class="kwrd">Sub</span>
    <span class="kwrd">End</span> Class</pre>

As you can see it inherits from the CAB class of the same name and overrides the same methods that it does and adds the support for the new Adapter for the ToolStripPanel.

You can now add the factory to the UI Element Adapter Factory Catalog in the AfterShellCreated part of the main shell application:

<pre class="csharpcode"><span class="kwrd">Dim</span> catalog <span class="kwrd">As</span> IUIElementAdapterFactoryCatalog = RootWorkItem.Services.<span class="kwrd">Get</span>(Of IUIElementAdapterFactoryCatalog)()
        catalog.RegisterFactory(<span class="kwrd">New</span> UIElements.ToolStripUIAdapterFactory())</pre>

The CAB framework will now handle ToolStripPanel's as UI Extention Sites with the appropriet factory. Now all we need is the adapter...

Here is the code for the ToolStripPanel Adapter:

<div class="csharpcode">
<pre class="alt"><span class="lnum">   1:  </span>    <span class="kwrd">Public</span> <span class="kwrd">Class</span> ToolStripPanelUIAdapter : <span class="kwrd">Inherits</span> UIElementAdapter(Of ToolStrip)</pre>
<pre><span class="lnum">   2:  </span></pre>
<pre class="alt"><span class="lnum">   3:  </span>        <span class="kwrd">Private</span> innerToolStripPanel <span class="kwrd">As</span> ToolStripPanel</pre>
<pre><span class="lnum">   4:  </span>        <span class="kwrd">Private</span> <span class="kwrd">Shared</span> NumberOfAddedControls <span class="kwrd">As</span> <span class="kwrd">Integer</span> = 0</pre>
<pre class="alt"><span class="lnum">   5:  </span></pre>
<pre><span class="lnum">   6:  </span>        <span class="kwrd">Public</span> <span class="kwrd">Sub</span> <span class="kwrd">New</span>(<span class="kwrd">ByVal</span> objToolStripPanel <span class="kwrd">As</span> ToolStripPanel)</pre>
<pre class="alt"><span class="lnum">   7:  </span>            Guard.ArgumentNotNull(objToolStripPanel, <span class="str">"objToolStripPanel"</span>)</pre>
<pre><span class="lnum">   8:  </span>            <span class="kwrd">Me</span>.innerToolStripPanel = objToolStripPanel</pre>
<pre class="alt"><span class="lnum">   9:  </span>        <span class="kwrd">End</span> <span class="kwrd">Sub</span></pre>
<pre><span class="lnum">  10:  </span></pre>
<pre class="alt"><span class="lnum">  11:  </span></pre>
<pre><span class="lnum">  12:  </span>        <span class="kwrd">Protected</span> <span class="kwrd">Overrides</span> <span class="kwrd">Function</span> Add(<span class="kwrd">ByVal</span> uiElement <span class="kwrd">As</span> ToolStrip) <span class="kwrd">As</span> ToolStrip</pre>
<pre class="alt"><span class="lnum">  13:  </span>            <span class="kwrd">If</span> <span class="kwrd">Me</span>.innerToolStripPanel <span class="kwrd">Is</span> <span class="kwrd">Nothing</span> <span class="kwrd">Then</span></pre>
<pre><span class="lnum">  14:  </span>                <span class="kwrd">Throw</span> <span class="kwrd">New</span> InvalidOperationException()</pre>
<pre class="alt"><span class="lnum">  15:  </span>            <span class="kwrd">End</span> <span class="kwrd">If</span></pre>
<pre><span class="lnum">  16:  </span>            <span class="kwrd">Dim</span> Row <span class="kwrd">As</span> <span class="kwrd">Integer</span> = 2</pre>
<pre class="alt"><span class="lnum">  17:  </span>            <span class="rem">'TODO: work out how to specify row!</span></pre>
<pre><span class="lnum">  18:  </span>            <span class="kwrd">Me</span>.innerToolStripPanel.Join(uiElement, 0)</pre>
<pre class="alt"><span class="lnum">  19:  </span>            <span class="kwrd">Me</span>.innerToolStripPanel.Controls.SetChildIndex(uiElement, NumberOfAddedControls + 1)</pre>
<pre><span class="lnum">  20:  </span>            NumberOfAddedControls += 1</pre>
<pre class="alt"><span class="lnum">  21:  </span>            <span class="kwrd">Return</span> uiElement</pre>
<pre><span class="lnum">  22:  </span>        <span class="kwrd">End</span> <span class="kwrd">Function</span></pre>
<pre class="alt"><span class="lnum">  23:  </span></pre>
<pre><span class="lnum">  24:  </span>        <span class="kwrd">Protected</span> <span class="kwrd">Overrides</span> <span class="kwrd">Sub</span> Remove(<span class="kwrd">ByVal</span> uiElement <span class="kwrd">As</span> ToolStrip)</pre>
<pre class="alt"><span class="lnum">  25:  </span>            <span class="kwrd">If</span> <span class="kwrd">Me</span>.innerToolStripPanel.Controls.Contains(uiElement) <span class="kwrd">Then</span></pre>
<pre><span class="lnum">  26:  </span>                <span class="kwrd">Me</span>.innerToolStripPanel.Controls.Remove(uiElement)</pre>
<pre class="alt"><span class="lnum">  27:  </span>            <span class="kwrd">End</span> <span class="kwrd">If</span></pre>
<pre><span class="lnum">  28:  </span>        <span class="kwrd">End</span> <span class="kwrd">Sub</span></pre>
<pre class="alt"><span class="lnum">  29:  </span></pre>
<pre><span class="lnum">  30:  </span>    <span class="kwrd">End</span> Class</pre>
</div>

This code registers the Top panel, but you can register another or all of them, but only on seperate sites. Once you have register the site you can create and add ToolStrips to it:

<pre class="csharpcode"><span class="kwrd">Dim</span> objToolStip <span class="kwrd">As</span> <span class="kwrd">New</span> System.Windows.Forms.ToolStrip
LocalWorkItem.UIExtensionSites(<span class="str">"MainToolStripPanelSiteName"</span>).Add(objToolStip)
LocalWorkItem.UIExtensionSites.RegisterSite(<span class="str">"MyCustomToolStripSitename"</span>, objToolStip)</pre>

Don't forget the second registration that allows you to add a button to the ToolStrip.

All done... You should now be able to create dynamic tool strips and populate them. If you want to customise command, you will need to create a command adapter for the ToolStripPanel and add it to CAB.