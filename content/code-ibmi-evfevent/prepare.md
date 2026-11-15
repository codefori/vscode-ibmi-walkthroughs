#

## Prepare an RPG source member

Throughout this walkthrough, replace `MYLIB` with your own existing development library. Choose unused names for the example source file and programs: `QEVFSRC`, `EVFDEMO`, and `EVFIFS`. If these names are already in use, substitute other names in all subsequent steps.

From an IBM i CL command line, create a source physical file and member:

```cl
CRTSRCPF FILE(MYLIB/QEVFSRC) RCDLEN(112)
ADDPFM FILE(MYLIB/QEVFSRC) MBR(EVFDEMO) SRCTYPE(RPGLE)
```

In the Code for IBM i Object Browser, add or adjust a filter to include `MYLIB` and `QEVFSRC`. Refresh it, expand the source file, and open `EVFDEMO.RPGLE`.

Paste this example and save the member. Put `**free` at the start of the first source line.

```rpgle
**free
ctl-opt dftactgrp(*no);

dcl-s greeting char(20) inz('Hello from EVFEVENT');

dsply greting;
*inlr = *on;
```

The misspelling is intentional: the variable is declared as `greeting`, but the `dsply` statement uses `greting`. Leave it that way for the first compile.

Keep this source member open. The next step creates an Action specifically for this exercise, so you can inspect its compiler options without changing your usual compile Actions.

**Checkpoint:** you have saved the example in `MYLIB/QEVFSRC(EVFDEMO)`, with source type `RPGLE` and the intentional misspelling still present.
