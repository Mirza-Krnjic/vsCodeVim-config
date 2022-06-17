<h2 align="center"><img src="https://raw.githubusercontent.com/VSCodeVim/Vim/master/images/icon.png" height="128"><br>My config for VSCodeVim</h2>
<p align="center"><strong>Vim emulation for Visual Studio Code</strong></p>


It can be installed via the VS Code [Marketplace](https://marketplace.visualstudio.com/items?itemName=vscodevim.vim).


## 💾 Installation


### Mac

To enable key-repeating, execute the following in your Terminal, log out and back in, and then restart VS Code:

```sh
$ defaults write com.microsoft.VSCode ApplePressAndHoldEnabled -bool false              # For VS Code
$ defaults write com.microsoft.VSCodeInsiders ApplePressAndHoldEnabled -bool false      # For VS Code Insider
$ defaults write com.visualstudio.code.oss ApplePressAndHoldEnabled -bool false         # For VS Codium
$ defaults write com.microsoft.VSCodeExploration ApplePressAndHoldEnabled -bool false   # For VS Codium Exploration users
$ defaults delete -g ApplePressAndHoldEnabled                                           # If necessary, reset global default
```

We also recommend increasing Key Repeat and Delay Until Repeat settings in _System Preferences -> Keyboard_.

### Windows

Like real vim, VSCodeVim will take over your control keys. This behaviour can be adjusted with the [`useCtrlKeys`](#vscodevim-settings) and [`handleKeys`](#vscodevim-settings) settings.

## ⚙️ Settings

The settings documented here are a subset of the supported settings; the full list is described in the `Contributions` tab of VSCodeVim's [extension details page](https://code.visualstudio.com/docs/editor/extension-gallery#_extension-details), which can be found in the [extensions view](https://code.visualstudio.com/docs/editor/extension-gallery) of VS Code.

### Quick Example

Keybinds that I found useful (add this to settings.json):

```json
{
  //vim genral settings
  "vim.useSystemClipboard": true,
  "vim.easymotion": true,

  "vim.leader": "<space>",
  "vim.normalModeKeyBindings": [
    {
      "before": ["č"],
      "after": ["0"]
    },
    //faster movement
    {
      "before": ["J"],
      "after": ["5", "j"]
    },
    {
      "before": ["K"],
      "after": ["5", "k"]
    },
    {
      "before": ["<Leader>", "e"],
      "commands": ["workbench.explorer.fileView.focus"]
    },
    {
      "before": ["<Leader>", "a"],
      "commands": ["editor.action.quickFix"]
    },
    {
      "before": ["<Leader>", "p"],
      "commands": ["workbench.action.navigateBack"]
    },
    {
      "before": ["shift+h"],
      "commands": ["workbench.action.previousEditor"]
    },
    {
      "before": ["shift+l"],
      "commands": ["workbench.action.nextEditor"]
    }
  ],
  "editor.linkedEditing": true,
  "editor.minimap.enabled": false,
  "workbench.editor.enablePreview": false,
  "zenMode.fullScreen": false,
  "editor.autoClosingBrackets": "always"
}
```

Most commonly used keybindings (add this to your keybindings.json):

```json
{
  // Place your key bindings in this file to override the defaultsauto[]
[
  {
    "key": "cmd+j",
    "command": "selectNextSuggestion",
    "when": "suggestWidgetMultipleSuggestions && suggestWidgetVisible && textInputFocus"
  },
  {
    "key": "cmd+k",
    "command": "selectPrevSuggestion",
    "when": "suggestWidgetMultipleSuggestions && suggestWidgetVisible && textInputFocus"
  },
  {
    "key": "cmd+b",
    "command": "macros.showExplorer"
  },
  {
    "key": "cmd+e",
    "command": "workbench.action.toggleSidebarVisibility"
  },
  {
    "key": "alt+f",
    "command": "workbench.action.focusSideBar"
  },
  {
    "key": "cmd+t",
    "command": "workbench.action.terminal.toggleTerminal"
  },
  //cmd + num tab switching
  { "key": "cmd+1", "command": "workbench.action.openEditorAtIndex1" },
  { "key": "cmd+2", "command": "workbench.action.openEditorAtIndex2" },
  { "key": "cmd+3", "command": "workbench.action.openEditorAtIndex3" },
  { "key": "cmd+4", "command": "workbench.action.openEditorAtIndex4" },
  { "key": "cmd+5", "command": "workbench.action.openEditorAtIndex5" },
  { "key": "cmd+6", "command": "workbench.action.openEditorAtIndex6" },
  { "key": "cmd+7", "command": "workbench.action.openEditorAtIndex7" },
  { "key": "cmd+8", "command": "workbench.action.openEditorAtIndex8" },
  {
    "key": "cmd+9",
    "command": "workbench.action.openEditorAtIndex9"
  },
  {
    "key": "cmd+[Quote]",
    "command": "workbench.action.navigateToLastEditLocation"
  },
  {
    "key": "cmd+k cmd+q",
    "command": "-workbench.action.navigateToLastEditLocation"
  },
  {
    "key": "ctrl+n",
    "command": "editor.action.addSelectionToNextFindMatch",
    "when": "editorFocus"
  },
  //sidemenu options
  {
    "key": "a",
    "command": "explorer.newFile",
    "when": "explorerViewletVisible && filesExplorerFocus && !explorerResourceIsRoot && !inputFocus"
  },
  {
    "key": "shift+a",
    "command": "explorer.newFolder",
    "when": "explorerViewletVisible && filesExplorerFocus && !explorerResourceIsRoot && !inputFocus"
  },
  {
    "key": "c",
    "command": "filesExplorer.copy",
    "when": "explorerViewletVisible && filesExplorerFocus && !explorerResourceIsRoot && !inputFocus"
  },
  {
    "key": "x",
    "command": "filesExplorer.cut",
    "when": "explorerViewletVisible && filesExplorerFocus && !explorerResourceIsRoot && !inputFocus"
  },
  {
    "key": "p",
    "command": "filesExplorer.paste",
    "when": "explorerViewletVisible && filesExplorerFocus && !explorerResourceReadonly && !inputFocus"
  },
  {
    "key": "r",
    "command": "renameFile",
    "when": "explorerViewletVisible && filesExplorerFocus && !explorerResourceIsRoot && !explorerResourceReadonly && !inputFocus"
  },
  {
    "key": "f",
    "command": "revealFileInOS",
    "when": "explorerViewletFocus && explorerViewletVisible && !inputFocus"
  }
]
}
```
