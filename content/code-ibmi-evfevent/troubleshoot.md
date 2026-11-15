#

## Troubleshoot missing diagnostics

If a compile fails but Problems is empty, work through these checks in order. An empty Problems view is not proof that the program compiled successfully.

### 1. Did the compiler run?

Read the Action's terminal output first. An invalid command parameter, unavailable compiler, missing source, or authority error can prevent compilation from reaching the stage that produces useful event data. Resolve that failure before investigating diagnostic display.

Confirm you saved the source and ran the intended Action from the intended member or stream-file editor.

### 2. Was event-file retrieval requested?

For these ILE Actions, keep `OPTION(*EVENTF)` in the saved command, including the uppercase `*EVENTF`. Look for these messages in the Action output:

```text
Fetching errors for MYLIB/EVFDEMO.
```

This identifies the retrieval target. If instead you see:

```text
*EVENTF not found in command string. Not fetching errors for MYLIB/EVFDEMO.
```

check the saved Action command. Compiler defaults or options hidden inside a wrapper do not put `*EVENTF` into that Action's command text.

Code for IBM i only writes that second message when the saved command starts with `CRT`. If the Action calls a wrapper command or program and its command text does not contain `*EVENTF`, neither message appears and no retrieval is attempted.

### 3. Are you checking the correct event member?

For `PGM(MYLIB/EVFDEMO)`, check `MYLIB/EVFEVENT(EVFDEMO)`, not a file in the source library merely because the source lives there. Use `DSPFD ... TYPE(*MBRLIST)` and `DSPPFM` as shown in **Follow a diagnostic to the source**. Check the member details and latest compile output together; an existing event member may be left from an earlier compile.

Use explicit target libraries while troubleshooting. Confirm the connected user can access the target library, file, and member. If another job builds the same target concurrently, repeat the exercise with a separate target name.

### 4. Are the diagnostics hidden or attached to another source?

Clear text and severity filters in Problems and check whether it is restricted to the active file. Review **Errors to ignore** in the connection settings: configured message IDs are filtered out of compiler diagnostics.

If a diagnostic opens a different source, compare its location with the expanded `SRCFILE`/`SRCMBR` or `SRCSTMF` in the Action output. For local workspace builds, also check that the latest source was deployed and that the deployment path matches the source used by the compiler.

### Further reading

The [Actions reference](https://codefori.github.io/docs/environment/actions/#evfevent--problems-view) describes target discovery through job-log `EVFEVENT:` messages and compile-command parameters. Custom wrappers, IASP configuration, and TOBi builds need additional setup beyond this exercise. Build tools can also supply downloaded `.evfevent` files for local projects; that is a separate retrieval path from the remote members used here.

If you still need help, include the Code for IBM i version, source type, expanded compile command, Action output, and expected event library/member. Remove credentials and private source details before sharing them.
