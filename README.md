# nest + paths + swc + windows bug

> ✅ Fixed in version v10.1.17

Reproduction if an issue with NestJS + paths + SWC + Windows

https://github.com/nestjs/nest-cli/issues/2211

## Steps to reproduce

```
# Install swc
npm i -D @swc/cli @swc/core

# Install dependencies
npm install
```

Build using nest -> tsc

```
nest build

# app.module.js
const app_controller_1 = require("./app.controller");
const app_service_1 = require("./app.service");
```

Build using swc

```
npx swc ./src -d dist

# app.module.js
const _appcontroller = require("./app.controller");
const _appservice = require("./app.service");
```

Build nest -> swc

```
nest build -b swc

# app.module.js
const _appcontroller = require("C:/path/to/nest-swc-paths-issue/src/app.controller");
const _appservice = require("C:/path/to/nest-swc-paths-issue/src/app.service");
```
