1. Clone the project
2. Make `npm i`
3. Make `ls -l node_modules`. Result (short version): `local-package -> ../local-package`
4. Make `cordova prepare android`.

*Actual*:
1. Output after step 4:

`Discovered plugin "local-package" in config.xml. Adding it to the project
Failed to restore plugin "local-package" from config.xml. You might need to try adding it again. Error: Failed to fetch plugin local-package@./local-package via registry.
Probably this is either a connection problem, or plugin spec is incorrect.
Check your connection and plugin name/version/URL.
Failed to get absolute path to installed module`

2. Output after a command `ls -l node_modules` (short version):
`local-package -> local-package`

3. `package.info` is modified.
before command:
`"local-package": "./local-package"`
After command:
`"local-package": "file:node_modules/local-package"`

*Expected*:
1. Output is empty after step 4.
2. Output after a command `ls -l node_modules` (short version):
`local-package -> ../local-package`
3. `package.info` is not modified.
