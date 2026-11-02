# JARVIS — Trainable iPhone AI Brain (starter)

A local-first iPhone web app. It uses WebLLM to run `Qwen2.5-0.5B-Instruct-q4f16_1-MLC` in the browser with WebGPU. Memory is stored in IndexedDB on the device. No Gemini/OpenAI key or paid server is required.

## Important requirements

- iPhone with a recent iOS version and Safari/WebGPU support.
- Enough free storage and memory for the model. The first model download is several hundred MB (exact size varies).
- Internet for first app/model load. After model assets are cached, inference is on-device; browser cache eviction and iOS storage policies mean offline persistence is not guaranteed.
- Serve over HTTPS. Opening `index.html` directly from Files is not a supported setup.
- This starter is a web app, not an App Store native app.

## Fastest free install: GitHub Pages

1. On the Windows laptop, unzip this folder.
2. Sign in or create a free account at https://github.com.
3. Create a new **public** repository named `jarvis-brain` (do not add a README).
4. Upload all files from this folder to the repository root: `index.html`, `app.js`, `style.css`, `manifest.json`, `sw.js`, `icon.svg`, `README.md`.
5. In repository **Settings → Pages**, choose **Deploy from a branch**, select `main` and `/ (root)`, then Save.
6. Wait for GitHub Pages to publish. Open the Pages URL on the iPhone in Safari.
7. Tap **Share → Add to Home Screen**. Enable **Open as Web App** if shown, then tap Add.
8. Open JARVIS from the Home Screen. Tap **Load local brain** and wait for the model download to finish.

You can also use any HTTPS static hosting provider. GitHub Pages hosts the app files, not your chats or memory.

## Use and train JARVIS

- **Chat:** Ask questions. The selected local model generates answers on your iPhone.
- **Teach:** Save facts and preferences manually.
- **Conversation learning:** Start a message with `Remember that ...` to save it as a memory.
- **Corrections:** Add a correction in the Teach tab.
- **Import notes:** Import TXT, Markdown or CSV files. The app splits them into searchable memory chunks.
- **Memory:** Review/delete notes and export a JSON backup.

Memory is retrieved by simple keyword matching and added to the local model's prompt. This is retrieval-augmented memory, not automatic neural-network fine-tuning. The model's weights do not change when you teach it.

## Troubleshooting

- **WebGPU/model error:** Update iOS, open the app in Safari, reload, and check WebGPU compatibility. Not all devices/browser contexts expose WebGPU reliably.
- **Not enough memory/storage:** Close other tabs/apps, free storage, reload and try again. A smaller quantized model may be needed.
- **First load takes time:** Model weights are downloaded once and may be hundreds of MB.
- **App not installing:** Use Safari, not an in-app browser. The site must use HTTPS.
- **Memory missing:** Browser website data may have been cleared or evicted. Export a backup regularly.

## Privacy and limits

- Model inference runs locally after model download.
- Memories stay in this browser's IndexedDB; they are not synced to another phone.
- The initial runtime package and model files are fetched from their respective hosting/CDN endpoints. The app does not send chat prompts to a cloud AI API.
- This is an early starter: no unrestricted iPhone control, no background always-listening microphone, no automatic access to messages/contacts, and no native PDF parsing.
