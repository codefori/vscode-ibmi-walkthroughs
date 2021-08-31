#

## RPGLE content assist

Code for IBM i ships with content assist for RPGLE, but it is disabled by default.

Content assist for RPGLE works only for total free-format source code (`**FREE`).

To enable the content assist, [open the VS Code Settings](command:workbench.action.openSettings) and search for 'rpgle content assist'.

![](./rpgContentAssist1.png)

To test it, create a new source member (or streamfile) with the following content:

```rpgle
**FREE

Ctl-Opt DFTACTGRP(*NO);

Dcl-S text char(20);

text = 'Hello world';

// try the content assist here!

return;

Dcl-Proc addWorld;
  Dcl-Pi addWorld Varchar(20);
    base varchar(20) const;
  End-Pi;

  return %trim(base) + ' world!';
End-Proc;
```

Use Control+Space to invoke content assist, and you should see the `addWorld` procedure on the list.

![](./rpgContentAssist2.png)
