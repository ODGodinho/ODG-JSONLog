<h1 align="center">
    <a href="https://github.com/ODGodinho">
        <img
            src="https://raw.githubusercontent.com/ODGodinho/Stanley-TheTemplate/main/public/images/Stanley.jpg"
            alt="Stanley Imagem" width="500"
        />
    </a>
    <br />
    Parse your log in JSON formatter
    <br />
</h1>

<h4 align="center">Using @ODG/Log parser logs message ๐ฆ!</h4>

<p align="center">

[![codecov](https://codecov.io/gh/ODGodinho/ODG-JSONLog/branch/main/graph/badge.svg?token=HNBNLLPZ3J)](https://codecov.io/gh/ODGodinho/ODG-JSONLog)
[![Stargazers](https://img.shields.io/github/stars/ODGodinho/ODG-JSONLog?color=F430A4)](https://github.com/ODGodinho/ODG-JSONLog/stargazers)
[![Made by ODGodinho](https://img.shields.io/badge/made%20by-ODGodinho-%2304A361)](https://www.linkedin.com/in/victor-alves-odgodinho/)
[![Forks](https://img.shields.io/github/forks/ODGodinho/ODG-JSONLog?color=CD4D34)](https://github.com/ODGodinho/ODG-JSONLog/network/members)
![Repository size](https://img.shields.io/github/repo-size/ODGodinho/ODG-JSONLog)
[![GitHub last commit](https://img.shields.io/github/last-commit/ODGodinho/ODG-JSONLog)](https://github.com/ODGodinho/ODG-JSONLog/commits/master)
[![License](https://img.shields.io/badge/license-MIT-brightgreen)](https://opensource.org/licenses/MIT)
[![StyleCI](https://github.styleci.io/repos/589358308/shield?branch=main)](https://github.styleci.io/repos/562306382?branch=main)

</p>

# Table of Contents

- [๐ Benefits](#-benefits)
- [๐ Libraries](#-libraries)
- [๐ Dependencies](#-dependencies)
- [โฉ Get Started](#-get-started)
  - [๐ Use Plugin](#-use-plugin)
  - [๐ฒ Implementation](#-implementation)
    - [๐ SendLog](#-send-log)
  - [๐ป Prepare to develop](#-prepare-to-develop)
  - [๐ Start Project](#-start-project)
  - [๐จ Build and Run](#-build-and-run)
  - [๐งช Teste Code](#-teste-code)

---

## ๐ Benefits

- ๐ Speed start new project or package using typescript
- ๐จ Over 800 rules for pattern, possible errors and errors in Linter
- ๐ Log Pattern default format

## ๐ Libraries

- [Node.js 16](https://nodejs.org/?n=dragonsgamers)
- [Typescript](https://www.typescriptlang.org/?n=dragonsgamers)
- [Eslint](https://eslint.org/?n=dragonsgamers)
- [ODG-Linter-JS](https://github.com/ODGodinho/ODG-Linter-Js?n=dragonsgamers)
- [EditorConfig](https://editorconfig.org/?n=dragonsgamers)
- [ReviewDog](https://github.com/reviewdog/action-eslint)

## ๐ Dependencies

- [Node.js](https://nodejs.org) 16 or later
- [Yarn](https://yarnpkg.com/) Optional/Recommended
- [ODG TsConfig](https://github.com/ODGodinho/tsconfig) Last Version
- [error-stack-parser](https://www.npmjs.com/package/error-stack-parser) Last Version

## โฉ Get Started

---

### ๐ Use Plugin

install this plugin with

```powershell
yarn add @odg/json-log
```

### ๐ฒ Implementation

```typescript
const logger = new ConsoleLogger(); // Or Other Class Logger
const plugin = new JSONLoggerPlugin(
    "appName",
);
logger.use(plugin);

plugin.setIdentifier(randomUUID());
```

#### ๐ Send Log

```typescript
try {
    throw new Exception("Example");
} catch (error) {
    await logger.error(error);
}
```

LOG JSON Return

```jsonc
{
    "type": "error",
    "index": "appName",
    "instance": "ContainerID",
    "identifier": "00000000-0000-0000-0000-00000", // use setIdentifier in plugin to change log group
    "gitRelease": "v1.0.0",
    "gitBranch": "main",
    "exception": {
        "type": "string", // ExceptionClassName
        "message": "string", // Example
        "fileException": "string", // index.js
        "functionName": null, // OPTIONAL:
        "fileLine": "number", // 1
        "fileColumn": "number", // 1
        "stack": "stack",
    },
    "exceptionPreview": null, // OPTIONAL: This is preview second property on new Exceptions("Example", error);
    "request": {
        "url": "string",
        "baseURL": "string",
        "method": "Methods | string",
        "headers": "HttpHeadersInterface",
        "params": "ParametersInterface",
        "data": "RequestData",
        "timeout": "number",
        "responseType": "ResponseType",
        "maxContentLength": "number",
        "validateStatus": "((status: number) => boolean) | null",
        "maxBodyLength": "number",
        "maxRedirects": "number",
        "socketPath": "string | null",
        "proxy": "ProxyConfigInterface | false",
        "response": { // OPTIONAL: This is response from axios
            "data": "any",
            "status": "number",
            "headers": {
                "string": "string"
            },
        }
    },
    "createdAt": "Date",
}
```

### ๐ป Prepare To Develop

Copy `.env.example` to `.env` and add the values according to your needs.

### ๐ Start Project

First install dependencies with the following command

```bash
yarn install
# or
npm install
```

## ๐จ Build and Run

To build the project, you can use the following command

> if you change files, you need to run `yarn build` and `yarn start` again

```bash
yarn build && yarn start
# or
yarn dev
```

## ๐งช Teste Code

To Test execute this command

```bash
yarn test
# or
yarn test:watch
```
