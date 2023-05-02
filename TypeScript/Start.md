1. ##Install `node.js`##: To create a `TypeScript` project, set up `Node.js` as it includes `TypeScript` as a dependency. The `npm` package manager is automatically installed with `Node.js`. If you prefer to use the `yarn` package manager, you'll need to install it separately.
2. ##Install `TypeScript` compiler globally##: 
    use `npm`
    ```shell
    npm install -g typescript
    ```
    or use `yarn`
    ```shell
    yarn global add typescript
    ```
3. ##Initialize the project##: 
    use `npm`
    ```shell
    npm init
    ```
    or use `yarn`
    ```shell
    yarn init
    ```
4. ##(optional) Create `ts.config` file##
    If the `ts.config` file is not necessary, the step can be skipped.
    ```shell
    tsc --init
    ```
5. ##Add Dependency##:
    use `npm`
    ```shell
    npm install typescript -D
    ```
    or use `yarn`
    ```shell
    yarn add typescript -D
    ```