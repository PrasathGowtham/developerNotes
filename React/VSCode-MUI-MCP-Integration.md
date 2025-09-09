Perfect — let’s get you set up in **VS Code** with **MUI MCP** 🚀

---

## 🔧 Step 1. Install the Required AI Extension

You need an AI assistant in VS Code that supports **MCP**:

* **OpenAI VS Code extension** (from the marketplace)
* Or **Cursor** / **Windsurf** (they’re VS Code forks with MCP built in)

👉 If you’re using plain VS Code, make sure you’ve installed **ChatGPT: Official (OpenAI)** or any MCP-compatible assistant.

---

## 🔧 Step 2. Add MUI MCP to Your Settings

Open your **VS Code `settings.json`** (`Ctrl + Shift + P` → *Preferences: Open Settings (JSON)*).
Add this snippet:

```json
"mcp": {
  "servers": {
    "mui-mcp": {
      "type": "stdio",
      "command": "npx",
      "args": ["-y", "@mui/mcp@latest"]
    }
  }
},
"chat.mcp.enabled": true,
"chat.mcp.discovery.enabled": true
```

### 🔍 Explanation:

* `"mui-mcp"` → the name of the MCP server.
* `"command": "npx"` → runs it via `npx`.
* `"args": ["-y", "@mui/mcp@latest"]` → ensures it always pulls the latest MUI MCP version.
* `"chat.mcp.enabled": true` → turns MCP on.
* `"chat.mcp.discovery.enabled": true` → allows automatic discovery of MCP servers.

---

## 🔧 Step 3. Restart VS Code

After saving your settings:

* Restart VS Code (or Cursor/Windsurf).
* The AI assistant will now **detect the MUI MCP server**.

---

## 🔧 Step 4. Test It

In your AI chat panel, try asking something like:

* **“Show me an example of a responsive MUI AppBar with a Drawer.”**
* **“What props does the MUI Button component support?”**

👉 The AI will now **pull real code + doc links** from the official MUI docs instead of hallucinating.

---

✅ That’s it — you’ve integrated **MUI MCP** into VS Code!

---

Do you want me to also give you a **ready-to-paste full `settings.json` example** (with MUI MCP + Copilot/OpenAI together), so you don’t need to merge configs manually?
