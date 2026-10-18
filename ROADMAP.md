# 🗺️ DuRT Public Product Roadmap

This roadmap provides transparent visibility into what the DuRT team has shipped, what is actively under development, and upcoming initiatives shaped by our community.

To propose or vote on new features, please head to [GitHub Discussions - Ideas & Features](https://github.com/codeAndxv/durt-community/discussions/categories/ideas). Features with the most upvotes receive direct priority in our sprint planning.

---

## 🟢 Shipped (v3.0 Release)

- [x] **Modular Pipeline Architecture**: Decoupled workflow pipeline allowing arbitrary ordering of ASR, glossary refinement, translation, AI synthesis, TTS, and multi-channel delivery.
- [x] **Dual Translation Pathways**: Independent decoupling of real-time simultaneous streaming translation and offline full-document batch translation.
- [x] **Domain Glossary & Terminology Hub**: Native SQLite/GRDB-backed dictionary supporting O(1) set-based deduplication, case-sensitivity normalization, and prompt entity injection.
- [x] **1:1 Dedicated AI Studio Copilot**: Removed multi-session overhead; each transcription task is bound directly to an isolated, persistent AI assistant with 2x2 action tiles.
- [x] **Studio 2D Subtitle Positioning**: Full 2D coordinate canvas dragging for burned-in subtitles with transient drag decoupling and video resolution adaptation.
- [x] **Multi-Channel Cloud Delivery**: Automated push to Obsidian vaults, Local folders, Amazon S3, WebDAV, Notion databases, and Webhook endpoints.
- [x] **12-Language Comprehensive Localization**: Native UI localization for English, Simplified Chinese, Traditional Chinese, Japanese, Korean, German, French, Spanish, Italian, Portuguese, Russian, and Arabic.

---

## 🟡 In Progress (v3.1)

- [ ] **Workflow Bundle Import/Export (.durtworkflow)**: One-click export and import of full workflow configuration recipes to easily share pipelines with team members.
- [ ] **Enhanced Streaming LLM Endpoints**: Support for streaming reasoning tokens (`<think>` blocks) from DeepSeek-R1 and similar reasoning models in Studio.
- [ ] **Batch Media Queue**: Multi-file batch queue processing in the background with progress notification toasts.
- [ ] **Custom Audio Device Routing Profiles**: Quick profile switching between podcast microphones, internal system loops, and meeting headsets.

---

## 🔵 Planned & Under Evaluation (Community Voting)

- [ ] **macOS Shortcuts (快捷指令) Integration**: Run DuRT workflows silently via native macOS Shortcuts actions, Siri, or Raycast script commands.
- [ ] **Audio Denoising & Voice Isolation Pre-filter**: Optional on-device ML voice isolation step before audio enters the transcription engine.
- [ ] **Export to Final Cut Pro / Premiere Pro (FCPXML / EDL)**: Native timeline marker and caption export for professional non-linear video editors.
- [ ] **Speaker Diarization Overhaul**: Improved visual timeline speaker avatars and multi-speaker color-coded subtitle splits.
- [ ] **Local LLM Runner Integration**: Direct native support for Ollama / MLX / llama.cpp on Apple Silicon without manual API endpoint setup.

---

## 🗳️ How We Prioritize

1. **User Upvotes**: Ideas posted in [GitHub Discussions - Ideas](https://github.com/codeAndxv/durt-community/discussions/categories/ideas) that gain community traction are reviewed weekly.
2. **Apple Platform Polish**: We prioritize features that leverage macOS native strengths (Metal, Apple Neural Engine, Swift Concurrency, Sandboxing).
3. **Privacy & Reliability**: Offline capabilities and data sovereignty always take precedence over forced cloud dependencies.
