# My setup for Advent of code problems

## Getting started

1. Add an environment variable called AOC_SESSION_COOKIE containing your adventofcode session cookie.
2. Open this folder with VSCode
3. Install the extension for Polyglot Notebooks https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.dotnet-interactive-vscode
4. Update it to the preview version (necessary in early December in order to use the latest C# features)
5. Open one of the 2023-x.dib files and run it
6. Enjoy

## Working on a problem



## Bash commands to create files

```bash
for i in {1..25}; do cp example.dib 2023-$i.dib; done
for i in {1..25}; do sed -i "s/Problem(2022,8)/Problem(2023,$i)/" 2023-$i.dib; done
```