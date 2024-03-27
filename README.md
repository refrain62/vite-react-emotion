# Vite + React + TypeScript (ESLint + Prettier + Husky) + Vercel 開発環境＋emotion
https://chocolat5.com/tips/react-vite-typescript-vercel-boilerplate/
https://chocolat5.com/tips/react-vite-typescript-emotion/

## アプリの作成
```
$ npm create vite@latest vite-react-emotion --template react-ts
```

## いったん実行
```
$ cd vite-react-emotion
$ npm i
$ npm run dev
```

## Pretterのインストール
```
$ npm i -D prettier
```
.prettierrc ファイルを作成します。基本に必要なものを追加しました。
```
{
  "trailingComma": "es5",
  "bracketSpacing": true,
  "bracketSameLine": false,
  "tabWidth": 2,
  "semi": true,
  "singleQuote": false,
  "useTabs": true,
  "printWidth": 80
}
```
.prettierignore ファイルを作成
```
**/.git
**/.svn
**/.hg
**/node_modules
build
dist
public
```

## ESLintの設定
ESLintはプロジェクト作成時にインストールされているので初期化します。 .eslintrc.json ファイルが作成されます。
```
$ npm init @eslint/config
```
必要なプラグイン類をインストールします。
```
$ npm i -D eslint-config-airbnb eslint-config-airbnb-typescript eslint-config-prettier eslint-plugin-prettier eslint-plugin-react
```
デフォルトの記述に必要なものを追加しました。
```
{
  "env": {
    "browser": true,
    "es6": true,
    "node": true
  },
  "extends": [
    "airbnb",
    "plugin:react/recommended",
    "plugin:@typescript-eslint/recommended",
    "airbnb-typescript",
    "plugin:import/typescript",
    "prettier"
  ],
  "overrides": [],
  "parser": "@typescript-eslint/parser",
  "parserOptions": {
    "ecmaVersion": "latest",
    "sourceType": "module",
    "project": "./tsconfig.json",
    "extraFileExtensions": [".md", ".json"]
  },
  "plugins": [
    "react",
    "react-hooks",
    "@typescript-eslint",
    "prettier",
    "import"
  ],
  "rules": {
    "semi": [2, "always"],
    "react-hooks/rules-of-hooks": "error",
    "react-hooks/exhaustive-deps": "warn",
    "react/react-in-jsx-scope": "off",
    "@typescript-eslint/triple-slash-reference": "off",
    "import/extensions": [
      "error",
      "ignorePackages",
      {
        "ts": "never",
        "tsx": "never"
      }
    ]
  },
  "settings": {
    "react": {
      "version": "detect"
    }
  },
  "ignorePatterns": ["vite.config.ts"],
  "root": true
}
```
.eslintignore ファイルを作成します。
```
node_modules
dist
.github
```



# React + TypeScript + Vite

This template provides a minimal setup to get React working in Vite with HMR and some ESLint rules.

Currently, two official plugins are available:

- [@vitejs/plugin-react](https://github.com/vitejs/vite-plugin-react/blob/main/packages/plugin-react/README.md) uses [Babel](https://babeljs.io/) for Fast Refresh
- [@vitejs/plugin-react-swc](https://github.com/vitejs/vite-plugin-react-swc) uses [SWC](https://swc.rs/) for Fast Refresh

## Expanding the ESLint configuration

If you are developing a production application, we recommend updating the configuration to enable type aware lint rules:

- Configure the top-level `parserOptions` property like this:

```js
export default {
  // other rules...
  parserOptions: {
    ecmaVersion: 'latest',
    sourceType: 'module',
    project: ['./tsconfig.json', './tsconfig.node.json'],
    tsconfigRootDir: __dirname,
  },
}
```

- Replace `plugin:@typescript-eslint/recommended` to `plugin:@typescript-eslint/recommended-type-checked` or `plugin:@typescript-eslint/strict-type-checked`
- Optionally add `plugin:@typescript-eslint/stylistic-type-checked`
- Install [eslint-plugin-react](https://github.com/jsx-eslint/eslint-plugin-react) and add `plugin:react/recommended` & `plugin:react/jsx-runtime` to the `extends` list
