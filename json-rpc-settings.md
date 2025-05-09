﻿## Plugin Settings

You might need to have some settings in your plugins that are easily changeable by users. Inputs for JSON RPC plugin settings are defined in the file called `SettingsTemplate.yaml` in the root of your plugin directory.


### SettingsTemplate.yaml
This is a YAML file that contains the settings page layout for your plugin. It contains an object with a single property called `body`. The `body` property contains an array of objects that define the layout of the settings page. Each object in the `body` array is a section of the settings page. Each section takes up the entire width of the page, which means you can't have one input on the left and one on the right. The layout of each section is always static: input description on the left, input on the right. Every object in the `body` array has the same structure: a `type` property that defines the type of this input (text input, textarea etc.), and an `attributes` property that contains everything else the object needs to render, such as label, description, or default value. The following is a list of the different input types that can be used in the `SettingsTemplate.yaml` file.

---

#### `textBlock`
This is a block of text with no input. Can't be edited by users, used only to display text.
```yaml
type: textBlock
attributes:
  description: This is a block of text. 
```
<settings-component-demo type="textBlock" description="This is a block of text."></settings-component-demo>

| Property name | Property description |
|---------------|----------------------|
| `description` | The text to display. |

#### `input`
This is a simple text input.
```yaml
type: input
attributes:
  name: inputName
  label: This is a text input
  description: Description of the input
  defaultValue: Hello there
```
<settings-component-demo type="input" label="This is a text input" description="Description of the input" value="Hello there"></settings-component-demo>

| Property name  | Property description                                                                                                                                   |
|----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| `name`         | The name of the input. This is the key that you will use to access the value of the input in the settings object.                                      |
| `label`        | The label for the input. If set, it's displayed to the left of the input.                                                                              |
| `description`  | The description for the input. If set, it's displayed to the left of the input, right below the label.                                                 |
| `defaultValue` | The default value for the input. It's the value your plugin will receive in the settings for that input until the user changes that value in settings. |

#### `inputWithFileBtn` and `inputWithFolderBtn`
This is a text input with a "Browse" button for selecting a file or a folder respectively. They look the same, the only difference is that one only allows selecting a file and the other only allows selecting a folder.
```yaml
type: inputWithFileBtn
attributes:
  name: file
  label: This is a text input with a Browse button
  description: Description of the input
  defaultValue: Hello there
```
<settings-component-demo type="inputWithFileBtn" label="This is a text input with a Browse button" description="Description of the input" value="Hello there"></settings-component-demo>

| Property name  | Property description                                                                                                                                   |
|----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| `name`         | The name of the input. This is the key that you will use to access the value of the input in the settings object.                                      |
| `label`        | The label for the input. If set, it's displayed to the left of the input.                                                                              |
| `description`  | The description for the input. If set, it's displayed to the left of the input, right below the label.                                                 |
| `defaultValue` | The default value for the input. It's the value your plugin will receive in the settings for that input until the user changes that value in settings. |

#### `textarea`
This is a multiline text input.

```yaml
type: textarea
attributes:
  name: multilineString
  label: This is a multiline text input
  description: Description of the input
  defaultValue: Hello there
```
<settings-component-demo type="textarea" label="This is a multiline text input" description="Description of the input" value="Hello there"></settings-component-demo>

| Property name  | Property description                                                                                                                                 |
|----------------|------------------------------------------------------------------------------------------------------------------------------------------------------|
| `name`         | The name of the input. This is the key that you will use to access the value of the input in the settings object.                                    |
| `label`        | The label for the input. If set, it's displayed to the left of the input.                                                                            |
| `description`  | The description for the input. If set, it's displayed to the left of the input, right below the label.                                               |
| `defaultValue` | The default value for the input. It the value your plugin will receive in the settings for that input until the user changes that value in settings. |

#### `passwordBox`
This is a password input. The user will see dots instead of the actual characters they type.
```yaml
type: passwordBox
attributes:
  name: password
  label: This is a password input
  description: Description of the input
  defaultValue: secret password
```
<settings-component-demo type="passwordBox" label="This is a password input" description="Description of the input" value="secret password"></settings-component-demo>

| Property name  | Property description                                                                                                                                   |
|----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| `name`         | The name of the input. This is the key that you will use to access the value of the input in the settings object.                                      |
| `label`        | The label for the input. If set, it's displayed to the left of the input.                                                                              |
| `description`  | The description for the input. If set, it's displayed to the left of the input, right below the label.                                                 |
| `defaultValue` | The default value for the input. It's the value your plugin will receive in the settings for that input until the user changes that value in settings. |

