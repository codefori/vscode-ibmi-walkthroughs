#

## Compile with event-file support

In the Code for IBM i **Environment** view, use **Create action** on the Actions node. Create an Action with these values:

- Name: `EVFEVENT demo - member`
- Type: `Member`
- Environment: `ILE`
- Extensions: `RPGLE`
- Command(s) to run: the following single line, with `MYLIB` replaced by your development library.

```cl
CRTBNDRPG PGM(MYLIB/EVFDEMO) SRCFILE(&OPENLIB/&OPENSPF) SRCMBR(&OPENMBR) OPTION(*EVENTF)
```

Save the Action. Select the `EVFDEMO.RPGLE` source editor again and use **Run Action...** from the editor toolbar. Choose `EVFEVENT demo - member`.

The Action substitutes `&OPENLIB`, `&OPENSPF`, and `&OPENMBR` with the open member's library, source file, and member name. The explicit `PGM(MYLIB/EVFDEMO)` makes the output library and object name easy to follow.

### Two things need to happen

The compiler must receive `OPTION(*EVENTF)` to generate event data. For this ordinary ILE Action, Code for IBM i also checks for the literal uppercase text `*EVENTF` in the Action command to trigger remote event-file retrieval.

The parameter is `OPTION`, singular. `DBGVIEW(*SOURCE)` is a separate debugging option; it is not what enables compiler diagnostics.

**Expected result:** the compile fails because of `greting`. In the Action's terminal output, look for `Fetching errors for MYLIB/EVFDEMO.` after the compile output. This means the extension is attempting retrieval; it does not by itself confirm that reading the event data succeeded.

[Actions reference](https://codefori.github.io/docs/environment/actions/)
