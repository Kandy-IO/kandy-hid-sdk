# Electron Context Isolation

Kandy-hid requires the ability to communicate between the Renderer and Main processes via IPC.
This SDK includes a preload script that exposes the specific, targeted IPC messaging functions necessary for its proper operation.

So, if your app enables context-isolation, all that's required is to `require` this SDK's preload script in your app's preload script.

For example:

If you have enabled context-isolation in your electron app, you will also specify your preload file:

```
// Electron main process

const { BrowserWindow } = require('electron')
const path = require('path')

const window = new BrowserWindow({
  height: ...,
  width: ...,
  ...
  webPreferences: {
    contextIsolation: true,
    preload: path.join(__dirname, './preload.js'),
    ...
  }
})
```

In your preload, simply `require` this SDK's preload script, which resides under `local/`:

```
// preload.js

const { contextBridge, ipcRenderer, ... } = require('electron')
require('@distant/kandy-hid/local/preload')


contextBridge.exposeInMainWorld(...)
```