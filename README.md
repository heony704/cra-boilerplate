# cra-boilerplate

This project is boilerplate containing basic settings that are mainly used when creating a React project.

See below for settings.

- `Create React App`
- Package Manager: `yarn`
- Language: `TypeScript`
- Linter: `eslint-config-airbnb`, `eslint-config-airbnb-typescript`
- Code Formatter: `prettier`
- IDE/Editor: `vscode`

## How to Set

### 1. Create react app.

```bash
yarn create react-app app-name --template typescript
```

### 2. Install `eslint-config-airbnb`.

React App already has ESlint configuration. We can found `eslintConfig` in `package.json`.  
However, To apply stricter rules, Install `eslint-config-airbnb`.

[This is Github of `eslint-config-airbnb`.](https://github.com/airbnb/javascript/tree/master/packages/eslint-config-airbnb)  
[This is ESLint configuration of React App.](https://github.com/facebook/create-react-app/blob/v4.0.3/packages/eslint-config-react-app/index.js)

```bash
npx install-peerdeps --dev eslint-config-airbnb
```

This Command is shortcut available on npm 5+.

### 3. Apply packages related to TypeScript.

`eslint-config-airbnb-typescript` configures TypeScript lint rules.

[This is Github of `eslint-config-airbnb-typescript`.](https://github.com/iamturns/eslint-config-airbnb-typescript)

```bash
yarn add -D eslint-config-airbnb-typescript |
            @typescript-eslint/eslint-plugin@^5.13.0 |
            @typescript-eslint/parser@^5.0.0
```

### 4. Create `.eslintrc` file.

```bash
yarn create @eslint/config
```

Choose the option you want.  
Then `.eslintrc` file will be created.

Modify `.eslintrc` file as below.

```json
    "extends": [
        "eslint:recommended",
        "plugin:react/recommended",
        "plugin:@typescript-eslint/recommended",
        "airbnb", // added !
        "airbnb-typescript" // added !
    ],
    "parserOptions": {
        "ecmaVersion": "latest",
        "sourceType": "module",
        "project": "./tsconfig.json" // added !
    },
```

Add to `extends` to apply the airbnb lint rules.  
If you do not add location of `tsconfig` file, ESLint does not know the TypeScript configuration of this project.

I prefer `json` file.  
But if you choose a different filename extension, write according to that format.

### 5. Apply `prettier`.

```bash
yarn add -D prettier eslint-config-prettier
```

ESLint can also do code formatting.  
`eslint-config-prettier` prevents conflicts between `ESLint` and `prettier`.

And Modify `.eslintrc` file.

```json
    "extends": [
        "eslint:recommended",
        "plugin:react/recommended",
        "plugin:@typescript-eslint/recommended",
        "airbnb",
        "airbnb-typescript",
        "prettier" // added !
    ],
```

Create `.prettierrc` file and Add any prettier rules you want.

As follows. (I used `json` file.)

```json
{
  "singleQuote": true,
  "trailingComma": "all",
  "printWidth": 80,
  "tabWidth": 2,
  "useTabs": false,
  "semi": true,
  "arrowParens": "avoid",
  "bracketSpacing": true,
  "proseWrap": "never",
  "endOfLine": "auto"
}
```

### 6. Add vscode settings file.

Create a `.vscode` folder and Create a `settings.json` file in it.

```
.vscode
 ┗ settings.json
```

Write this in the file.

```json
{
  // Use LF instead of CRLF.
  "files.eol": "\n",

  // Lint, code format every time you save.
  "editor.formatOnSave": true,
  "editor.codeActionsOnSave": {
    "source.fixAll.eslint": true
  },
  "editor.defaultFormatter": "esbenp.prettier-vscode"
}
```

This way you can use the same vscode settings everywhere.

If your project is not only used in vscode, you can force lint and code formatting with `husky`. [Check out the details here.](https://create-react-app.dev/docs/setting-up-your-editor#formatting-code-automatically)

### 7. Lint and code formatting using scripts.

Add the following scripts to `package.json`.

```json
  "scripts": {
    "lint": "eslint ./src/**/*.{ts,tsx,js,jsx}",
    "lint:fix": "eslint --fix ./src/**/*.{ts,tsx,js,jsx}",
    "prettier": "prettier --write ./src/**/*.{ts,tsx}"
  },
```

You can lint or code formatting an entire file using these scripts.

### + additional settings

- Set line ending to `LF`.

  Create `.gitattributes` file like below.

  ```
  * text eol=lf
  ```

## How to use

### 1. Create a new repository on GitHub.

Creating a new repository to apply boilerplate.

### 2. Clone this boilerplate repository.

```bash
git clone https://github.com/heony704/cra-boilerplate.git newProjectName
```

Then a new folder will be created.

### 3. Set new remote url.

Because you cloned, the git remote url is this boilerplate repository url.  
So, replace the git remote url with your new repository url.

```bash
git remote set-url origin newRepositoryUrl
```

### 4. Modify `package.json` and `README.md` to fit your project.

Change the contents of `READEMEname` and `name` value of `package.json`.

### 5. Start the Project.

Install the packages and start the project.

```bash
yarn
yarn start
```
