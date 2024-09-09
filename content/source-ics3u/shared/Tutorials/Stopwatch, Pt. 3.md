---
created: 2023-11-03T00:00:00.000-0400
---
> [!NOTE]
>
> Before you begin following the instructions shown here, be sure you have completed [[Stopwatch, Pt. 2|part 2 of this tutorial]].

## Adding the list

We're almost done! 😎

![[Screen Shot 2022-11-09 at 8.07.23 AM.png|300]]

Here is our goal:

![[IMG_09818EAF16D7-1.jpeg|300]]

All that is left is to create the list.

Lists can adopt many appearances on iOS. This article by Peter Freise [provides an outstanding set of examples on how to format a list](https://peterfriese.dev/posts/swiftui-listview-part3/).

> [!TIP]
>
> Bookmark [Peter's article for future reference](https://peterfriese.dev/posts/swiftui-listview-part3/).

Let's get started on our list. Scroll up to the top of `ContentView`:

![[Screen Shot 2022-11-09 at 8.12.15 AM.png]]

Then add the basic structure of a list with five entries, like this:

![[Screen Shot 2022-11-09 at 8.14.20 AM.png]]

You will notice that the list immediately pushs the rest of the content up to the top of the screen.

That is because a list naturally expands, vertically, to take up all available space, regardless of how many list items it contains.

We want the list to take up only a portion of the space available, so, add a `.frame` view modifier, like this, on lines 45 and 46:

![[Screen Shot 2022-11-09 at 8.16.15 AM.png]]

That helps a bit, but the interface still does not quite match our goal:

![[IMG_09818EAF16D7-1.jpeg|300]]

This is a case where a `Spacer` structure is helpful. Add one above the `Text` view, inside the `VStack`:

![[Screen Shot 2022-11-09 at 8.18.18 AM.png]]

This is pretty good – we still have some work to do – but let's commit and push at this point, with the following message:

```
Added a simple list and made the position of user interface elements mostly match the goal.
```

Now, compared to the goal:

![[IMG_09818EAF16D7-1.jpeg|300]]

... you can see that the visual appearance of our list does not match the goal – our list is rounded, whereas the target list is more square.

If you consult [Peter Friese's article on formatting list views](https://peterfriese.dev/posts/swiftui-listview-part3/), you might see what we need to do:

![[Screen Shot 2022-11-09 at 8.21.40 AM.png]]

Add the `.listStyle` modifier as shown above on lines 50 and 51. This is progress.

If you look very closely, however, you might notice that the inset of the text for each list item is a bit off:

![[Screen Shot 2022-11-09 at 8.24.37 AM.png|300]]

Notice how our list items are just a bit further to the right of the leading edge the **Reset** button, as compared to the goal:

![[IMG_09818EAF16D7-1 copy 3.jpeg|300]]

That can be fixed by adjusting the list items themselves.

We need to apply a view modifier to all the list *items*, but not to the `List` structure itself.

To do this, we can add a `Group` structure around the list items:

![[Adding a Group Structure.gif]]

Now we can attach a view modifier to the `Group` structure, as shown here on lines 50 and 51:

![[Screen Shot 2022-11-09 at 9.57.50 AM.png]]

The view modifier will be applied to all the structures that are part of the group – all five `Text` views in this case.

As a result, the inset of the list items is now `0` on all sides – leading, trailing, top, and bottom.

This is great progress – our app better matches the goal.

So, save your work now by committing and pushing with this message:

```
Made list style better match our goal; also adjusted list item insets.
```

## Mini-Exercise: Complete the list

The list in the current version of our app:

![[Screen Shot 2022-11-09 at 10.43.29 AM.png|300]]

... is very close to matching the goal:

![[IMG_09818EAF16D7-1.jpeg|300]]

You can probably identify a few things that are not quite right:
- text size of a list item
- vertical height of a list item
- tint, or color, of the separator between rows in the list
- some list items need to be a different color

Of course, the list items themselves are also not showing the correct information yet:
- the lap number
- how long that lap took

Using the understanding you have developed in this lesson and earlier lessons – and [resources like this one on how to style lists](https://peterfriese.dev/posts/swiftui-listview-part3/) – finish the interface – make your app's visual appearance match the goal.

> [!HINT]
>
> Consider writing a custom structure to represent a list item – will that help you to avoid writing repetitive code?