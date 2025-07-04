> Preface: This document was translated by AI. If there are any errors or unclear parts, please refer to the Chinese documentation or suggest a more reasonable translation. Thank you!

![QuickLook icon](https://user-images.githubusercontent.com/1687847/29485863-8cd61b7c-84e2-11e7-97d5-eacc2ba10d28.png)

![example](img/example.png)

> Frontend developers with experience are welcome to modify the frontend styles if they feel the current interface is not visually appealing.
> Please note that this plugin may no longer be updated in the future. New features will be developed in [MultiViewer](https://github.com/heicycyu/QuickLook.Plugin.MultiViewer), which will support previewing more formats. The frontend of MultiViewer will uniformly use HTML, and relevant interfaces will be provided subsequently.

# QuickLook.Plugin.SqliteViewer

This plugin allows [QuickLook](https://github.com/QL-Win/QuickLook) to preview sqlite file formats, without the requirement of installing sqlite tools.

## Try out

1. Go to [Release page](https://github.com/QL-Win/QuickLook.Plugin.SqliteViewer/releases) and download the latest version.
2. Make sure that you have QuickLook running in the background. Go to your Download folder, and press <key>Spacebar</key> on the downloaded `.qlplugin` file.
3. Click the “Install” button in the popup window.
4. Restart QuickLook.
5. Select the file and press <key>Spacebar</key>.

## InterfaceDescription
> All interfaces are invoked using `window.external.xxx`. The returned result is a JSON string. Please use `JSON.parse()` in the front-end to parse it.

### `window.external.GetTableNames`
> Get the list of table names
1. Calling method: `window.external.GetTableNames()`
2. Parameters: None
3. Return value: `{status: boolean, data: string[], message: string}`

### `window.external.LoadTableData`
> Load data for a specified table
1. Calling method: `window.external.LoadTableData(input, isTableName)`
2. Parameters:
    - `input`: string, table name or SQL query
    - `isTableName`: bool, indicates whether the input is a table name; should correspond to the input data
3. Return value: `{status: boolean, data: {map[]}, message: string}`

### `window.external.LoadTableDataBySql`
> Load table data by SQL query
1. Invocation: `window.external.LoadTableDataBySql(sql)`
2. Parameters:
   - `sql`: string, the SQL statement
3. Returns: `{status: boolean, data: {map[]}, message: string}`

### `window.external.GetTableRecordCount`
> Get the number of records in a table
1. Invocation: `window.external.GetTableRecordCount(tableName)`
2. Parameters:
   - `tableName`: string, the name of the table
3. Returns: `{status: boolean, data: number, message: string}`

### `window.external.GetTableColumns`
> Get column names of a table
1. Invocation: `window.external.GetTableColumns(tableName)`
2. Parameters:
   - `tableName`: string, the name of the table
3. Returns: `{status: boolean, data: string[], message: string}`


## Configuration Instructions
> Configuration file path: `$QuickLookAppDir\UserData\QuickLook.Plugin\QuickLook.Plugin.SqliteViewer\setting.json`

| Key       | Type   | Description |
|-----------|--------|-------------|
| width     | double | Default window width |
| height    | double | Default window height |
| log_level | int    | Log level, 0-5 correspond to `TRACE`, `DEBUG`, `INFO`, `WARN`, `ERROR`, `FATAL` respectively. Default is 2 |


## Update History
### v0.2
1. The frontend has been refactored using Vue 2.
2. Added settings functionality
3. Configurable default window size (`width`, `height`)
4. Added logging feature; log level can be configured in settings.
   Levels 0-5 correspond to `TRACE`, `DEBUG`, `INFO`, `WARN`, `ERROR`, and `FATAL` respectively
5. Added interfaces:
   - `window.external.LoadTableDataBySql`
   - `window.external.GetTableRecordCount`
   - `window.external.GetTableColumns`

### v0.1
1. Added SQLite preview functionality
2. Used `WebBrowser` to render the front-end
3. Front-end communicates with the back-end via `window.external.xxx`, added interfaces:
   - `window.external.GetTableNames`
   - `window.external.LoadTableData`
   > For detailed usage, see [Interface Description](##InterfaceDescription)


## License

### Source codes in this project

MIT License

Copyright (c) 2018 Paddy Xu

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
