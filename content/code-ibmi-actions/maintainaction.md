#

## Creating or Changing an Action

![](maintainaction1.png)

After opening the Actions panel, you have two options:

* Create a new Action by clicking the 'New Action' item at the top of the list (it is always at the top)
* Click on an existing Action in the list to edit and update it.

Creating or changing, you will see this same view:

![](maintainaction2.png)

In this example, we are editing 'Create Bound RPG Program (CRTBNDRPG)'. We can change any of the properties.

* '**Command to run**' is the command that will be executed. Notice it has portions of text that start with an `&` (ampersand) - such text is a "variable" that will be substituted when the action is run. Commands can have different variables based on what 'Type' (member, streamfile, object) is specified.
  
   [Check out the documentation page](https://halcyon-tech.github.io/vscode-ibmi/#/?id=command-variables-and-fields) for more information on available variables.
* '**Extensions**' defines the list of extensions that can use this Action. For `CRTBNDRPG`, that usually means only `RPGLE` and `RPG`, so we would enter: `RPGLE, RPG`.
* '**Types**' determines which type of object can run this action. For example, if your Action only applies to source members, then choose 'Member' from the dropdown.
* '**Environment**' determine where the command should be run. In this case, `CRTBNDRPG` needs to run in the ILE environment since it's an ILE command. You also have the option to run commands through PASE or QShell.

When complete, **click Save**. If you simply close the tab, nothing will be saved.

## Compile errors

Note that if you're running a command to compile source code and want to errors to show up in the Problems tab, you need to make sure your command has `OPTIONS(*EVENTF)`. All of the default commands have this.
