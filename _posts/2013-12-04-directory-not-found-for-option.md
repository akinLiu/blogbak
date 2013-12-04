---
layout: post
title: "ld: warning: directory not found for option"
description: ""
category: "xcode 5"
tags: [xcode, iOS]
---
{% include JB/setup %}

I'm getting these warning messages

	ld: warning: directory not found for option '-F"/Users/...."'
I look into it and found this cause by a bug of xcode 5 whene the user adding new files of folders to the project.

Xcode is modifying the 'Library Search Paths' build setting, and making a god-awful mess of it. Instead of adding $(SRCROOT)/ it is adding fully rooted paths to all new items, and adding random amounts of /// into other elements of the string. It also seems to be duplicating source paths in some instances, probably because it's broken the existing ones, and thinks they need adding again.

The solution:

1. Copy out your Library Search Paths string into a text editor.
2. Remove any fully rooted paths that shouldn't be there, and replace them with the usual $(SRCROOT)/MyFiles/ type paths.
3. Remove all extraneous slashes and make sure each path has a " character at beginning and end to protect against spaces in filenames.
4. Paste the edited string back into Build Settings.
5. Clean, then Build. Should be back to normal.

hope to help you!
	
####source:[stackoverflow](http://stackoverflow.com/a/19831462/584254)
	
	
