# My setup for Advent of code problems

A simple setup using Polyglot Notebooks in VSCode.

The provided Api can read the problem and the input data from the website, and submit the response. It should be usable by leaderboard chasers. (Please test it well first in order to understand how it works and any shortcomings it may have.)

## Getting started

1. Add an environment variable called AOC_SESSION_COOKIE containing your adventofcode session cookie.
2. Open this folder with VSCode
3. Install the extension for Polyglot Notebooks https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.dotnet-interactive-vscode
4. Update it to the preview version (necessary in early December in order to use the latest C# features)
5. Open one of the 2023-x.dib files and run it
6. Enjoy

## Working on a problem

### First we import the Api library.

```
#!import Api.dib
```

### Then we initialise and load the problem. 

```csharp
var problem = new Problem(2022,8);
await problem.Load();
```

This downloads the problem description and input from adventofcode.com
and stores local copies in the Problems folder.

**N.B.** If you manually submit a solution you will have to delete the file `Problems/{year}-{day}.html` in order to refresh your answers.

**N.B.** If you switch your access token for one from another account, you will need to delete the file `Problems/{year}-{day}.txt` in order to download the correct input for the new account.

If the problem is not yet available, the server is not contacted in order to avoid spamming it. If there are only a few minutes left, the `Load` method will count down and download the files as soon as it is available.

* `problem.Input` gives access to the full input
* `problem.Part1` gives access the first part
* `problem.Part1.ExampleInput` gives access the example input for the first part
* `problem.Part1.ExampleAnswer` gives access the example answer for the first part
* `problem.Part1.Answer` gives access to the previously submitted answer to the first part

### Then we display the first part. 

```csharp
problem.ShowPart1();
```

If the example data and answer are easily identifiable in the text, they are shown separately.

### Then we implement and submit the code for the first part.

```csharp
int Part1(string input) {
    return -1;
};
await problem.VerifyPart1(Part1);
```

The call to VerifyPart1 does the following in order:

1. If the example data and answer were identified, it tests that your code against the example. If it fails, it stops.
2. If the html summary mentions any previously submitted answers, it tests your code against the submitted answer.
3. If the html summary does not mention any previously submitted answers, it submits the result of your code, and downloads the summary again.

**N.B.** Part1 does not have to return an int, anything with a ToString method will work.

### Then we can proceed to part 2.

```csharp
problem.ShowPart2();
```

### And submit 

```csharp
int Part2(string input) {
    return -1;
}
await problem.VerifyPart2(Part2);
```

## FAQ

### What to do if the example data or answer are not recognised?

You can override the example input and answer like so:

```csharp
problem.Part1.ExampleInput = "Something else";
problem.Part1.ExampleAnswer = "Something else";
```

Replace `Part1` with `Part2` if needed.

You can also set the example input or answer to `null` in order to skip the example verification step.

### What if the execution of a cell takes too long?

Sometimes the `Stop Execution` button does not work. In that case use the `Restart` button.

### How can I display debug info?

Use the `display` function provided by the notebook environment. Don't worry if it shows as an error, it generally works at runtime.

For more information, see the docs https://github.com/dotnet/interactive/blob/main/docs/display-output-csharp.md

`display` can display many different data types, such as lists, objects and so on.

```csharp
display(myVar);
```

### How can I avoid displaying too much debug info when running against the full input?

The length of the input should allow you to distinguish which input was provided. 

*Example inputs are generally short, probably less than 200 characters long, and full inputs are generally much longer.*

```csharp
// something like this should display only for the example input
if (input.Length < 200) display(myVar);
```

## Bash commands to create files

```bash
for i in {01..25}; do cp example.dib 2023-$i.dib; done
for i in {01..25}; do sed -i "s/Problem(2022,8)/Problem(2023,$i)/" 2023-$i.dib; done
```