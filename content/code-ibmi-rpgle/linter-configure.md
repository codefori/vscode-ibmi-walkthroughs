#

## Rules Location

### Developing in a Library

If you are developing in `LIB/QRPGLESRC/MYSOURCE.RPGLE`, then the linter rules exist in `LIB/VSCODE/RPGLINT.JSON`. Each library has its own rules configuration file, binding it to all sources in that library. 

### Developing in the IFS

When developing in the IFS, linter rules exist in `.vscode/rpglint.json` in the current working directory.

### Developing in the local Workspace.

When developing in the IFS, linter rules exist in `.vscode/rpglint.json` in the Workspace folder root.

## Opening the linter rules

Navigate to source code you'd like to use the linter against and run the 'Open RPGLE lint configuration' command (`vscode-rpgle.openLintConfig`) to open the rules configuration for the project.

![Open Lint Configuration command](./lint-1.png)

Or you can right click on a library filter:

![Open Lint Config with a click](./lint-2.png)

 If a linter rules file  does not exist, you will be asked asked if you want to create one. The created file will provide some default rules, as below.
