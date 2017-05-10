---
layout: page
title: Welcome to TextBundle.org!
navigationTitle: Home
position: 0
---
The TextBundle file format aims to provide a more seamless user expericence when exchanging plain text files, like Markdown or Fountain, between sandboxed applications.

Sandboxing is required for all apps available on the Mac and iOS app store, in order to grant users a high level of data security. Sandboxed apps are only permitted access to files explicitly provided by the user - for example Markdown text files. When working with different Markdown applications, sandboxing can cause inconveniences for the user.

An example: Markdown files may contain references to external images. When sending such a file from a Markdown editor to a previewer, users will have to explicitly permit access to every single image file.

This is where TextBundle comes in. TextBundle brings convenience back - by bundling the Markdown text and all referenced images into a single file. Supporting applications can just exchange TextBundles without asking for additional permissions. Beyond being a simple container, TextBundle includes a standard to transfer additional information - to open up new possibilites for future integration.

You can download a simple example file for a [TextBundle file (Version 2)][2] and its compressed variant [TextPack][3]. We provide also an example for apps only supporting [TextBundle file (Version 1)][1].

## Supporting Apps

<table class="apps">
    <tr>
        <th colspan='2'></th>
       <th>OS</th>
        <th class="appreading">Reading</th>
        <th class="appwriting">Writing</th>
        <th class="appstandard">Standard</th>
    </tr>
    <tr>
        <td class="appicon"><a href='http://bear-writer.com/'><img src='images/apps/bear.png' /></a></td>
        <td class="appname"><a href='http://bear-writer.com/'>Bear</a></td>
       <td class="appos">macOS, iOS</td>
        <td class="appreading">1.0 +</td>
        <td class="appwriting">1.0 +</td>
        <td class="appstandard">v2</td>
    </tr>
    <tr class="app">
        <td class="appicon"><a href='http://basilsalad.com/ios/go-edit/'><img src='images/apps/goedit.png' /></a></td>
        <td class="appname"><a href='http://basilsalad.com/ios/go-edit/'>Go Edit</a></td>
        <td class="appos">iOS</td>
        <td class="appreading">1.0 +</td>
        <td class="appwriting">1.0 +</td>
		<td class="appstandard">v2 (md, html)</td>		
    </tr>
    <tr class="app">
        <td class="appicon"><a href='http://www.highlightsapp.net'><img src='images/apps/highlights.png' /></a></td>
        <td class="appname"><a href='http://www.highlightsapp.net'>Highlights</a></td>
       <td class="appos">macOS</td>
        <td class="appreading">-</td>
        <td class="appwriting">1.0 +</td>
        <td class="appstandard">v1</td>     
    </tr>
    <tr>
        <td class="appicon"><a href='http://www.marked2app.com'><img src='images/apps/marked2.png' /></a></td>
        <td class="appname"><a href='http://www.marked2app.com'>Marked 2</a></td>
       <td class="appos">macOS</td>
        <td class="appreading">2.3.4 +</td>
        <td class="appwriting">-</td>
        <td class="appstandard">v1</td>
    </tr>
    <tr>
        <td class="appicon"><a href='http://www.mindnode.com'><img src='images/apps/mindnode.png' /></a></td>
        <td class="appname"><a href='http://www.mindnode.com'>MindNode</a></td>
       <td class="appos">macOS, iOS</td>
        <td class="appreading">2.5&nbsp;+&nbsp;(macOS), 4.5&nbsp;+&nbsp;(iOS)</td>
        <td class="appwriting">2.5&nbsp;+&nbsp;(macOS), 4.5&nbsp;+&nbsp;(iOS)</td>
        <td class="appstandard">v2</td>
    </tr>
    <tr class="app">
        <td class="appicon"><a href='http://xelaton.com/index.php?lang=en&rubrik=Applications--Myary'><img src='images/apps/myary.png' /></a></td>
        <td class="appname"><a href='http://xelaton.com/index.php?lang=en&rubrik=Applications--Myary'>Myary</a></td>
        <td class="appos">macOS</td>
        <td class="appreading">1.5.0 +</td>
        <td class="appwriting">1.5.0 +</td>
		<td class="appstandard">v2</td>		
    </tr>
    <tr class="app">
        <td class="appicon"><a href='http://xelaton.com/index.php?lang=en&rubrik=Applications--Note-C'><img src='images/apps/note-c.png' /></a></td>
        <td class="appname"><a href='http://xelaton.com/index.php?lang=en&rubrik=Applications--Note-C'>Note-C</a></td>
        <td class="appos">macOS</td>
        <td class="appreading">1.5.0 +</td>
        <td class="appwriting">1.5.0 +</td>
		<td class="appstandard">v2</td>		
    </tr>
    <tr class="app">
        <td class="appicon"><a href='http://www.aflava.com'><img src='images/apps/smartdown.png' /></a></td>
        <td class="appname"><a href='http://www.aflava.com'>Smartdown II</a></td>
       <td class="appos">Windows</td>
        <td class="appreading">-</td>
        <td class="appwriting">0.8.2 +</td>
		<td class="appstandard">v2</td>		
    </tr>
    <tr class="app">
        <td class="appicon"><a href='http://www.toketaware.com/'><img src='images/apps/ithoughts.png' /></a></td>
        <td class="appname"><a href='http://www.toketaware.com/'>iThoughts</a></td>
       <td class="appos">macOS, iOS, Windows</td>
        <td class="appreading">-</td>
        <td class="appwriting">4.11&nbsp;+&nbsp;(macOS), 2.3&nbsp;+&nbsp;(Windows), 2.7&nbsp;+&nbsp;(iOS)</td>
		<td class="appstandard">v1</td>		
    </tr>
    <tr class="app">
        <td class="appicon"><a href='http://www.ulyssesapp.com'><img src='images/apps/ulysses.png' /></a></td>
        <td class="appname"><a href='http://www.ulyssesapp.com'>Ulysses</a></td>
       <td class="appos">macOS, iOS</td>
        <td class="appreading">2.7</td>
        <td class="appwriting">1.2.2 +</td>
        <td class="appstandard">v2</td>     
    </tr>
</table>


### Quick Look on OS X
Properly formatted TextBundle files can be viewed with Quick Look on OS X by installing [Brett Terpstra's fork of the MultiMarkdown QuickLook plugin][6]. Be sure to run `qlmanage -r` in Terminal after installing or upgrading the plugin.


### Logo
You can download the official logo of TextBundle in various file formats [here](downloads/textbundle-logo.zip). The logo was created by [Brett Terpstra][7]. It is published under the [CC0](https://creativecommons.org/publicdomain/zero/1.0/) license, so you can use it without restrictions.


### Join us!
Like to join in with your app? Please [drop us a line][4] or write us on [twitter][5]!

[1]:    /downloads/example-bundle-v1.zip
[2]:    /downloads/example-bundle-v2.zip
[3]:    /downloads/example.textpack
[4]:    mailto:info@textbundle.org
[5]:    https://twitter.com/txtbndl
[6]:    http://brettterpstra.com/2015/06/03/mmd-quicklook-1-dot-2-with-textbundle-support/
[7]:	http://brettterpstra.com/
