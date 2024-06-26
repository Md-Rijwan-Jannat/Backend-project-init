# Backend Setup with Mongoose, TypeScript, Express, CORS, and dotenv

This repository provides a backend setup using modern technologies including Mongoose, TypeScript, Express, CORS, and dotenv. It includes tooling for development and code quality, such as ts-run-dev, ESLint, and Prettier. The recommended software design pattern followed is the Modular pattern.

## Installation and Setup

### Prerequisites

Make sure you have Node.js and Yarn installed on your machine.

### Initial Setup

1. Initialize a new Node.js project:

   ```bash
   npm init
   ```

2. Add TypeScript as a development dependency:

```bash
yarn add -D typescript
```

3. Initialize TypeScript configuration:

```bash
tsc --init --rootDir "./src" --outDir "./dist"
```

4. Install required packages:

```bash
yarn add express mongoose cors dotenv
```

5. Install development tools:

```bash
yarn add -D ts-node-dev eslint prettier
```

6. Project Structure

```bash

project-root
├── src
│ ├── server.ts
│ ├── app.ts
│ └── ...
├── .env
├── .eslintignore
├── .eslintrc.json
├── .gitignore
├── package.json
├── tsconfig.json
└── yarn.lock
Setting up Express Server
Create src/app.ts:
```

- Create app.ts

```bash
*typescript
import express from 'express';
import cors from 'cors';

const app = express();

// Middleware
app.use(cors());
app.use(express.json());

// Routes
app.get('/', (req, res) => {
res.send('Hello World!');
});

export default app;
```

- Create src/server.ts:

```bash
*typescript
import dotenv from 'dotenv';
import mongoose from 'mongoose';
import app from './app';

dotenv.config();

const PORT = process.env.PORT || 3000;
const MONGODB_URI = process.env.MONGODB_URI || 'your-default-mongodb-uri';

const startServer = async () => {
try {
await mongoose.connect(MONGODB_URI, {
useNewUrlParser: true,
useUnifiedTopology: true,
});
console.log('Connected to MongoDB');

    app.listen(PORT, () => {
      console.log(`Server is running on http://localhost:${PORT}`);
    });

} catch (error) {
console.error('Error connecting to the database', error);
process.exit(1);
}
};

startServer();
```

7. Environment Variables
   Create a .env file at the root of the project:

```bash
*makefile
MONGODB_URI=your-mongodb-uri
PORT=3000
Git Ignore
```

8. Create a .gitignore file:

```bash
node_modules
dist
.env
Linting and Formatting
```

9. Install ESLint and Prettier for linting and formatting:

```bash
yarn add -D eslint prettier eslint-config-prettier eslint-plugin-prettier @typescript-eslint/eslint-plugin @typescript-eslint/parser
```

10. Create a .eslintrc.json file:

```bash
*json
{
"parser": "@typescript-eslint/parser",
"extends": [
"eslint:recommended",
"plugin:@typescript-eslint/recommended",
"plugin:prettier/recommended"
],
"parserOptions": {
"ecmaVersion": 2020,
"sourceType": "module"
},
"rules": {
"prettier/prettier": "error"
}
}
```

12. Create a .eslintignore file:

```bash
node_modules
dist
Running the Development Server
```

13. To start the development server, use:

```bash
yarn ts-node-dev src/server.ts
```

14. Recommended Pattern: Modular
    The project follows a modular pattern to enhance maintainability and scalability.

Contributing
Feel free to contribute to this project by submitting a pull request. Ensure that your code adheres to the linting and formatting rules provided.

License
This project is licensed under the MIT License.

```bash
arduino

This README file provides a professional overview of setting up a backend project using M
```
