# oef README

This is the README for the extension "oef".

OEF stands for Open Exercise Format, a language used by the educational platform WIMS ( https://wims.univ-cotedazur.fr/ )

## Features

This extension provides syntax highlighting for the following extensions:

* `*.phtml`
* `*.var`
* `*.proc`
* `*.input`
* `*.ca`
* `*.cn`
* `*.de`
* `*.en`
* `*.es`
* `*.fr`
* `*.it`
* `*.nl`
* `*.si`
* `*.tw`
* `*.template`
* `*.def`
* `*.local`
* `*.dat`

It is a translation of the .tmLanguage file provided in 

https://sourcesup.renater.fr/scm/viewvc.php/trunk/divers/syntax_highlighting/?root=wimsmodules


## Requirements

For the moment, you have to install it manually.  To do so, just uncompress the file vscode-wims.tgz in your
.vscode/extensions directory, and restart the editor Visual Studio Code.

## Extension Settings

None

## Known Issues

None

## Release Notes

None

### 1.0.0

Initial release

### 1.0.1

Bug fix. Removed the key that highlights operators (+,-,/ etc) since it was preventing the extension to load.
