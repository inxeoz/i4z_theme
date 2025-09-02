

### 1. Project structure


```
mtheme/
 ├── themes/
 │    ├── i4z_dark.json
 │    ├── i4z_light.json
 │    ├── i4z_light_Warm.json   ← your new theme
 │    └── ...
 ├── package.json
 ├── LICENSE.md
 ├── LICENSE.txt
 ├── index.html
 └── ...
```

---

### 2. Add your theme to `package.json`

Open `package.json` and make sure your new `i4z_light_Warm.json` is listed under **contributes.themes**.

Example:

```json
{
  "name": "i4ztheme",
  "displayName": "i4z Theme",
  "description": "A set of custom light/dark themes",
  "version": "0.0.1",
  "publisher": "your-name-or-org",
  "engines": {
    "vscode": "^1.70.0"
  },
  "categories": ["Themes"],
  "contributes": {
    "themes": [
      {
        "label": "i4z Dark",
        "uiTheme": "vs-dark",
        "path": "./themes/i4z_dark.json"
      },
      {
        "label": "i4z Light",
        "uiTheme": "vs",
        "path": "./themes/i4z_light.json"
      },
      {
        "label": "i4z Light Warm",
        "uiTheme": "vs",
        "path": "./themes/i4z_light_Warm.json"
      },
      {
        "label": "JD Dark",
        "uiTheme": "vs-dark",
        "path": "./themes/JD_dark.json"
      },
      {
        "label": "JD Light",
        "uiTheme": "vs",
        "path": "./themes/JD_light.json"
      }
    ]
  }
}
```

---

### 3. Test your theme in VS Code

From the root of the project (`mtheme/`), run:

```bash
code --install-extension i4ztheme-0.0.1.vsix
```

Then in VS Code:

1. Open **Command Palette** (`Ctrl+Shift+P` / `Cmd+Shift+P`)
2. Run **Preferences: Color Theme**
3. Select **i4z Light Warm**

---

### 4. Update & repack the extension

If you edit the JSON files or `package.json`, rebuild the `.vsix` package.

Install the VS Code Extension Manager (if not installed yet):

```bash
npm install -g @vscode/vsce
```

Then run inside `mtheme/`:

```bash
vsce package
```

It will generate a new file like:

```
i4ztheme-0.0.2.vsix
```

You can then install it again with:

```bash
code --install-extension i4ztheme-0.0.2.vsix
```

---

### 5. (Optional) Publish to Marketplace

If you want to share the theme on the **VS Code Marketplace**, you’ll need a publisher account and run:

```bash
vsce publish
```

---

👉 So in short:

* Add your JSON theme file into `themes/`
* Reference it in `package.json`
* Build a new `.vsix` with `vsce package`
* Install/test with `code --install-extension`