#### `dropdown`
This is a dropdown input. The user can select one of the predefined options.
```yaml
type: dropdown
attributes:
  name: dropdownValue
  label: This is a dropdown input
  description: Description of the input
  defaultValue: Option 1
  options:
    - Option 1
    - Option 2
    - Option 3
```
<settings-component-demo type="dropdown" label="This is a dropdown input" description="Description of the input" value="Option 1" options='["Option 1", "Option 2", "Option 3"]'></settings-component-demo>

| Property name  | Property description                                                                                                                                                                                                        |
|----------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `name`         | The name of the input. This is the key that you will use to access the value of the input in the settings object.                                                                                                           |
| `label`        | The label for the input. If set, it's displayed to the left of the input.                                                                                                                                                   |
| `description`  | The description for the input. If set, it's displayed to the left of the input, right below the label.                                                                                                                      |
| `options`      | An array of strings. Each string is an option that the user can select.                                                                                                                                                     |
| `defaultValue` | The default value for the input. It's the value your plugin will receive in the settings for that input until the user changes that value in settings. If set, this must match one of the values in the `options` property. |

#### `checkbox`
This is a simple checkbox.
```yaml
type: checkbox
attributes:
  name: checkboxValue
  label: This is a checkbox
  description: Description of the checkbox
  defaultValue: true
```
<settings-component-demo type="checkbox" label="This is a checkbox" description="Description of the checkbox" value="true"></settings-component-demo>

| Property name  | Property description                                                                                                    |
|----------------|-------------------------------------------------------------------------------------------------------------------------|
| `name`         | The name of the checkbox. This is the key that you will use to access the value of the checkbox in the settings object. |
| `label`        | The label for the checkbox. If set, it's displayed to the left of the checkbox.                                         |
| `description`  | The description for the checkbox. If set, it's displayed to the left of the checkbox, right below the label.            |
| `defaultValue` | The default value for the checkbox. Can be either `true` or `false`.                                                    |


### Example `SettingsTemplate.yaml` file
```yaml
body:
  - type: textBlock
    attributes:
      description: Welcome to the settings page for my plugin. Here you can configure the plugin to your liking.
  - type: input
    attributes:
      name: userName
      label: How should I call you?
      defaultValue: the user
  - type: textarea
    attributes:
      name: prependResult
      label: Text to prepend to result output
      description: >
        This text will be added to the beginning of the result output. For example, if you set this to 
        "The result is: ", and the result is "42", the output will be "The result is: 42". 
  - type: dropdown
    attributes:
      name: programmingLanguage
      label: Programming language to prefer for answers
      defaultValue: TypeScript
      options:
        - JavaScript
        - TypeScript
        - Python
        - "C#"
  - type: checkbox
    attributes:
      name: preferShorterAnswers
      label: Prefer shorter answers
      description: If checked, the plugin will try to give answer much shorter than the usual ones.
      defaultValue: false
```
<settings-component-demo type="textBlock" description="Welcome to the settings page for my plugin. Here you can configure the plugin to your liking."></settings-component-demo>
<settings-component-demo type="input" label="How should I call you?" value="the user"></settings-component-demo>
<settings-component-demo type="textarea" label="Text to prepend to result output" description='This text will be added to the beginning of the result output. For example, if you set this to "The result is: ", and the result is "42", the output will be "The result is: 42".'></settings-component-demo>
<settings-component-demo type="dropdown" label="Programming language to prefer for answers" value="TypeScript" options='["JavaScript", "TypeScript", "Python", "C#"]'></settings-component-demo>
<settings-component-demo type="checkbox" label="Prefer shorter answers" description="If checked, the plugin will try to give answer much shorter than the usual ones."></settings-component-demo>

### JSON Schema
Add the following line at the beginning of your `SettingsTemplate.yaml` file to enable validation and auto-completion in your IDE. Unfortunately, this feature is supported only in JetBrains IDEs (WebStorm, PhpStorm, Rider, etc.) and does not work in Visual Studio or Visual Studio Code. Please note that it must start with `#` as it must be a comment, otherwise Flow Launcher won't be able to parse the file.

```yaml
#$schema: https://www.flowlauncher.com/schemas/settings-template.schema.json
```

### Visual editor for `SettingsTemplate.yaml`
You can use a [visual editor](/json-rpc-visual-settingstemplate-editor.md) for creating the `SettingsTemplate.yaml` file. When you're done editing, click the `Generate SettingsTemplate.yaml` file and copy-paste its contents into your `SettingsTemplate.yaml` file. Optionally, you can also copy the generated typings for your settings object in your preferred programming language.

<script>
const element = document.querySelector('#__settings-script__');
if (!element) {
    const script = document.createElement('script');
    script.id = '__settings-script__';
    script.src = 'https://www.flowlauncher.com/docs/webcomponents/dist/flow-launcher-docs-web-components.js';
    script.type = 'module';
    document.body.appendChild(script);
}
</script>
