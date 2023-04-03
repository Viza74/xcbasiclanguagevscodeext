![xcbasic logo](images/xcbasic_logo.png)

# "xcbasiclanguage" VS Code extension README

Syntax highlighting and snippets for XC-BASIC, a new cross compiling basic dialect for the C64.

## Features

### Grammar definition for syntax highlighting and more

![Syntax highlighting](images/syntaxhighlighting.png)

### Snippets

There are snippets for all the main commands with arguments, all with some handy help text too. Just type away, or use Ctrl+Space to call the helper.

## Requirements

Not really a "requirement", but of course you will need XC-BASIC to compile anything you write... Get it at: https://github.com/neilsf/XC-BASIC

## Extension Settings

This extension contributes the following settings:

* `xcbasic.basefolder`: Absolute path of the XC-BASIC base folder (the one containing the 'bin' and 'third_party' folders).

For now this setting is not used directly by the extension, you can use it with the following `tasks.json` and simply hit Crtl+Shift+B or Cmd+Shift+B to build the currently open XC-BASIC file to a C64 prg with the same name.

```json
{
    // See https://go.microsoft.com/fwlink/?LinkId=733558
    // for the documentation about the tasks.json format
    "version": "2.0.0",
    "tasks": [
        {
            "label": "Build XC_BASIC file to .prg",
            "type": "shell",
            "osx": {
                "command": "./xcbmac",
                "args": [
                    "${file}",
                    "${fileDirname}/${fileBasenameNoExtension}.prg"
                ]
            },
            "linux": {
                "command": "./xcb",
                "args": [
                    "${file}",
                    "${fileDirname}/${fileBasenameNoExtension}.prg"
                ]
            },
            "windows": {
                "command": "xcb.bat",
                "args": [
                    "${file}",
                    "${fileDirname}\\${fileBasenameNoExtension}.prg"
                ]
            },
            "group": {
                "kind": "build",
                "isDefault": true
            },
            "options": {
                "cwd": "${config:xcbasic.basefolder}"
            }
        }
    ]
}
```


## Known Issues

Nothing that I know of, but since this grammar-extension-authoring thing is new for me, there may be some bugs here and there. :) 
If you see something just open an issue on the github repository, and I'll see what can i do about it.

## Release Notes

### 0.0.1

Initial release of `xcbasiclanguage` extension.
