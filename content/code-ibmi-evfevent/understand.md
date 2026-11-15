#

## Understanding compile errors and EVFEVENT

This walkthrough follows one compiler error from an IBM i compile into the VS Code Problems view. You will create an RPG source member, compile it, fix an intentional error, and repeat the exercise with an IFS stream file.

### Before you start

- Connect to an IBM i using Code for IBM i. These steps use the Code for IBM i 3.x Actions interface.
- Use a system with the ILE RPG compiler and support for fully free RPG (`**free`).
- Have a development library where you can create source files and programs, and an IFS directory where you can edit stream files.
- For this first exercise, use a library in the system ASP. IASP setup and build tools are follow-up topics.

### What the names mean

`OPTION(*EVENTF)` asks the RPG compiler to produce event data. For the `CRTBNDRPG` commands in this walkthrough, IBM i stores that data in a member of the `EVFEVENT` file in the **target program library**. The member has the **target program name**. The compiler creates the file if it does not exist.

For example, `PGM(MYLIB/EVFDEMO)` identifies event data in `MYLIB/EVFEVENT(EVFDEMO)`, even when the source is elsewhere.

The workflow is:

1. An Action runs the compile command on IBM i.
2. The compiler writes event data describing source locations and messages.
3. Code for IBM i locates and reads that data.
4. The extension turns it into VS Code diagnostics, shown in Problems and at the corresponding source locations.

Compiler diagnostics describe a compile that has run. The RPGLE language tools can also provide editor feedback and lint results; those have a different source and do not prove that a compile succeeded.

[IBM CRTBNDRPG reference](https://www.ibm.com/docs/en/i/7.5.0?topic=ssw_ibm_i_75%2Fcl%2Fcrtbndrpg.html)
