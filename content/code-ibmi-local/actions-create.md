#

## Creating an `actions.json` file

The `actions.json` file defines what commands should be used to build your application. It belongs in the `.vscode` folder.

The company_system repository comes with an existing one that uses `gmake` (GNU Make) to build the application, but you could also set up an action to:

* run the `CRTBNDxxx` command
* run `gmake`
* run `makei` (ibmi-bob)

**You do not need a build tool** like ibmi-bob or GNU Make to compile programs.

You also have access to some variables in the command:

* `&CURLIB` and `&BUILDLIB` is the current library as setup in VS Code
* `&RELATIVEPATH` is the path to the source being compiled
* `&BASENAME` for the name and extension of the file
* `&NAME` for just the name, useful for object parameter
* `&USERNAME` for the currently signed in username

For the errors (EVFEVENT) to be returned for the compile on the active source, `*EVENTF` must be in the command string. Notice below that `deployFirst` is set to `true` on all Actions. This is to make sure source code gets uploaded to the Deploy directory before the Action is run.

#### Running an ILE command

```json
  {
    "name": "Compile with CRTBNDRPG 🔨",
    "command": "CRTBNDRPG PGM(&CURLIB/&NAME) SRCSTMF('&RELATIVEPATH') OPTION(*EVENTF) DBGVIEW(*SOURCE) TGTRLS(*CURRENT)",
    "environment": "ile",
    "deployFirst": true,
    "extensions": [
      "RPGLE"
    ]
  }
```

#### Running a pase command (make)

**Note:** this would build the entire project.

```json
  {
    "name": "Build and deploy with make 🔨",
    "command": "/QOpenSys/pkgs/bin/gmake BIN_LIB=&CURLIB OPT=*EVENTF",
    "environment": "pase",
    "deployFirst": true,
    "extensions": [
      "GLOBAL"
    ]
  }
```

#### Running a pase command (ibmi-bob)

**Note:** this would build the entire project. Look into use `makei compile` to build a single source.

```json
  {
    "name": "Deploy & build with bob 🔨",
    "command": "OPT=*EVENTF BUILDLIB=&CURLIB /QOpenSys/pkgs/bin/makei build",
    "extensions": [
      "GLOBAL"
    ],
    "environment": "pase",
    "deployFirst": true
  }
```
