#

## Compare source-member and IFS builds

In the IFS Browser, create `evfifs.rpgle` in a writable development directory on IBM i, such as a directory under your home directory. Open it through the IFS Browser, paste the example from **Prepare an RPG source member**, and save it with the intentional `greting` misspelling.

Create another Action in the Environment view:

- Name: `EVFEVENT demo - IFS`
- Type: `Streamfile`
- Environment: `ILE`
- Extensions: `RPGLE`
- Command(s) to run: the following single line, replacing `MYLIB`.

```cl
CRTBNDRPG PGM(MYLIB/EVFIFS) SRCSTMF('&FULLPATH') OPTION(*EVENTF) TGTCCSID(*JOB)
```

Save the Action, return to the remote stream-file editor, and run it. `&FULLPATH` expands to that file's IBM i IFS path; keep the surrounding single quotes. `TGTCCSID(*JOB)` follows the Code for IBM i RPG stream-file compile example and is separate from event-file support.

**Expected result:** the compile fails, and selecting the `GRETING` diagnostic opens the corresponding location in the IFS source. Correct it to `greeting`, save, and run the same Action again to confirm the successful compile.

### What changed?

- **Source member:** `SRCFILE` and `SRCMBR` identify the input; this exercise uses event member `MYLIB/EVFEVENT(EVFDEMO)`.
- **Remote IFS file:** `SRCSTMF` identifies the input; this exercise uses event member `MYLIB/EVFEVENT(EVFIFS)`.

An IFS source path does not move this `CRTBNDRPG` event output into an IFS directory. The target program library still determines the event file location.

A file opened from your computer's Explorer workspace is a different case: local development requires deployment to IBM i and mapping diagnostics back to the local source. Continue with the **Local Development with ILE** walkthrough for that workflow.
