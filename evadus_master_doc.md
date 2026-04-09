# ZAP: COMPLETE ENGINEERING & ARCHITECTURE SPECIFICATION
**Version:** 1.5 (Final UI, Logic & Screenshare Master)
**Target:** 2026 Advanced Proctoring Bypasses (Respondus, SEB, Pearson, ProctorU, Bluebook, etc.)

---

## 1. THE LAUNCHER (COMMAND CENTER UI/UX)
The Launcher is a standalone C++ ImGui dashboard designed for zero-latency performance. It mirrors the structural layout of Evadus to ensure 1:1 familiarity for power users but features a polished, enterprise-grade aesthetic.

### 1.1 Visual Identity & The Window
* **The Frame:** A sleek, frameless borderless window. No standard Windows title bars or borders.
* **Base Palette:** Obsidian Black (`#0D0D0D`) backgrounds with Charcoal Grey (`#1A1A1A`) floating panels, and Off-White text (`#EDEDED`).

### 1.2 Top Navigation (The "Chameleon" Tab Layout)
Dead center at the top of the launcher are three wide, high-contrast tabs: `LITE`, `CORE`, and `PLUS`.
* **Dynamic Content Shifting:** Clicking a tab swaps the entire main body settings and shifts the accent color of the application:
* **Colors:** * `LITE` = Electric Cyan (`#00FFFF`)
  * `CORE` = Vivid Purple (`#BF00FF`)
  * `PLUS` = Zap Electric Yellow (`#D4FF00`)

### 1.3 The Command Hub (Top-Right Corner)
* **Status Shield:** A glowing shield icon next to the profile. 
  * `[INACTIVE]` (Grey/Dimmed) by default.
  * `[READY]` (Active Accent Color) when the bypass/wrapper is successfully hooked.
* **Remote Assist Toggle (The Broadcast Icon):** A dedicated icon next to the shield. Clicking this opens the standalone **Remote Screenshare Hub** (See Section 3), allowing users to instantly generate a session ID for a remote helper regardless of which tab they are currently using.
* **The User Profile Icon:** A circular avatar. Clicking it opens the Master Dropdown Menu:
  * **User Identity:** Displays the logged-in Email and a unique alphanumeric Zap ID.
  * **Live Account Stats:** "AI Requests Used: X/5" (Real-time counter) and "Total Active Exam Time."
  * **Active Plan Details:** Displays "Free Trial," "Monthly Subscriber," or "Annual Subscriber."
  * **Cryo-Billing Toggle:** A 1-click button to "Freeze" subscription time during academic breaks.
  * **Global Settings (Opens a Pop-up Modal):**
    * **BYO API Key Manager:** Input fields to override Zap's Master Key. Supports: OpenAI, Anthropic, Gemini, OpenRouter, and Local LM Studio IP/Ports.
    * **Hardware Overrides:** Manual selection for Host Microphone and Host Speaker routing.
    * **App Behaviors:** Toggles for "Launch on Boot," "Minimize to Tray," and "Silent Auto-Updater."
  * **Logout:** Securely terminates the session and wipes temp tokens.

---

## 2. THE 3-TIER BYPASS MODES (TAB-SPECIFIC SETTINGS)

### 2.1 The [LITE] Tab (Browser-Level Stealth)
**Target:** Screen-share proctors (Canvas, Zoom, standard ProctorU).
* **Mechanic:** Injects a hardware-accelerated floating browser using the `WDA_EXCLUDEFROMCAPTURE` API, rendering it physically invisible to any OS-level screen recording or capture.
* **Settings Panel:**
  * **Home URL:** Input field for default start page (e.g., chatgpt.com).
  * **Opacity Slider:** 0% to 100% dynamic transparency.
  * **Window Scale:** Resizing percentage for the overlay.
  * **Stealth Visibility Keybinds:** Custom hotkey to vanish/show the browser instantly.
* **Bug Fixes:** Includes an automated input-buffer wipe to fix the "Sticky Key" bug when tabbing between the exam and the overlay.

### 2.2 The [CORE] Tab (Behavioral & Process Stealth)
**Target:** Behavioral AI monitors and process-list scanners.
* **Mechanic:** Injects stealth logic directly into legitimate Windows processes.
* **Settings Panel:**
  * **Polymorphic Spoofer:** "Generate New Identity" button to rename/hide the Zap process as a random Windows service (e.g., `svchost_update.exe`).
  * **Biometric Typing Engine:** * **Target WPM** slider.
    * **Randomized Delay bounds (ms)** (e.g., 60ms - 150ms).
    * **Human Error %** slider to inject artificial typos and backspace corrections.

