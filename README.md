# WorkItemUpdater
Original source is from BlueBasher's [WorkItem Updater](https://github.com/BlueBasher/WorkItemUpdater) project.


See [overview](src/overview.md) for more details on how to configure a build/release.

## Requirements to Build
* [Node.js](https://nodejs.org)
* Typescript Compiler
    ```
    npm install -g typescript
    ```
* Microsoft's Extension Packaging tool TFX which can be installed using npm
    ```
    npm install -g tfx-cli
    ```
* Microsoft VSS Web Extension SDK package
    ```
    npm install vss-web-extension-sdk --save
    ```

## How to Build
Navigate to opr open a command line window in the `src` folder and run the `tsc` command.

If that compiles, you can then run the following in the command line to build the extension package
```
tfx extension create --manifest-globs vss-extension.json
```

## Updating Azure Package
Make sure that you incremented the version in both the `task.json` and `vss-extension.json` files.

Go to our [publisher](https://marketplace.visualstudio.com/manage/publishers/TempWorksSoftware) and clock the `...` symbol next to the extension. Select Update and then upload the new package. It will spend some time verifying the package and then it may take 5-10 minutes for the new package to be available for use in your pipeline.

If you don't have access to our publisher, talk with Ruggles.

## Important Files
`task.json` is what is used to configure the setup screen in the Build/Release pipeline.

`WorkItemUpdater.js` does all the actual work when the extension runs.