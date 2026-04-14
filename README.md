# Gemini Chat Viewer

A lightweight, offline tool for visualising Gemini CLI conversation exports. Paste or drop a `.json` export and get a clean, readable view of your chat — tool calls, model reasoning, and all.

Built by **Mohamed Aly**.

---

## Why

Gemini CLI's `/chat share` command exports conversations as JSON, but the raw format is not easy to read or share with teammates. This tool renders those exports into a structured, human-friendly view with no setup required.

---

## Usage

### 1. Export your conversation from Gemini CLI

```
/chat share my-conversation.json
```

This writes the export to your current working directory.

### 2. Open the viewer

Open `gemini-viewer.html` in any browser — no server, no install, no internet connection required.

### 3. Load your export

Either drag and drop the `.json` file onto the viewer, or paste the JSON directly into the text area.

---

## What it renders

| Part type | How it appears |
|---|---|
| User messages | Blue `user` badge |
| Model responses | Green `model` badge |
| Tool calls (`functionCall`) | Collapsible `call` block with argument preview |
| Tool results (`functionResponse`) | Collapsible `tool results` block |
| Internal thoughts (`thoughtSignature`) | Collapsible `internal thought` block |
| Session / editor context injections | Hidden — these are CLI internals, not part of the conversation |

---

## Privacy

**Your data never leaves your browser.**

The viewer is a single self-contained HTML file. It makes no network requests — parsing and rendering happen entirely in the browser. You can disconnect from the internet before loading a file and everything will work identically.

There is no telemetry, no analytics, no server, and no third-party scripts.

---

## Contributing

The entire tool is a single file: `index.html`. No build step, no dependencies.

To extend it — for example to handle a new part type in a future Gemini CLI release — find the `renderChat` function and add a new branch to the `parts.forEach` loop.

To add a new injected prose pattern that should be hidden from the conversation view, add a regex to the `INJECTED_PROSE_PATTERNS` array near the top of the script.

---

## License

MIT
