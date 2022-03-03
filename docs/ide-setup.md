# IDE Setup

## [VSCode](https://code.visualstudio.com/)

VSCode is one of the most popular IDEs for web development. Out of the box, Code is rather lightweight compared to other IDEs, however, through the vast library of extensions available, Code can be transformed to be much more powerful.

To install Code, visit the link above (in title or [here](https://code.visualstudio.com/)), download the most recent version for your machine, and install it as any other program. For more detailed setup instructions, follow [this link](https://code.visualstudio.com/docs/setup/windows).

VSCode itself really only needs a small amount of setup. The rest is configured through extensions.

- Tab Size, recommend 4 for readability. If monitor space is limited, 2 is fine. Should be consistent throughout team.
- Install Code CLI tool. This allows you to use the `code` in the command line to open files/folders and do some other functions. This comes packaged with Code on windows builds I believe, if not, it can be installed by going to the command palette `ctrl+shift+p` and looking for **Shell Command: Install 'code' command in PATH**
- Connect GitHub account. This can be done by clicking the account icon in the bottom left of the editor, above the manage icon.

## Essential Extensions

### [ESLint](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint)

For linting of JavaScript and TypeScript projects. Provides in editor indicators of linting problems.

### [GitLens](https://marketplace.visualstudio.com/items?itemName=eamodio.gitlens)

Aids the VSCode Git GUI. Adds support for viewing branches, repos, commits etc etc.

### [Prettier](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode)

Formatter. Can be configured with config files to ensure everyone is using the same settings

### Language Extensions

To enable support for most languages you need to download the extension for the specific language. Note that JS and TS are built into VSCode

## Other Extensions

- Auto Close Tag + Auto Rename Tag
  does exactly what it says, useful for HTML or JSX in the case of React
- Bracket Pair Colorizor
  Overrides coloring to match open and closing brackets color. Helps to match start and end of code chunks.
- ES7 React/Redux/GraphQL/React-Native snippets
  Snippets of code that can be used by typing acronyms. Helps speed up development if memorized. I only use a few of them but nice to have now and again.
- Azure Extensions
  Can be useful if you are connecting to Azure DB or and Azure resource. Not too helpful for Auth flows. Lots of different extensions available though.
