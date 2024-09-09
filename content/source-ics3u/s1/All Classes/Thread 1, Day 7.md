---
tags:
excludeBacklinks: true
excludeFromExplorer: true
enableToc: false
created: 2023-10-27T00:00:00.000-0400
---
## Agenda
1. Productivity: [Negative app](https://apps.apple.com/ca/app/negative/id1378123825?mt=12)
	- Dark mode makes using most parts of our computers comfortable after sundown.
	- PDFs have long been a problem – they still show with a white background.
	- Negative solves this – optionally, try it out.
1. Discussion: [Rubber Duck Debugging](https://rubberduckdebugging.com)
	- Solving logical errors and syntax errors can be frustrating, but everyone deals with it, even experienced programmers.
	- Pairing with a friend to describe what you are trying to do with your code, line by line, can be helpful.
		- Often during this process, you will realize the source of the problem you are having.
	- When a friend is not nearby, [use your duck](https://rubberduckdebugging.com)! 🦆
1. Setup: [SF Symbols App](https://developer.apple.com/sf-symbols/)
	- Not all software developers have graphic design skills.
	- Platform owners like Apple want their users to have a consistent experience when using apps written by different people.
	- One of the ways Apple helps their developers provide that consistent look and feel is by offering a wide variety of built-in images that can be used in apps.
	- Please [download and install](https://devimages-cdn.apple.com/design/resources/download/SF-Symbols-5.dmg) the SF Symbols app now. 
	  > [!TIP]
	  > 
	  > To use an SF Symbol within a SwiftUI layout, try the following code:
	  > ```swift
	  >   Image(systemName: "bolt")
	  >       .resizable()
	  >       .scaledToFit()
	  >       .frame(width: 20)
	  > ```
1. Setup: [[macOS Projects]]
	- Please follow these steps to create a new project for the Bento-Box exercise below.
1. Tutorial: Saving Revisions of Your Work
	- Xcode automatically saves your code as you type.
	- However, it is additionally useful to have "save points" while you author code.
	- Mr. Gordon will explain how to *stage* and *commit* your work to save revisions locally.
	  > [!IMPORTANT]
	  > 
	  >  As you go forward in this course, *always* commit your work frequently with descriptive messages.
	  >  
	  >  This serves as a form of note-taking, makes it easier to debug problems, and if necessary, makes it possible for you to return to a prior version of your code.
1. Exercise: Create a "Bento-Box" Design
	- Marketing teams must be able to convey new features in a concise manner to an audience.
	- In recent years, Apple has used "Bento-Box" graphics to do so.
	- Try to [[Bento Box Example|reproduce this image]] using SwiftUI, or use it as inspiration to design a bento-box themed view related to something you care about.
	- Mr. Gordon will demonstrate how to add images into your project.
	- Use [[SwiftUI Views Mastery]] as a reference.
	- Here is the [starter code discussed in class](https://gist.github.com/lcs-rgordon/3e9812b1dfd2a776137a807bed860db4) and a [[Bento Box Starter Code|screenshot of what it looks like]].
	  > [!HINT]
	  > 
	  > Some keywords to look for examples of:
	  > - foregroundStyle
	  > - cornerRadius
	  > - gradient
	  > - Image
	  >   
	  > **Also:** the keyboard shortcut `Option-Shift-K` produces the Apple logo.

## Things to do before our next class
- [ ] Complete the exercise on layout as described above, then write about what you learned in a portfolio entry on [Notion](https://notion.so).
- [ ] ==Review your portfolio==
	- We will be doing mid-module portfolio reviews early next week.
	- You will have a short private conversation with Mr. Gordon, and:
		- describe what you have done well by using the evidence in your portfolio
		- identify what you might do to improve
		- categorize your current level of achievement as one of these levels:
			- approaching expectations
			- meeting expectations
			- exceeding expectations