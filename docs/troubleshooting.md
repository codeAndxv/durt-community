# 🛠️ DuRT Troubleshooting & Diagnostics Guide

This document covers common configuration, audio permissions, and operational issues encountered on macOS, along with step-by-step solutions.

---

## 📑 Quick Navigation

- [1. Microphone Permission or No Audio Input](#1-microphone-permission-or-no-audio-input)
- [2. System Audio Recording & ScreenCaptureKit Permission](#2-system-audio-recording--screencapturekit-permission)
- [3. Offline Apple Speech Recognition Not Transcribing](#3-offline-apple-speech-recognition-not-transcribing)
- [4. Custom Cloud API Endpoint Connection Errors](#4-custom-cloud-api-endpoint-connection-errors)
- [5. Obsidian or Local Delivery Permission Denied](#5-obsidian-or-local-delivery-permission-denied)
- [6. Diagnostics Checklist for Bug Reports](#6-diagnostics-checklist-for-bug-reports)

---

## 1. Microphone Permission or No Audio Input

### Symptom:
The recording indicator stays at zero, or transcription produces no output when speaking into the microphone.

### Solution:
1. Open **macOS System Settings** ➔ **Privacy & Security** ➔ **Microphone**.
2. Verify that **DuRT** is toggled **ON**.
3. If DuRT does not appear in the list, open Terminal and execute:
   ```bash
   tccutil reset Microphone
   ```
   Then relaunch DuRT and click **Allow** when the permission prompt appears.
4. Check DuRT's internal Audio Input setting (under Settings ➔ Audio) to ensure the intended hardware device (e.g. USB Mic or AirPods) is selected rather than a silent virtual device.

---

## 2. System Audio Recording & ScreenCaptureKit Permission

### Symptom:
When choosing **Monitor / System Audio Capture**, internal video or meeting sound is not recognized, or macOS displays a permission warning.

### Solution:
1. Apple requires **Screen & System Audio Recording** permission for modern zero-latency audio capture via `ScreenCaptureKit`.
2. Open **macOS System Settings** ➔ **Privacy & Security** ➔ **Screen & System Audio Recording**.
3. Ensure **DuRT** is enabled.
4. If toggling was already ON, toggle it **OFF**, wait 2 seconds, and toggle it back **ON**, then restart DuRT.

---

## 3. Offline Apple Speech Recognition Not Transcribing

### Symptom:
Using the native Apple ASR engine fails or hangs on certain languages when offline.

### Solution:
1. macOS on-device speech recognition requires language assets to be downloaded locally.
2. Open **macOS System Settings** ➔ **Keyboard** ➔ **Dictation**.
3. Toggle Dictation **ON** and select the language you wish to transcribe. macOS will download the offline speech recognition package (typically 50MB–200MB).
4. Restart DuRT after the download completes.

---

## 4. Custom Cloud API Endpoint Connection Errors

### Symptom:
AI Content Creation, LLM Chat, or Cloud ASR fails with `Network Error`, `401 Unauthorized`, or `SSL Handshake Failed`.

### Solution:
1. **API Key Verification**: In Settings ➔ Service Providers, ensure your API Key has no accidental leading or trailing whitespaces.
2. **Base URL Format**: When using third-party proxies (e.g. SiliconFlow, DeepSeek, OpenRouter), ensure the URL includes the version path if required (e.g., `https://api.deepseek.com/v1`).
3. **Model Name Matching**: Ensure the model name exactly matches the vendor's API identifier (e.g. `deepseek-chat` or `gpt-4o`).

---

## 5. Obsidian or Local Delivery Permission Denied

### Symptom:
The Export step fails with `Folder access denied` or `Sandbox error`.

### Solution:
macOS sandbox guidelines require explicit user consent to write to folders outside the app container:
1. In the **Export Step** settings, click **Select Folder...** to invoke the native macOS Open Panel.
2. Select your Obsidian vault or target folder. macOS creates a persistent Security-Scoped Bookmark allowing DuRT to write outputs cleanly.

---

## 6. Diagnostics Checklist for Bug Reports

If none of the above resolves your issue, please open a [Bug Report](https://github.com/codeAndxv/durt-community/issues/new?template=01_bug_report.yml) with:
1. **macOS Version** (e.g., macOS 15.1 Sequoia) & Mac Model (e.g., M3 Max).
2. **DuRT Version** (e.g., v3.0.0).
3. **Capture Source** (Mic vs. System Internal Audio).
4. Relevant error message or screenshot.
