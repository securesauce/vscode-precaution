# Precaution extension for Visual Studio Code

A Visual Studio Code extension with support for the Precaution static analysis tool.

This extension supports all [actively supported versions](https://devguide.python.org/#status-of-python-branches) of the Python language.

For more information on Precaution, see https://precli.readthedocs.io/

## Settings

There are several settings you can configure to customize the behavior of this extension.

| Settings | Default | Description |
| ----------------------- | -------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| precaution.args | `[]` | Arguments passed to Precaution for linting files. Each argument should be provided as a separate string in the array. <br> Examples: <br>- `"precaution.args": ["--config=precli.toml"]` <br> - `"precaution.args": ["--disable=PY001"]` |
| precaution.cwd | `${workspaceFolder}` | Sets the current working directory used to lint files with Precaution. By default, it uses the root directory of the workspace `${workspaceFolder}`. You can set it to `${fileDirname}` to use the parent folder of the file being linted as the working directory for Precaution. |
| precaution.enabled | `true` | Enable/disable linting files with Precaution. This setting can be applied globally or at the workspace level. If disabled, the linting server itself will continue to be active and monitor read and write events, but it won't perform linting or expose code actions. |
| precaution.path | `[]` | "Path or command to be used by the extension to lint files with Precaution. Accepts an array of a single or multiple strings. If passing a command, each argument should be provided as a separate string in the array. If set to `["precli"]`, it will use the version of Precaution available in the `PATH` environment variable. Note: Using this option may slowdown linting. <br>Examples: <br>- `"precaution.path" : ["~/global_env/precli"]` <br>- `"precaution.path" : ["precli"]` <br>- `"precaution.path" : ["${interpreter}", "-m", "precli"]` |
| precaution.interpreter | `[]` | Path to a Python executable or a command that will be used to launch the Precaution server and any subprocess. Accepts an array of a single or multiple strings. When set to `[]`, the extension will use the path to the selected Python interpreter. If passing a command, each argument should be provided as a separate string in the array. |
| precaution.importStrategy   | `useBundled` | Defines which precli binary to be used to lint files. When set to `useBundled`, the extension will use the Precaution binary that is shipped with the extension. When set to `fromEnvironment`, the extension will attempt to use the Precaution binary and all dependencies that are available in the currently selected environment. Note: If the extension can't find a valid precli binary in the selected environment, it will fallback to using the Precaution binary that is shipped with the extension. This setting will be overriden if `Precaution.path` is set. |
| Precaution.showNotification | `off` | Controls when notifications are shown by this extension. Accepted values are `onError`, `onWarning`, `always` and `off`. |

The following variables are supported for substitution in the `precaution.args`, `precaution.cwd`, `precaution.path`, and `precaution.interpreter` settings:

-   `${workspaceFolder}`
-   `${workspaceFolder:FolderName}`
-   `${userHome}`
-   `${env:EnvVarName}`

The `precaution.path` setting also supports the `${interpreter}` variable as one of the entries of the array. This variable is subtituted based on the value of the `precaution.interpreter` setting.

## Commands

| Command                | Description                       |
| ---------------------- | --------------------------------- |
| Precaution: Restart Server | Force re-start the linter server. |

## Logging

From the Command Palette (**View** > **Command Palette ...**), run the **Developer: Set Log Level...** command. Select **Precaution** from the **Extension logs** group. Then select the log level you want to set.

To open the logs, click on the language status icon (`{}`) on the bottom right of the Status bar, next to the Python language mode. Locate the **Precaution** entry and select **Open logs**.

## Troubleshooting

In this section, you will find some common issues you might encounter and how to resolve them. If you are experiencing any issues that are not covered here, please [file an issue](https://github.com/securesauce/vscode-precaution/issues).