### 2.3 The [PLUS] Tab (Bare-Metal Kernel Isolation)
**Target:** Kernel-level lockdown browsers (Respondus, SEB, Pearson OnVUE, Bluebook).
* **Mechanic:** Creates a dual-session bare-metal environment using a custom RDP wrapper.
* **Settings Panel:**
  * **"Setup This PC" Button:** When clicked, it launches the standalone **RDP Wrapper Installer** executable to configure the registry and environment.
  * **Adaptive Resolution:** Toggles for "Host Fullscreen" vs. "Custom X/Y" with free aspect ratio stretching for ultra-wide monitors.
  * **Hardware Passthrough:** Dropdown to route the raw physical IDs of the Host Microphone and Webcam into the VM.
  * **GPU Driver & Gamma Bypass Toggle:** Kernel-level hooks to spoof GPU signatures and defeat advanced color-monitoring detection.
  * **Interception Monitor:** A live, scrolling terminal log of detected proctor executables.
* **Bug Fixes:** Hardcoded override that replaces the VM "Sign Out" button with a "Shutdown" button to prevent session boot loops.

---

## 3. REMOTE SCREENSHARE HUB (STEALTH ASSISTANCE)
Designed to provide a secure, proctor-invisible portal for remote helpers. Accessed globally via the **Broadcast Icon** in the Command Hub.
* **Architecture:** A standalone stealth-wrapped pop-up window built directly into the Zap kernel.
* **UI Elements:**
  * **ID Field:** Displays the user's secure connection ID.
  * **Password Field:** Displays a temporary, session-based passcode.
  * **Connection Toggle:** Large button to initiate/terminate the WebSocket handshake.
* **Bypass:** Operates entirely through Zap's process-ghosting, making it invisible to proctoring software that specifically flags AnyDesk, TeamViewer, or Chrome Remote Desktop.

---

## 4. THE AI ASSISTANT SIDEBAR & UI
The primary ImGui overlay used inside the exam environment.

### 4.1 AI Intelligence & Routing
* **Omni-Model Selector:** Dropdown for Claude 4.6, Grok 4, GPT-5.2, and Deepseek V3.2 R1.
* **OpenRouter Auto-Mode:** Automatic task-based routing (identifies Math vs. Writing).
* **System Prompt Injection:** User-defined master behavior rules (e.g., "Answer-only mode").
* **Auto-Text Appending:** Field to automatically attach a prefix (e.g., "Solve this:") to all captures.
* **Neural Text Sanitization:** Regex filter to strip AI-disclaimers (e.g., "As an AI model...").
* **Textbook/CV Upload:** Button to attach PDFs for the AI to reference during answers.

### 4.2 UI Features & Workflow
* **Drag-and-Drop Capture Cache:** Vertical sidebar history for thumbnails; support for multi-image sending.
* **Discrete Answer Module:** A tiny, transparent, scrollable box showing only final answers for 2-camera exams.
* **Markdown Rendering:** Formatted equations, code blocks, and bold text.
* **Persistent UI Memory:** Remembers X/Y position, scaling, and opacity across sessions.
* **Live Mode:** Real-Time WebSocket streaming for audio/video transcription during job interviews.

---

## 5. STEALTH CONTROLS & HOTKEYS

* **Master Pause / Release (Ctrl+Alt+C):**
  * **Action:** Physically severs all input to the VM for safe Host OS usage.
  * **Visual:** VM window dims 20%, Yellow banner reads: **"ZAP: MOUSE RELEASED"**.
  * **Spatial Persistence:** Cursor teleports instantly back to the exact last VM coordinate.
* **The Panic Switch (Ctrl+Alt+F):** Instantly vanishes all overlays and suspends AI threads.
* **Mouse-Bound Macros:** Bind Pause/Release and Snip tools to Mouse Button 4 and Mouse Button 5.
* **Capture Tools:**
  * **Nav-Bar Rapid Capture:** Title-bar camera icon for 1-click Snip-Paste-Send.
  * **Region Snip & Full Screen Snip:** Standard stealth capture tools.
* **3-Cursor Remote Spoofing:** Generates a smoothed, delayed "fake" mouse path for proctor recording software to hide remote-helper movements.

---

## 6. ERROR HANDLING & SUPPORT MATRIX

| Error State | User-Facing Message | Zap Auto-Resolution Logic |
| :--- | :--- | :--- |
| **Needs Admin** | *"Admin Rights Required."* | UI displays a 1-click "Restart as Admin" button. |
| **Unzip Fail** | *"Corrupted Payload."* | Auto-deletes temp folder and re-downloads the installer. |
| **VM Boot Loop** | *"VM State Corrupted."* | "Nuke & Rebuild VM" button resets session in 10s. |
| **Hardware Lock**| *"Hardware Locked by Host."* | Prompts user to close conflicting apps (Discord/Zoom). |
| **API Failure** | *"API Authentication Failed."* | If BYOK is invalid, auto-reverts to Zap Master Key. |

---

## 7. BUSINESS LOGIC

### 7.1 Monetization (Monthly/Annual Only)
* **Freemium:** 5 free AI requests/day per account.
* **Subscription Tiers:** * **Monthly Plan:** Recurring unlimited access.
  * **Annual Plan:** Discounted yearly unlimited access.
* **Crypto:** Native Monero (XMR) gateway for anonymity.

---
**[END OF MASTER SPECIFICATION V1.5]**