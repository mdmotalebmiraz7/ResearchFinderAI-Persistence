# Persistence update

- Desktop app now reuses a saved localhost port (`server-port.json`) so Chromium localStorage remains on the same origin between launches. This preserves API keys, selected model, language, and other settings after the user saves them.
- The selected Ollama model is already stored by Ollama outside the app installation directory. The desktop backend also keeps its Hugging Face cache under Electron's persistent user-data directory.
- App data/logs/model cache live under Electron's `app.getPath("userData")` data folder; reinstalling the app without deleting user data should preserve them.
- If the saved port is occupied by an unrelated service, the app shows an error rather than silently changing ports and making settings appear lost.

Note: On the first launch of this updated build, settings saved by an older build may need to be entered and saved once because the older build used a different random localhost port. After that, settings persist across launches.
