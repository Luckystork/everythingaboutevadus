# ZAP: COMPLETE ENGINEERING & ARCHITECTURE SPECIFICATION
**Version:** 1.2 (Definitive UI, Screenshare & Monetization Master)
**Target:** 2026 Advanced Proctoring Bypasses (Respondus, SEB, Pearson, ProctorU, Bluebook, etc.)

---

## 1. THE LAUNCHER (COMMAND CENTER UI/UX)
The Launcher is a standalone C++ ImGui dashboard. It perfectly mirrors the structural layout of Evadus to ensure zero learning curve for migrating users, but is built with a high-end, zero-latency aesthetic.

### 1.1 Visual Identity & The Window
* **The Frame:** A sleek, frameless borderless window. No standard Windows title bars. 
* **Base Palette:** Obsidian Black (`#0D0D0D`) backgrounds with Charcoal Grey (`#1A1A1A`) floating panels, and Off-White text (`#EDEDED`).

### 1.2 Top Navigation (The "Chameleon" Tab Layout)
Dead center at the top of the launcher are three wide tabs: `LITE`, `CORE`, and `PLUS`. 
* **Dynamic Content Shifting:** Clicking a tab does two things:
  1. It instantly swaps out the main body of the launcher to display the specific settings for that mode.
  2. It shifts the accent color of the entire application (toggles, active text, glowing icons) to match the threat level.
* **Colors:** `LITE` = Electric Cyan (`#00FFFF`), `CORE` = Vivid Purple (`#BF00FF`), `PLUS` = Zap Electric Yellow (`#D4FF00`).

### 1.3 The Command Hub (Top-Right Corner)
* **Status Shield:** A small shield icon that reads `[INACTIVE]` in grey. When a bypass hooks successfully, it glows in the active tab's accent color and reads `[READY]`.
* **The User Profile Icon:** A circular avatar. Clicking it opens the Master Dropdown Menu.
* **Master Dropdown Menu Contents:**
  * **User Identity:** Displays the logged-in Email and unique Zap ID.
  * **Live Account Stats:** "AI Requests Used: X/5" (for free users) and "Total Active Exam Time."
  * **Active Plan Details:** Displays "Free", "Monthly", or "Annual".
  * **Cryo-Billing Toggle:** A 1-click button to freeze subscription time during academic breaks.
  * **Global Settings (Opens a pop-up Modal):**
    * **BYO API Key Manager:** Input fields to override Zap's Master OpenRouter Key. Supports direct keys for: OpenAI, Anthropic, Gemini, OpenRouter, and Local LM Studio IP/Ports.
    * **Hardware Overrides:** Dropdowns to manually select the default Host Microphone and Host Speaker to be used by the bypass environment.
    * **App Behaviors:** Toggles for "Launch on Boot", "Minimize to Tray", and "Auto-Update Silent Patcher."
  * **Logout:** Securely terminates the session.

---

## 2. THE 3-TIER BYPASS MODES (TAB-SPECIFIC SETTINGS)

### 2.1 The [LITE] Tab (Browser-Level Stealth)
**Target:** Screen-share proctors (Canvas, Zoom, standard ProctorU).
* **Mechanic:** Injects a hardware-accelerated floating browser over the screen using the `WDA_EXCLUDEFROMCAPTURE` Windows API flag, rendering it physically invisible to screen capture.
* **Settings Displayed on this Tab:**
  * **Home URL:** Text box to set the default website (e.g., chatgpt.com).
  * **Opacity Slider:** 0% to 100% dynamic transparency for the floating window.
  * **Window Scale:** Resize the webview dynamically.
  * **Stealth Keybinds:** Custom inputs to instantly hide/show the overlay.
* **Bug Fixes Integrated:** Includes an input-buffer wipe to prevent the infamous "Sticky Key" bug when tabbing between the host exam and the Lite overlay.

