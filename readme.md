# vscode-ibmi-walkthroughs

This extension/repo is specifc to creating walkthroughs for Code for IBM i and IBM i related content.

## Plans:

* [x] Introduction to Code for IBM i (done, but still open to PRs!)
* [ ] Introduction to RPGLE
* [ ] Introduction to CL
* [ ] Writing your first service program
* [ ] Introduction to COBOL

See something you want to add? Make a PR!

## Contributing

This is an open project to make new and existing developers better at IBM i things! We'll take any type of PR, whether it's a spelling fix, or some additional paragraphs, or a whole new guide - we'd love that!

### To get started

1. Check out the `package.json` file, as this is where all the walkthroughs are defined. The example walkthrough I provided should be enough, but also check out:
  * The [`walkthrough` property documentation](https://code.visualstudio.com/api/references/contribution-points#contributes.walkthroughs).
  * The [MSFT example](https://github.com/microsoft/vscode-extension-samples/tree/main/getting-started-sample).
2. Each steps requires a markdown file or an image and each walkthrough has it's own folder in the `content` folder for that content to live in.

**Getting started is simple.**

1. Make a fork on GitHub
2. Open your fork on GitHub
3. Press . (DOT) on your keyboard to open the web editor.
   * From here you can make all the changes you want
   * You can edit and preview your markdown in the web editor (which is just VS Code in the browser) with Command+Shift+V / Control+Shift+V.
   * Testing your walkthrough won't work in the browser though, you will need to clone it on your local machine and start debugging it to try it out!
4. Make your commits and push to your fork
5. Go back to your fork on GitHub and make a PR when you are ready!