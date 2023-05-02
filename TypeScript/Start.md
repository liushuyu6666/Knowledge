# Create a Typescript project
1. **Install `node.js`**: To create a `TypeScript` project, set up `Node.js` as it includes `TypeScript` as a dependency. The `npm` package manager is automatically installed with `Node.js`. If you prefer to use the `yarn` package manager, you'll need to install it separately.
2. **Install `TypeScript` compiler globally**: 
    use `npm`
    ```shell
    npm install -g typescript
    ```
    or use `yarn`
    ```shell
    yarn global add typescript
    ```
3. **Initialize the project**: 
    use `npm`
    ```shell
    npm init
    ```
    or use `yarn`
    ```shell
    yarn init
    ```
4. **(optional) Create `ts.config` file**
    If the `ts.config` file is not necessary, the step can be skipped.
    ```shell
    tsc --init
    ```
5. **Add Dependency**:
    use `npm`
    ```shell
    npm install typescript -D
    ```
    or use `yarn`
    ```shell
    yarn add typescript -D
    ```
6. **Add `src`**:
Create a `src` directory in the root directory.

# Add test
1. **Install `@types/jest`**:
    use `npm`
    ```shell
    npm install jest @types/jest -D
    ```
    or use `yarn`
    ```shell
    yarn add jest @types/jest -D
    ```
2. **Create `jest.config.js`**:
    ```javascript
    module.exports = {
        preset: 'ts-jest',
        testEnvironment: 'node',
        testMatch: ['<rootDir>/test/**/?(*.)+(spec|test).[jt]s?(x)']
    };
    ```
    This tells `Jest` to use the `ts-jest` preset, which handles TypeScript compilation during testing, and to use the `Node.js` test environment. Besides, it also specifies the location of all test files.
3. **Create test directory**:
    Create a `test` folder under the root directory, as the `testMatch` property specify.
4. **Shortcut in `package.json`**:
    Add the following lines in the `package.json` to use the `yarn test` command.
    ```json
    "scripts": {
        "test": "jest",
        "test updateSnapshot": "jest --updateSnapshot"
    }
    ```