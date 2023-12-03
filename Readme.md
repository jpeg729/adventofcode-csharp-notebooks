# My setup for Advent of code problems

## Getting started

1. Add an environment variable called AOC_SESSION_COOKIE containing your adventofcode session cookie.
2. Open this folder with VSCode
3. Install the extension for Polyglot Notebooks https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.dotnet-interactive-vscode
4. Update it to the preview version (necessary in early December in order to use the latest C# features)
5. Open one of the 2023-x.dib files and run it
6. Enjoy

## Working on a problem

First we import the Api library.

```
#!import Api.dib
```

Then we initialise and load the problem. This downloads the problem description and input from adventofcode.com
and stores local copies in the Problems folder.

N.B. If you manually submit a solution you will have to delete the year-day.html file in order to refresh if.
N.B. If you switch your access token for one from another account, you will need to delete the year-day.txt file
in order to download the correct input for the new account.

Note the lack of semi-colon on the last line. This allows a summary to be shown.

```csharp
var problem = new Problem(2022,8);
await problem.Load()
```

Then we display the first part. If the example data and answer are easily identifiable in the text, they are shown separately.

Note the lack of semi-colon on the last line. This allows the content to be displayed.

```csharp
problem.ShowPart1()
```

Then we implement and submit the code for the first part.

The call to VerifyPart1 does the following:

1. If the example data and answer were identified, it tests that your code gives the right answer to the example data. If not it does nothing more.
2. If the html summary mentions any previously submitted answers, it tests your code against the submitted answer.
3. If the html summary does not mention any previously submitted answers, it submits the result of your code, and downloads the summary again.

```csharp
var part1 = (string input) => {
    return -1;
};
await problem.VerifyPart1(part1)
```

Then we can proceed to part 2.

```csharp
problem.ShowPart2()
```

Then 

```csharp
var part2 = (string input) => {
    return -1;
};
await problem.VerifyPart2(part2)
```

## What to do if the example data or answer are not recognised?

If the example data and/or the answer are badly recognised you can override them like so:

```csharp
problem.Part1.ExampleInput = "Something else";
problem.Part1.ExampleAnswer = "Something else";
```

Replace `Part1` with `Part2` if needed.

## Bash commands to create files

```bash
for i in {1..25}; do cp example.dib 2023-$i.dib; done
for i in {1..25}; do sed -i "s/Problem(2022,8)/Problem(2023,$i)/" 2023-$i.dib; done
```