### 2.2 The [CORE] Tab (Behavioral & Process Stealth)
**Target:** Behavioral AI monitors and process-list scanners.
* **Mechanic:** Injects stealth AI logic directly into legitimate Windows processes.
* **Settings Displayed on this Tab:**
  * **Polymorphic Spoofer:** A large "Generate New Identity" button that randomly renames the background process (e.g., `WinSysDaemon.exe` or hides it inside `svchost.exe`).
  * **Biometric Typing Engine Config:** * **Target WPM (Words Per Minute)** slider.
    * **Randomized Delay bounds:** Set min/max (e.g., 60ms - 150ms between keystrokes).
    * **Human Error %:** Slider to inject artificial typos and immediate backspace corrections so the AI typing looks human.

### 2.3 The [PLUS] Tab (Bare-Metal Kernel Isolation)
**Target:** Kernel-level lockdown browsers (Respondus, SEB, Pearson OnVUE, Bluebook).
* **Mechanic:** Creates a dual-session environment using a custom RDP wrapper.
* **Settings Displayed on this Tab:**
  * **"Setup This PC" Button:** The primary massive button in the center. Clicking it literally just launches the standalone **RDP Wrapper Installer** executable in the background, configures the registry, and sets up the dual-session environment.
  * **Adaptive Resolution & Stretch Screen:** Toggles for "Host Fullscreen" or custom X/Y resolutions. Includes free aspect ratio stretching for ultra-wide monitors.
  * **Hardware Passthrough:** Dropdown routing the raw physical IDs of the Host Microphone and Webcam directly into the VM to defeat virtual driver bans.
  * **GPU Driver & Gamma Bypass Toggle:** Enables driver-level kernel hooks that spoof GPU signatures to defeat advanced color/gamma-ramp monitoring.
  * **Interception Monitor:** A live, scrolling terminal log scanning for active proctor executables.
* **Bug Fixes Integrated:** Replaces the Windows VM "Sign Out" button with a forced "Shutdown" button to prevent session hanging/boot loops.

---

## 3. THE AI ASSISTANT SIDEBAR & UI
The primary ImGui overlay used during the exam.

### 3.1 AI Intelligence & Routing
* **Omni-Model Selector:** A top-bar dropdown to instantly hot-swap between: Claude 4.6 Opus, Grok 4, GPT-5.2, and Deepseek V3.2 R1.
* **OpenRouter Auto-Mode:** System automatically parses the screenshot (Math vs. Essay) and routes it to the most efficient model.
* **System Prompt Injection:** Define master rules in settings (e.g., "You are an exam solver. Output only the final answer letter. Do not explain.")
* **Auto-Text Appending:** A field to automatically attach text (e.g., "Solve this:") to every screenshot sent.
* **Neural Text Sanitization:** A regex filter that automatically deletes phrases like "As an AI language model..." from the UI before the user sees it.
* **Persona/Textbook Upload:** A button to attach local PDFs/CVs so the AI grounds its answers in specific course material or personal history.

### 3.2 UI Features & Workflow
* **Drag-and-Drop Capture Cache:** A vertical sidebar history of all recent stealth screenshots. Users can drag multiple thumbnails directly into the chatbox at once.
* **Discrete Answer Module (2-Camera Mode):** A toggle that shrinks the UI into a tiny, transparent, scrollable box that *only* displays the final answer for extreme-risk physical exams.
* **1-Click Erase & Copy:** Dedicated buttons on every AI response to copy the text to clipboard or wipe the entire chat history instantly.
* **Markdown Rendering:** Code blocks and complex math equations render perfectly formatted.
* **Persistent UI Memory:** The app remembers the exact X/Y position, size, and opacity of the sidebar between launches.

### 3.3 LIVE MODE (Interview Suite)
* **Real-Time WebSockets:** Opens a persistent connection for remote job interviews.
* **Audio Transcription:** Captures interviewer audio via system sound/mic and transcribes it into text in real-time.
* **Pre-Emptive Generation:** AI begins generating the answer before the interviewer finishes their sentence.

