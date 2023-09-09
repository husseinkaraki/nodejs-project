### Tutorial 

Link : https://auth0.com/blog/node-js-and-typescript-tutorial-build-a-crud-api/

express: Fast, unopinionated, minimalist web framework for Node.js.

dotenv: Zero-dependency module that loads environment variables from a .env file into process.env.

cors: Express middleware to enable CORS with various options.

helmet: Express middleware to secure your apps by setting various HTTP headers, which mitigate common attack vectors.

## Notes

### Built in Types
When a package doesn't have built-in types, you can get its type definitions through the @types npm namespace, which hosts TypeScript type definitions from the DefinitelyTyped project. Once you install the packages, the TypeScript compiler automatically includes the types, and your IDE can use them to provide you with code assistance.

### ts-node-dev
 `ts-node-dev` is a tweaked version of node-dev that uses ts-node under the hood, some of its options are the combined options of those two packages. 

## Steps to Bootstrap Nodejs, Expressjs, and Typescript

### Bootstrap application 
```
mkdir menu-api
cd menu-api
```

### Install Project Dependencies
`npm i express dotenv cors helmet`

### Install Typescript
`npm i -D typescript`

### Install Type Definitions for dependencies
`npm i -D @types/node @types/express @types/dotenv @types/cors @types/helmet`

### Initialize Typescript using tsconfig.json file. 
`npx tsc --init`

### Use Environment file
`touch .env`

Populate file with config: `PORT=7000`

### Create an Express app with Typescript
`mkdir src`
`touch src/index.ts`

### Setup index.ts
See `index.ts`

### Hot Reload
`npm i -D ts-node-dev` 

### Run Project
`npm run dev`