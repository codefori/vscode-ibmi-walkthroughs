#

## Fix the error and compile again

Change the `dsply` statement to use the declared variable:

```rpgle
dsply greeting;
```

Save the member, then run `EVFEVENT demo - member` again from its editor.

**Expected result:** the compile succeeds and the diagnostic for `GRETING` disappears after the compiler diagnostics refresh. Check the Action output for the result of this new compile. With this example corrected, the `EVFDEMO` program should now exist in your development library; you do not need to run it for this exercise.

### Why saving is not enough

Editing a source member does not run the IBM i compiler. Diagnostics can continue to describe the previous compile until you compile again.

The setting `code-for-ibmi.clearDiagnosticOnEdit` can remove a diagnostic when its line is edited. That disappearance is not evidence of a successful compile.

The setting `code-for-ibmi.clearErrorsBeforeBuild` defaults to `true` and clears existing ILE diagnostics before new event data is processed. With it disabled, entries for other files can remain. When checking this exercise, focus on this source and the latest Action output rather than expecting every entry in Problems to disappear.

**Checkpoint:** you have completed the cycle of compile, locate, correct, save, and recompile.