### 3.4 REMOTE SCREENSHARE HUB (Stealth Assistance)
* **Dedicated Screenshare Window:** An independent, stealth-wrapped pop-out window built directly into the Zap architecture, bypassing the need for banned third-party tools (AnyDesk/TeamViewer).
* **Secure Handshake:** Generates a unique, one-time Connection ID and Passcode to give to a remote tutor/helper.
* **Invisible Streaming:** Streams the VM and Overlay visual feed securely via WebSockets directly to the remote helper's browser window.

---

## 4. STEALTH CONTROLS & HOTKEYS

* **Master Pause / Release (Ctrl+Alt+C):** * **Action:** Physically severs all keyboard and mouse inputs to the Virtual Machine, allowing the user to safely click around their Host OS without accidentally clicking inside the exam.
  * **Visual Cue:** The VM window dims by 20%, and an Electric Yellow banner drops from the top of the monitor displaying: **"ZAP: MOUSE RELEASED"**.
  * **Spatial Persistence:** When unpaused, the cursor teleports instantly back to the exact pixel it left inside the VM, preventing "cursor jump" detection.
* **The Panic Switch (Ctrl+Alt+F):** Instantly toggles the RDP environment between windowed/fullscreen, or completely vanishes the Lite overlay and suspends background threads.
* **Mouse-Bound Macros:** Allows binding of the Master Pause and Snip tools to Mouse Button 4 and Mouse Button 5, keeping the user's hands off the keyboard during recorded sessions.
* **Capture Tools:**
  * **Nav-Bar Rapid Capture:** A camera icon integrated into the title bar. One click takes a screen snip, pastes it, and sends it to the AI.
  * **Region Snip & Full Screen:** Standard stealth capture tools triggerable via UI or custom keybinds.
* **Undetectable Screen Recording:** A built-in, kernel-level stealth recorder (OBS alternative) that captures the session for evidence without triggering proctor recording bans.
* **3-Cursor Remote Spoofing:** Tied directly into the Remote Screenshare Hub. Generates a delayed, smoothed "fake" mouse path for the proctor's recording software, hiding the erratic movements of the remote helper taking control over the WebSocket stream.

---

## 5. ERROR HANDLING & USER SUPPORT MATRIX

| Error State / Trigger | User-Facing Message | Automated Zap Resolution |
| :--- | :--- | :--- |
| **Needs Admin Rights** (`Code 740`) | *"Admin Rights Required."* | UI displays a 1-click "Restart as Admin" button. |
| **RDP Wrapper Fails to Unzip** | *"Corrupted Payload."* | Automatically deletes the temp folder and re-downloads the installer. |
| **VM Stuck on 'Preparing Repair'** | *"VM State Corrupted."* | UI provides a "Nuke & Rebuild VM" button that wipes the session and restarts it clean in 10s. |
| **Mic/Camera Not Routing** | *"Hardware Locked by Host."* | Warns user: "Another app (Discord/Zoom) is using your mic. Close it and click Retry." |
| **API Key Rate Limit/Fail** | *"API Authentication Failed."* | If BYOK fails, auto-reverts to Zap's Master Key and alerts user. |
| **Subscription Sync Fails** | *"Token Sync Error."* | Provides a "Force Refresh Account" button to ping the payment gateway. |

---

## 6. BUSINESS LOGIC & MONETIZATION
* **The Freemium Funnel:** All newly registered accounts receive exactly 5 free AI requests per day. Once exhausted, the chatbox locks with an upgrade prompt.
* **Subscription Tiers:**
  * **Monthly Plan:** Standard recurring unlimited access.
  * **Annual Plan:** Discounted yearly unlimited access.
* **Crypto Payments:** Integrated Monero (XMR) gateway for users demanding total financial anonymity.
* **Importable Config Profiles:** Users can save their specific Mode, Resolution, Keybinds, and AI settings as a profile, and share/import them via a dropdown menu.
* **IsDevMode:** Hardcoded developer toggle to bypass all API limits during testing.

---
**[END OF MASTER SPECIFICATION]**