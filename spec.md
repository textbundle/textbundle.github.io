---
layout: page
title: TextBundle Specification
navigationTitle: Specification
position: 1
---
The purpose of the TextBundle file format is to simplify the exchange of Markdown files and additional image files between sandboxed applications. By using a single package file, applications do not need to acquire additional sandbox extensions to access files referenced by a Markdown document.

## File Type
TextBundles are [package files][1] using the path extension `.textbundle`. The UTI of TextBundles is `org.textbundle.package` which inherits from the generic package UTI `com.apple.package`.

## Structure of a Text Bundle
A TextBundle package contains the following files:

| File name   |  Content
|-------------|-------------------------------------------------------------------------------------------------------------------------
| `info.json` | All meta information about the bundle. See section “The Meta Data File”.
| `text.md`   | The actual Markdown contents.
| `assets/`   | All asset files referenced form the Markdown file. 

To ensure proper integration with iOS apps these filenames should be written in lower case.

## The Meta Data file
The `info.json` file contains all meta data about the TextBundle. It is a JSON file using the following key / value pairs:

| Key                   | Type       | Description
|-----------------------|-------------------------------------------------------------------------------------------------------------------------
| `version`             | Integer    | The version number of the file format. Currently set to 1.
| `transient`           | Bool       | Whether or not the bundle is a temporary container solely used for exchanging a document between applications. See section “Cooperating With Other Applications”
| `creatorURL`          | String     | The URL of the application that originally created the TextBundle. Can be used by Markdown viewers to switch back to the originating editor.
| `creatorIdentifier`   | String     | The bundle identifier of the application that created the file.

Additionally, the meta data file can contain application-specific information. Application-specific information must be stored inside a nested dictionary. The dictionary is referenced by a key using the application bundle identifier (e.g. `com.example.myapp`). This dictionary should contain at least a version number to ensure backwards compatibility.

The following shows an example of the contents of an `info.json` file with an additional application-specific information block:

	{
	    "version":              1,
	    "transient":            true,
	    "creatorURL":           "file:///Applications/MyApp",
	    "creatorIdentifier":    "com.example.myapp",
	    "com.example.myapp":    {
	                             "version":    3,
	                             "customKey":    "aCustomValue"
	                            }
	}

## Referencing Assets
Inside the Markdown file, all assets must be referenced by a relative path prefixed by `assets/`. By that, even apps that are unable to open TextBundles can correctly process the contents of a bundle: they only need to access the `text.md` file directly. The following paragraph shows an example of an image reference inside the Markdown file of a TextBundle:

	This paragraph references an image: ![](assets/example.png)

When exporting files into TextBundles, Markdown editors should automatically add the `assets/` prefix inside all image references. This way, users do not need to consider the usage of TextBundles.

## Cooperating With Other Applications
TextBundles are meant to be opened, processed and modified by multiple applications at once. Therefore, applications must behave cooperatively on a bundle file. Whenever an application overwrites a TextBundle it should pay attention that any application-specific meta data of other applications is kept.

The only exception to this rule are *transient TextBundles*: Inside its meta data file, a bundle can be marked as transient. In this case it is meant as a temporary container for exchanging contents between apps. The application that originally created the TextBundle may overwrite the bundle regardless of any other application. 

TextBundles should be observed for changes using [file presenters][2] and access those files using [file coordination][3] for ensuring changes of other applications to be properly recognized. This is implicitly achieved if applications use the standard document classes `NSDocument` or `UIDocument`.

[1]:	https://developer.apple.com/library/mac/documentation/CoreFoundation/Conceptual/CFBundles/DocumentPackages/DocumentPackages.html#//apple_ref/doc/uid/10000123i-CH106-SW1 "Packages in Cocoa"
[2]:	https://developer.apple.com/library/ios/documentation/FileManagement/Conceptual/FileSystemProgrammingGuide/FileCoordinators/FileCoordinators.html
[3]:	https://developer.apple.com/library/ios/documentation/FileManagement/Conceptual/FileSystemProgrammingGuide/FileCoordinators/FileCoordinators.html#//apple_ref/doc/uid/TP40010672-CH11-SW3