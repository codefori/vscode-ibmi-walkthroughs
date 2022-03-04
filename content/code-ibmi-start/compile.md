#

## Compiling code

To compile code, or simply run a command, we use an "Action". Actions are defined ways to run a command. For example, there is an Action to run `CRTBNDRPG` for any member that has the `RPGLE` extension in the `ILE` environment.

Note: there is another tutorial on viewing and managing Actions, but for now we can use the built in ones.

To compile, open up a source member (or IFS streamfile) and press:

* Windows: Control + E
* Mac: Command + E

This will show a dropdown of the available Actions for the open source file. Use the arrow keys to select which Action you'd like to run and hit enter to select it.

![](compile.png)

You can also run Actions without opening source members

1. right click on any source member in the object browser
2. select 'Run Action'
3. get the same Action selection appear