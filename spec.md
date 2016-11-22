---
layout: page
title: TextBundle Specification
navigationTitle: Specification
position: 1
---
The purpose of the TextBundle file format is to simplify the exchange of various plain text files together with additional images between sandboxed applications. By using a single package file, applications do not need to acquire additional sandbox extensions to access files referenced by a plain text document. It can be used as container for various plain text formats, like Markdown or Fountain.

## File Type
There are two variants of the TextBundle format: The *package format* and the *compressed format*.

### Package Format
The [package][1] format is designed to simplify exchange between applications: For example, it can be used to pass a Markdown file together with its assets from an editor to an export tool. 

The package format uses the path extension `.textbundle`. The UTI of a TextBundle package is `org.textbundle.package` which inherits from the generic package UTI `com.apple.package`.

### Compressed Format
Alternatively, TextBundles can be stored inside a compressed [Zip][2] container. This is especially useful for exchanging files between users. 

The compressed format uses the path extension `.textpack`. The UTI of compressed TextBundles is `org.textbundle.compressed` which inherits from the ZIP format UTI `com.pkware.zip-archive`.

### Deriving Own Formats
Generally, you are free to derive your own format from TextBundle. In this case, your subformat just needs to use a different path extension and inherits its UTI either from `org.textbundle.package` or `org.textbundle.compressed`. With a custom format you can ensure additional properties of a TextBundle such as the availability of custom meta data or special asset files. 

## Structure of a Text Bundle
A TextBundle package contains the following files:

| File name   |  Content
|-------------|-------------------------------------------------------------------------------------------------------------------------
| `info.json` | All meta information about the bundle. See section “The Meta Data File”.
| `text.*`    | The actual plain text contents. (Whereas \* is an arbitrary file extension)
| `assets/`   | All asset files referenced from the plain text file. 

To ensure proper integration with iOS apps these filenames should be written in lower case.

## The Meta Data file
The `info.json` file contains all meta data about the TextBundle. It is a JSON file using the following key / value pairs:

| Key                   | Type       | Version | Optional | Description
|-----------------------|-------------------------------------------------------------------------------------------------------------------------
| `version`             | Integer    | 1       | NO       | The version number of the file format. Latest version is 2.
| `type`                | String     | 2       | NO       | The UTI of the `text.*` file. E.g. set to `net.daringfireball.markdown` for Markdown.
| `transient`           | Bool       | 1       | YES      | Whether or not the bundle is a temporary container solely used for exchanging a document between applications. See section “Cooperating With Other Applications”. Defaults to "false".
| `creatorURL`          | String     | 1       | YES      | The URL of the application that originally created the TextBundle. Can be used by viewers to switch back to the originating editor.
| `creatorIdentifier`   | String     | 1       | YES      | The bundle identifier of the application that created the file.
| `sourceURL`           | String     | 2       | YES      | The URL of the file used to generate the TextBundle. Can be used to switch back to a source file within the originating editor app.

Additionally, the meta data file can contain application-specific information. Application-specific information must be stored inside a nested dictionary. The dictionary is referenced by a key using the application bundle identifier (e.g. `com.example.myapp`). This dictionary should contain at least a version number to ensure backwards compatibility.

The following shows an example of the contents of an `info.json` file with an additional application-specific information block:

	{
	    "version":              2,
	    "type":                 "net.daringfireball.markdown",
	    "transient":            true,
	    "creatorURL":           "file:///Applications/MyApp",
	    "creatorIdentifier":    "com.example.myapp",
	    "sourceURL":            "file:///Users/johndoe/Documents/mytext.markdown",
	    "com.example.myapp":    {
	                             "version":    9,
	                             "customKey":  "aCustomValue"
	                            }
	}

## Referencing Assets
Inside the text file, all assets must be referenced by a relative path prefixed by `assets/`. By that, even apps that are unable to open TextBundles can correctly process the contents of a bundle: they only need to access the `text.markdown` file directly. The following paragraph shows an example of an image reference inside a Markdown file packaged by a TextBundle:

	This paragraph references an image: ![](assets/example.png)

When exporting files into TextBundles, plain text editors should automatically add the `assets/` prefix inside all image references. This way, users do not need to consider the usage of TextBundles.

## Cooperating With Other Applications
TextBundles are meant to be opened, processed and modified by multiple applications at once. Therefore, applications must behave cooperatively on a bundle file. Whenever an application overwrites a TextBundle it should pay attention that any application-specific meta data of other applications is kept.

The only exception to this rule are *transient TextBundles*: Inside its meta data file, a bundle can be marked as transient. In this case it is meant as a temporary container for exchanging contents between apps. The application that originally created the TextBundle may overwrite the bundle regardless of any other application. 

TextBundles should be observed for changes using [file presenters][3] and access those files using [file coordination][4] for ensuring changes of other applications to be properly recognized. This is implicitly achieved if applications use the standard document classes `NSDocument` or `UIDocument`.

[1]:	https://developer.apple.com/library/mac/documentation/CoreFoundation/Conceptual/CFBundles/DocumentPackages/DocumentPackages.html#//apple_ref/doc/uid/10000123i-CH106-SW1 "Packages in Cocoa"
[2]:	http://www.pkware.com/documents/casestudies/APPNOTE.TXT
[3]:	https://developer.apple.com/library/ios/documentation/FileManagement/Conceptual/FileSystemProgrammingGuide/FileCoordinators/FileCoordinators.html
[4]:	https://developer.apple.com/library/ios/documentation/FileManagement/Conceptual/FileSystemProgrammingGuide/FileCoordinators/FileCoordinators.html#//apple_ref/doc/uid/TP40010672-CH11-SW3