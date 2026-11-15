#

## Follow a diagnostic to the source

Open **View > Problems** in VS Code. Find the compiler diagnostic about the undeclared name `GRETING` in `EVFDEMO.RPGLE`. There may also be other compiler messages; the exact wording and number of diagnostics can vary.

For the example exactly as shown, look for `RNF7030` at line 6, column 7. A compilation-summary error may point to line 1; select the message about `GRETING` to find the statement that needs correcting.

Select the diagnostic to navigate to the `dsply greting;` statement. Read its message and message ID. Code for IBM i uses source locations from the event data to associate each diagnostic with a document and range; VS Code then displays the problem in the editor as well as in the Problems view.

### Find the event data

The target in the compile command was `PGM(MYLIB/EVFDEMO)`. Its event data is in:

```text
Library: MYLIB
File:    EVFEVENT
Member:  EVFDEMO
```

From an IBM i CL command line, list the file's members:

```cl
DSPFD FILE(MYLIB/EVFEVENT) TYPE(*MBRLIST)
```

Then display the example member:

```cl
DSPPFM FILE(MYLIB/EVFEVENT) MBR(EVFDEMO)
```

This is structured compiler output, not an RPG source member to edit. It can contain source-file information as well as diagnostic records. You do not need to decode its record format to use the Problems view.

For this example, the event member name happens to match the source member name. The rule is the **output object name**: compiling the same source as `PGM(MYLIB/OTHERPGM)` would use event member `OTHERPGM`.

**Checkpoint:** a compiler diagnostic takes you to the misspelled identifier, and you can identify the event file and member used by the Action.
