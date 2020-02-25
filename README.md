# Multilingual
#### An automatic language loading system

Allows you to define multiple languages without converting and dealing with RAGE formats

## How to use

Included is an **Excel** file (`.xlsx`)

Import that file into an editor, like **Excel** or **Google Spreadsheets**

Once you are done, save the file then import the file into http://beautifytools.com/excel-to-json-converter.php

The output can be put into a **`.json`** file

### Adding to resource

Follow the steps above to create one or more language `.json` files.

Add the following to your resource manifest:
```lua
dependencies {'multilingual'}
function language_file(fn) file(fn) language_json(fn) end
```
Then for each language file, add
```lua
language_file 'filename.json'
```
(replacing `filename` with the filename of course!)

That's it! The resource automatically loads the language files!

## Technicalities

Language name is based on the sheet name, `american` is the default English game language and **must be present**.
Other languages can be ignored.

Language names can be found in the FiveM Native Reference: https://runtime.fivem.net/doc/natives/?_0x2BDD44CC428A7EAE

The game client loads the corresponding language automatically based on client settings.
If the language is not defined, it just uses `american`.

**`A1`** must be `LABEL`
**`B1`** must be `ORIGINAL`
**`C1`** must be `TRANSLATION`

Col **`A`** is reserved for the label entry, like `LANG_SELECT`
Col **`B`** is used for the "original" entry, code ignores it
Col **`C`** is used for the translation, this is what is shown in-game for that label

### Example

#### "american" sheet

|   |      A      |        B        |        C        |
|---|:-----------:|:---------------:|:---------------:|
| 1 | LABEL       | ORIGINAL        | TRANSLATION     |
| 2 | LANG_SELECT | Select Language | Select Language |
| 3 | LANG_APPLY  | Apply           | Apply           |

#### "spanish" sheet

|   |      A      |        B        |           C          |
|---|:-----------:|:---------------:|:--------------------:|
| 1 | LABEL       | ORIGINAL        | TRANSLATION          |
| 2 | LANG_SELECT | Select Language | Seleccione el idioma |
| 3 | LANG_APPLY  | Apply           | Aplicar              |
