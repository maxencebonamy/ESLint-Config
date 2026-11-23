# ESLint Config

A shared ESLint configuration for JavaScript and TypeScript projects.

Published on npm as `@maxencebonamy/eslint-config`. It extends the ESLint and typescript-eslint recommended rule sets and enforces a fixed code style: tabs, double quotes, no semicolons.

## Table of contents

- [ESLint Config](#eslint-config)
	- [Table of contents](#table-of-contents)
	- [How it works](#how-it-works)
	- [Tech stack](#tech-stack)
	- [Repository structure](#repository-structure)
	- [Prerequisites](#prerequisites)
	- [Installation](#installation)
	- [Configuration](#configuration)
		- [ESLint (`.eslintrc.json`)](#eslint-eslintrcjson)
		- [VS Code (`.vscode/settings.json`)](#vs-code-vscodesettingsjson)
	- [Useful scripts](#useful-scripts)
	- [License](#license)

## How it works

1. **Base rules**: the config extends `eslint:recommended`, `plugin:@typescript-eslint/recommended` and `plugin:@typescript-eslint/recommended-requiring-type-checking`.
2. **Parsing**: files are parsed with `@typescript-eslint/parser`, with `parserOptions.project` set to `true` so type-aware rules use the nearest `tsconfig.json`.
3. **Style rules**: formatting is enforced through ESLint rules instead of a separate formatter. Main choices: tab indentation, double quotes, no semicolons, no trailing commas, no end-of-file newline, 150 characters per line.
4. **TypeScript rules**: explicit function return types (expressions allowed), unused variables prefixed with `_` are ignored, `import type` and `export type` are written as separate statements, type assertions use the `as` syntax.
5. **Ignored paths**: `.eslintrc.js`, `dist` and `build`.

## Tech stack

| Layer | Technologies |
| --- | --- |
| Linting | ESLint (`>=8.0.0`) |
| Language support | TypeScript (`>=4.9.0`), `@typescript-eslint/parser` 5, `@typescript-eslint/eslint-plugin` 5 |
| Distribution | npm (`@maxencebonamy/eslint-config`) |

## Repository structure

```
.
├── index.js        ESLint configuration (CommonJS export)
├── package.json    Package metadata and peer dependencies
├── LICENSE         MIT license
└── README.md       This file
```

The whole configuration lives in `index.js`: a single `module.exports` object with the `extends`, `parser`, `parserOptions`, `plugins`, `ignorePatterns` and `rules` fields.

## Prerequisites

- [Node.js](https://nodejs.org/) and npm
- A project using ESLint `>=8.0.0` and TypeScript `>=4.9.0`
- A `tsconfig.json` reachable from the linted files, required by the type-aware rules

## Installation

To use the config in a project:

```bash
npm install -D eslint @maxencebonamy/eslint-config
```

To work on the config itself:

```bash
git clone git@github.com:maxencebonamy/ESLint-Config.git
cd ESLint-Config
npm install
```

## Configuration

### ESLint (`.eslintrc.json`)

```json
{
	"extends": "@maxencebonamy"
}
```

### VS Code (`.vscode/settings.json`)

To apply fixes on save, install the [ESLint extension](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint), then add:

```json
{
	"prettier.enable": false,
	"editor.formatOnSave": false,
	"editor.codeActionsOnSave": {
		"source.fixAll.eslint": true
	}
}
```

## Useful scripts

The package defines no scripts. Add these to the `package.json` of the project that uses the config:

```json
{
	"scripts": {
		"lint": "eslint .",
		"lint:fix": "eslint . --fix"
	}
}
```

| Command | Effect |
| --- | --- |
| `npm run lint` | Report rule violations |
| `npm run lint:fix` | Report violations and apply automatic fixes |

## License

This project is licensed under the [MIT License](LICENSE).
