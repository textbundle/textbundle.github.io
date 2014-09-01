---
layout: page
title: Welcome to TextBundle.org!
navigationTitle: Home
position: 0
---
The TextBundle file format aims to provide a more seamless user expericence when exchanging Markdown files between sandboxed applications.

Sandboxing is required for all apps available on the Mac and iOS app store, in order to grant users a high level of data security. Sandboxed apps are only permitted access to files explicitly provided by the user - for example Markdown text files. When working with different Markdown applications, sandboxing can cause inconveniences for the user. 

An example: Markdown files may contain references to external images. When sending such a file from a Markdown editor to a previewer, users will have to explicitly permit access to every single image file.

This is where TextBundle comes in. TextBundle brings convenience back - by bundling the Markdown text and all referenced images into a single file. Supporting applications can just exchange TextBundles without asking for additional permissions. Beyond being a simple container, TextBundle includes a standard to transfer additional information - to open up new possibilites for future integration.

You can download a simple example file [here][downloads/example.zip].

## Supporting Apps

<table class="apps">
    <tr>
        <th colspan='2'></th>
	   <th>OS</th>
        <th>Reading</th>
        <th>Writing</th>
    </tr>
    <tr>
        <td class="appicon"><a href='http://www.marked2app.com'><img src='images/apps/marked2.png' /></a></td>
        <td class="appname"><a href='http://www.marked2app.com'>Marked 2</a></td>
	   <td class="appos">Mac</td>
        <td class="appreading">2.3.4 (or newer)</td>
        <td class="appwriting">-</td>
    </tr>
    <tr class="app">
        <td class="appicon"><a href='http://www.ulyssesapp.com'><img src='images/apps/ulysses.png' /></a></td>
        <td class="appname"><a href='http://www.ulyssesapp.com'>Ulysses</a></td>
	   <td class="appos">Mac</td> 
        <td class="appreading">-</td>
        <td class="appwriting">1.2.2 (or newer)</td>
    </tr> 
</table>


Like to join in with your app? Please [drop us a line][1] or write us on [twitter][2]!

[1]:	mailto:info@textbundle.org
[2]:	https://twitter.com/txtbndl