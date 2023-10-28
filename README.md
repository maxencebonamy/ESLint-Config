<p align="center">
	<img src="https://github.com/maxencebonamy/maxencebonamy/blob/main/assets/ESLint_Config.png" width="100%" alt="Sand Box">
</p>

<br>

<p align="center">
	<img src="https://github.com/maxencebonamy/maxencebonamy/blob/main/assets/1_Description.png" width="100%" alt="Description">
</p>

ESLint is a static code linter for JavaScript, which means it analyzes your JavaScript code for errors, style problems and coding convention violations.
This is my ESLint configuration, which I use for my JavaScript and TypeScript projects.

<br>

<p align="center">
	<img src="https://github.com/maxencebonamy/maxencebonamy/blob/main/assets/2_Get_Started.png" width="100%" alt="Get Started">
</p>

> [!NOTE]
> *Prerequisites:*
> - [x] *NodeJS must be installed on your computer. If not, <a href="https://nodejs.org/" target="_blank">click here.</a>*
<br>

### Install the config:

1. **Install** the dependency:
```
npm install -D eslint @maxencebonamy/eslint-config
```

2. **Paste** the following code into the `.eslintrc.json` file:
```json
{
    "extends": "@maxencebonamy"
}
```

### Enable auto fix with VS Code:

1. **Install** <a href="https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint" target="_blank">ESLint</a> extension.

2. **Paste** the folling code into the `.vscode/settings.json` file:
```
{
    "prettier.enable": false,
    "editor.formatOnSave": false,
    "editor.codeActionsOnSave": {
        "source.fixAll.eslint": true
    }
}
```