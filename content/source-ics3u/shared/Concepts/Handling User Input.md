---
tags:
created: 2024-01-31T00:00:00.000-0400
---
There is an obvious downside to the current interface of the [[Lists and Selection#Exercise|Guessing Game]] app created in our most recent class:

![[RocketSim_Recording_iPhone_15_Pro_6.1_2024-01-30_13.04.56.gif|301]]

It is inconvenient to have to repeatedly press the **+** or **-** signs.

It would be easier for the user to be able to type in values using the keyboard, like this:

![[RocketSim_Recording_iPhone_15_Pro_6.1_2024-01-30_13.00.20 - 01.gif|301]]

How can we accept user input in this way?

Read on to find out.

## Understanding optional data types

You have already explored the [[Optionals|theoretical concept of optional data types]].

Let's see, now, how to apply optional data types to safely handle the potential for bad user input within an app.

First, to better understand everything involved, we will simulate receiving user input in a command-line environment.

Later in this lesson, we will add text-based input to the Guessing Game app.

Then, you will try applying the same ideas in an exercise.

Right now, please create a new [[Command-Line Projects|command-line macOS app]] named **UserInputExamples**, like this:

![[Screenshot 2024-01-30 at 1.11.39 PM.png]]

When input is received in a text field in an app, the data type is always `String`:

![[RocketSim_Screenshot_iPhone_15_Pro_6.1_2024-01-30_13.13.22.png|301]]

Let's simulate the following user input:

![[RocketSim_Screenshot_iPhone_15_Pro_6.1_2024-01-30_13.15.36.png|301]]

In the command-line app you have just created, copy paste this code in:

```swift
// Simulate user input
let givenInput = "50"
```

... like this:

![[Screenshot 2024-01-30 at 1.17.55 PM.png]]

Press the **Option** key on your keyboard, then click the `givenInput` constant to confirm for yourself that its data type is `String`:

![[Screenshot 2024-01-30 at 1.18.09 PM.png]]

The Swift programming language is *type strict*.

This means that we cannot directly compare a `String` to an `Int`, for example. We can only compare a `String` to a `String`, or an `Int` to an `Int`, and so on.

> [!IMPORTANT]
> **Data types must match** to perform a comparison.

Check this for yourself by adding the following code *below* the code you added earlier:

```swift
// Simulate target number to guess
let target = 37

// Compare input to the target
if givenInput > target {
    print("Guess lower next time.")
}
```

So it looks like this:

![[Screenshot 2024-01-30 at 8.00.17 PM.png]]

Shortly after adding the code, you will see this error message:

![[Screenshot 2024-01-30 at 8.00.42 PM.png]]

The message:

```
Binary operator '>' cannot be applied to operands of type 'String' and 'Int'
```

... is the Swift compiler saying "I can't compare these values."

It's like the old expression:

> "You can't compare apples to oranges".

To perform the comparison, we have to convert the input into an integer first.

Replace all the code on line 16 and after:

![[Screenshot 2024-01-30 at 8.01.23 PM.png]]

... with this code instead:

```swift
// Attempt to convert the String input to an Int
let selectedNumber = Int(givenInput)

// Compare input to the target
if selectedNumber > target {
    print("Guess lower next time.")
}
```

... so that overall, the code looks like this:

![[Screenshot 2024-01-30 at 8.01.57 PM.png]]

Now, on line 17, we take the input provided – `givenInput` – which has a data type of `String` – and attempt to make it into an `Int`.

However, we still cannot make the comparison on line 20. An error message is shown:

```
Value of optional type 'Int?' must be unwrapped to a value of type 'Int'
```

What does *that* mean?

Although the newly-created constant, `selectedNumber`, was made by attempting to convert `givenInput` into an `Int`, we cannot compare `selectedNumber` to `target`.

Again, why?

Press the **Option** key on your keyboard, then click the `target` constant to confirm that it is an `Int`:

![[Screenshot 2024-01-30 at 7.53.29 PM.png]]

Now press the **Option** key on your keyboard, and click the `selectedNumber` to check it's data type:

![[Screenshot 2024-01-30 at 7.53.55 PM.png]]

Ah-hah – notice how the left side of the comparison – `selectedNumber` – is an *optional* integer – that is, it *might* contain `nil`.

The right side of the comparison – `target` – is a regular integer that is guaranteed to *never* contain `nil`.

Swift, by design, forces us as the programmer to plan for the fact that the conversion of `givenInput` to an `Int` may not succeed:

```swift
// Attempt to convert the String input to an Int
let selectedNumber = Int(givenInput)
```

When the conversion fails – `selectedNumber` will be `nil`.

We need to *unwrap* the result of converting `givenInput` into an integer, so that the resulting constant, `selectedNumber`, is not optional.

One way to do this is to *force-unwrap* the conversion.

Change the code on line 17 from this:

```swift
let selectedNumber = Int(givenInput)
```

... to this instead:

```swift
let selectedNumber = Int(givenInput)!
```

Now, the compiler no longer throws an error:

![[Screenshot 2024-01-30 at 8.05.19 PM.png]]

Try running the program by pressing the **Command-R** keyboard shortcut:

![[Screenshot 2024-01-30 at 8.05.58 PM.png]]

We see that the program ran successfully.

OK, so we're good?

Not so fast... try changing the simulated input on line 11 to `fifty` instead, like this:

![[Screenshot 2024-01-30 at 8.06.43 PM.png]]

Now run the program again by using the **Command-R** shortcut.

What happens?

💥

Our program crashes:

![[Screenshot 2024-01-30 at 8.23.12 PM.png]]

... because as the programmer, we have failed to anticipate that *users make poor decisions sometimes* and will occasionally... or maybe even *frequently*... provide us with unexpected input.

When we tried to convert the text `fifty` into an integer, that understandably failed – so we received a `nil`  – but [[Optionals|as you know]] – force-unwrapping a `nil` value leads to a crash.


So... how do we deal with this?

The Swift programming language has a *control structure* designed to help us in this situation – it is the `guard` statement.

Essentially, we ask the Swift compiler to protect us – or guard us – when the result of an operation could result in a `nil` value.

Change the code on line 17:

```swift
let selectedNumber = Int(givenInput)!
```

... to the following instead:

```swift
guard let selectedNumber = Int(givenInput) else {
    print("Please provide an integer.")
    exit(0)
}
```

... so the program looks like this overall:

![[Screenshot 2024-01-30 at 8.12.35 PM.png]]

Now run the program using the **Command-R** keyboard shortcut.

What do you notice?

The user is still providing (simulated) incorrect input – the text `fifty` instead of an integer.

However, our program no longer crashes.

The user is shown a clear error message – and then the program quits gracefully:

![[Screenshot 2024-01-30 at 8.13.49 PM.png]]

Here is an animation showing the flow of the program when bad input is provided:

![[Guard Statement Example.gif]]

On the other hand, if the conversion of `givenInput` into an integer value succeeds, our program continues on.

Change the simulated input on line 11 from:

```swift
let givenInput = "fifty"
```

... back to:

```swift
let givenInput = "50"
```

... like this:

![[Screenshot 2024-01-30 at 8.28.37 PM.png]]

Now run the program using the **Command-R** keyboard shortcut.

It works as expected, telling us that the simulated input, `50`, is more than the target to guess, `37`, and so we are told to guess lower next time.

Here is an animation of how the program flows through a `guard` statement when reasonable input is provided, and the conversion to an `Int` works:

![[Guard Statement Example – Conversion Works 2.gif]]

## Summary so far

To summarize, we can only compare apples to apples – that is – we can only compare values that have the same data type.

We *could* simply force-unwrap `givenInput` from a `String` into an `Int`, but that will fail when unexpected input is provided:

![[Screenshot 2024-01-30 at 8.18.20 PM.png]]

Instead, we should safely unwrap the `givenInput` into an `Int` using a `guard` statement:

![[Screenshot 2024-01-30 at 8.19.14 PM.png]]

Then, when bad input is provided, we can gracefully stop the conversion, and show an appropriate error message.

> [!IMPORTANT]
> 
> The core purpose of the `guard` statement is provide a graceful early exit from a section of logic that has received bad input.
> 
> When a `guard` statement is in a command-line program we can use the `exit` command to stop program execution.
> 
> When a `guard` statement is inside a function we use the `return` statement to  stop running the function.

## Apply to Guessing Game

Let's take what we have learned here, and apply it to the Guessing Game app, so that it accepts text-based input, but also gracefully handles unexpected input.

You can make these changes regardless of whether you have finished [[Lists and Selection#Complete the game|the first exercise from yesterday's lesson]].

You should have something like this at present:

![[Screenshot 2024-01-30 at 8.37.52 PM.png]]

Start by changing the stored property that holds the user's input from being an integer to being a string, like this – note that *old code is in grey above* and *new code is in blue below*:

![[Screenshot 2024-01-30 at 8.39.12 PM.png]]

Next, we will swap out the `Stepper` for a `TextField` instead.

Replace this code on lines 37 to 43:

```swift
Stepper(value: $selectedNumber, in: 1...100) {
	HStack {
		Text("Make a guess:")
		Spacer()
		Text("\(selectedNumber)")
	}
}
```

... with this code instead:

```swift
TextField("Make a guess", text: $givenInput)
```

You program should now look like this – note the new code on lines 15 and 37:

![[Screenshot 2024-01-30 at 8.41.39 PM.png]]

Essentially, all we have done so far is replace the stepper with a text input field, and changed the stored property that the user's input is placed into.

Before continuing, we need to fix code in the `reset` function.

Scroll down to that function:

![[Screenshot 2024-01-30 at 8.43.39 PM.png]]

... and instead of setting the old stored property that held the user's input back to a starting value of 50, have that line of code reset the given input back to an empty string.

So, replace this code:

```swift
// Start the user back at 50
selectedNumber = 50
```

... with this:

```swift
// Start the user back with an empty string
givenInput = ""
```

... like this:

![[Screenshot 2024-01-30 at 8.46.22 PM.png]]

Alright – so we are now accepting text-based input. Step one is complete.

The second and final step is to convert that text-based input into a number, so that we can do our comparison to guide the user to a correct answer, and tell them when they have won the guessing game.

Scroll up to the `checkGuess` function:

![[Screenshot 2024-01-30 at 8.47.20 PM.png]]

Above the section of code where we attempt to provide feedback to the user, add this code:

```swift
// Attempt to unwrap the input provided by the user
let selectedNumber = Int(givenInput)!
```

... like this:

![[Screenshot 2024-01-30 at 8.49.22 PM.png]]

Of course, this code is not the recommended approach to doing the conversion.

Try out the program – if you type in numbers – everything works.

If you type in something that cannot be converted into an integer:

![[Screenshot 2024-01-30 at 8.50.23 PM.png]]

... and then try to submit your guess, the program will crash:

![[Screenshot 2024-01-30 at 8.50.41 PM.png]]

So, we should unwrap the conversion safely, using a `guard` statement instead.

Change the code on line 91 from this:

```swift
let selectedNumber = Int(givenInput)!
```

... to this instead:

```swift
guard let selectedNumber = Int(givenInput) else {
	feedback = "Please provide an integer."
	return
}
```

... like this:

![[Screenshot 2024-01-30 at 8.52.46 PM.png]]

Now try providing incorrect input, and you will see that appropriate feedback is given:

![[Screenshot 2024-01-30 at 8.53.18 PM.png]]

## Exercise

### Setup

Create a [[iOS Projects|new iOS project]] **Arithmetic Buddy**.

Delete `ContentView`.

Add a new group named `Views`.

Create a new **SwiftUI View** named `AdditionView` inside the `Views` group.

Make the app entry point open `AdditionView`, like this:

![[Screenshot 2024-01-30 at 9.07.37 PM.png]]

Create a remote:

![[Screenshot 2024-01-30 at 9.08.05 PM.png]]

Then please commit and push your work with this message:

```
Created the project and finished initial project organization.
```

Now, [copy and paste this code](https://gist.githubusercontent.com/lcs-rgordon/31a6e332e7fe8a9b91307cd278cefa86/raw/71fb3ecf8b79ca48c4cd8de2b845070eb07f0441/AdditionView.swift) into `AdditionView`, like this:

![[Screenshot 2024-01-30 at 9.34.20 PM.png]]

Press the **Option-Command-P** keyboard shortcut a few times to see what happens.

Note how the two numbers to be added change each time – that is because they are randomly generated.

### Task

Complete this simple addition practice app.

You will need to:

- add a `TextField`, to replace the `HStack` that currently holds the black `Rectangle` placeholder
- add a stored property to bind the `TextField` to, perhaps named `givenInput`
- fill in the logic in the `checkAnswer` function

Be sure that the app does not crash when unexpected input is provided!

When all is said and done, your app might work something like this:

![[RocketSim_Recording_iPhone_15_Pro_6.1_2024-01-31_07.08.05.gif|301]]

