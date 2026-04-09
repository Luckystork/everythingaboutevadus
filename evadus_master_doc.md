# ZAP: COMPLETE ENGINEERING & ARCHITECTURE SPECIFICATION
**Version:** 1.18 (The Absolute Final Uncompressed Blueprint)
**Target:** 2026 Advanced Proctoring Bypasses (Respondus, SEB, Pearson, ProctorU, Canvas, Bluebook, Turnitin, Mercer Mettl, PSI Secure, TAO by OAT, EC-Council/LogMeIn Resolve, Iris Invigilation)

---

## 1. THE LAUNCHER (COMMAND CENTER UI/UX)
The Launcher is a standalone C++ ImGui dashboard designed for zero-latency performance. It mirrors the structural layout of Evadus to ensure 1:1 familiarity for power users but features a polished, enterprise-grade aesthetic.

### 1.1 First-Execution Stealth (Polymorphic Launch)
* **Runtime Mutator:** Before the UI ever renders, the `Zap.exe` executes a Runtime Mutator. It recompiles its own memory footprint and changes its process name in Task Manager to a randomly generated whitelisted Windows service (e.g., `spoolsv_update.exe` or `svchost_sys.exe`).
* **Auto-Cleanup:** Upon successful launch, Zap automatically deletes its own installation `.zip` file and desktop shortcut to clear forensic footprints from the hard drive.
* **Deep Registry Purge:** Upon closing or exiting the application, Zap scrubs all of its temporary execution traces from the `HKEY_CURRENT_USER` and `HKEY_LOCAL_MACHINE` registry paths to defeat deep forensic IT scans.

### 1.2 Visual Identity & The Window
* **The Frame:** A sleek, frameless borderless window. No standard Windows title bars or borders. It is draggable by clicking anywhere on the background.
* **Base Palette:** Obsidian Black (`#0D0D0D`) backgrounds with Charcoal Grey (`#1A1A1A`) floating panels, and Off-White text (`#EDEDED`).
* **Light Theme Toggle:** An optional "Light Mode" (White background, Dark Grey text) available in settings for users who specifically requested it for brightly lit rooms.

### 1.3 Top Navigation (The "Chameleon" Tab System)
Dead center at the top of the launcher are three wide, high-contrast tabs: `LITE`, `CORE`, and `PLUS`.
* **Universal Free Access:** The core stealth mechanics and bypasses of all three tabs are universally free and accessible to all users. They are never locked behind a paywall.
* **Dynamic Content Shifting:** Clicking a tab swaps the entire main body settings and shifts the accent color of the application:
  * `LITE` = Electric Cyan (`#00FFFF`)
  * `CORE` = Vivid Purple (`#BF00FF`)
  * `PLUS` = Zap Electric Yellow (`#D4FF00`)

### 1.4 The Command Hub (Top-Right Corner)
* **Status Shield:** A glowing shield icon next to the profile. 
  * `[INACTIVE]` (Grey/Dimmed) by default.
  * `[READY]` (Active Accent Color) when the bypass/wrapper is successfully hooked.
* **Remote Assist Toggle (The Broadcast Icon):** A dedicated icon next to the shield. Clicking this opens the standalone **Remote Screenshare Hub** (See Section 3), allowing users to instantly generate a session ID for a remote helper regardless of which tab they are currently using.
* **The User Profile Icon:** A circular avatar. Clicking it opens the Master Dropdown Menu:
  * **User Identity:** Displays the logged-in Email and a unique alphanumeric Zap ID.
  * **Live Account Stats:** "AI Requests Used: X/5" (or "Unlimited") and "Total Active Exam Time."
  * **Active Plan Details:** Displays "Basic Plan," "Premium Plan," or "Unlimited Plan."
  * **Cryo-Billing Toggle:** A 1-click button to "Freeze" subscription time during academic breaks.
  * **Profile Import/Export:** Allows users to save their current custom hotkeys, AI contexts, and hardware overrides as a `.zap` configuration file, and load different profiles instantly for different types of exams.
  * **Global Settings (Opens a Pop-up Modal):**
    * **BYO API Key Manager:** Input fields to locally override Zap's Master Key. Supports: OpenRouter, OpenAI, Anthropic, Gemini, and Local LM Studio IP/Ports.
    * **API Server Location Routing:** A dropdown to manually force OpenRouter/API traffic through specific regional datacenters (e.g., US-East, EU-Paris, Asia-Tokyo) to minimize latency based on the user's physical location.
    * **Custom Proxy / SOCKS5 Routing:** Input fields for users taking exams on strict campus Wi-Fi networks (e.g., Fortinet) to route Zap's API traffic through a secure proxy, bypassing firewall blocks.
    * **Hardware Overrides:** Manual selection for Host Microphone and Host Speaker routing.
    * **App Behaviors:** Toggles for "Launch on Boot," "Minimize to Tray," and "Silent Auto-Updater."
    * **Volatile RAM Vault Toggle:** Forces all screenshots, textbook PDFs, API keys, and Stealth DVR recordings to be stored in an encrypted temporary folder that exists *only* in RAM. Vaporizes instantly upon app close, leaving zero trace on the disk.
    * **Multi-Monitor Ghosting:** Fakes a single-display EDID profile to the OS, allowing a physical second monitor to remain active while proctors see only one screen.
  * **Logout:** Securely terminates the session and wipes temp tokens.

### 1.5 System & Device Requirements
To ensure users know Zap is highly optimized and accessible, the following minimum requirements are officially supported:
* **OS:** Windows 10 or Windows 11 (64-bit) (Home or Pro Edition).
  * **Tiny10 / Tiny11 Support:** Zap natively packs the required legacy `.dll` dependencies to run flawlessly on stripped-down, custom Windows ISOs to save RAM.
  * *(Note: Native Mac compatibility is not supported directly, but works flawlessly via Parallels Windows 11 ARM VM).*
* **Processor:** Intel Core i3 / AMD Ryzen 3 or higher (Basic multi-core processor).
* **RAM:** 8GB minimum (16GB recommended for smooth PLUS bare-metal allocation).
* **GPU:** Integrated graphics (iGPU) are fully supported. No dedicated graphics card required.
* **Storage:** Less than 500MB of available disk space.

---

## 2. THE 3-TIER BYPASS MODES (UNIVERSALLY FREE)

### 2.1 The [LITE] Tab (Browser-Level Stealth)
**Target:** Screen-share proctors (Canvas, Zoom, standard ProctorU, Iris Invigilation).
* **Mechanic:** Injects a hardware-accelerated floating browser using the `WDA_EXCLUDEFROMCAPTURE` API, rendering it physically invisible to any OS-level screen recording or capture.
* **Settings Panel:**
  * **Home URL:** Input field for default start page (e.g., chatgpt.com).
  * **Opacity Slider:** 0% to 100% dynamic transparency.
  * **Window Scale:** Resizing percentage for the overlay.
  * **Stealth Visibility Keybinds:** Custom hotkey to vanish/show the browser instantly.
* **Canvas DOM Vulnerability Fix:** Injects a lightweight JS payload into the exam browser that freezes `window.onblur` and `document.visibilityState`. Forces the exam to always think it is the active window, bypassing tab-tracking.
* **Global Drag-and-Drop:** Captures physical file drags (PDFs, images) from the host OS and routes them directly into the invisible browser instance.
* **Bug Fixes:** Includes an automated input-buffer wipe to fix the "Sticky Key" bug when tabbing between the exam and the overlay.

### 2.2 The [CORE] Tab (Behavioral & Process Stealth)
**Target:** Behavioral AI monitors and process-list scanners (TAO by OAT).
* **Mechanic:** Injects stealth logic directly into legitimate Windows processes.
* **Settings Panel:**
  * **Polymorphic Spoofer:** "Generate New Identity" button to manually rename/hide the Zap process as a random Windows service.
  * **Biometric Typing Engine:** * **Target WPM** slider.
    * **Randomized Delay bounds (ms)** (e.g., 60ms - 150ms).
    * **Human Error %** slider to inject artificial typos and backspace corrections.

### 2.3 The [PLUS] Tab (Bare-Metal Kernel Isolation)
**Target:** Kernel-level lockdown browsers (Respondus, SEB, Pearson OnVUE, Bluebook, PSI Secure, EC-Council/LogMeIn Resolve).
* **Mechanic:** Creates a dual-session bare-metal environment using a custom RDP wrapper.
* **Hybrid Injection Mode:** A toggle that allows users to securely inject the [LITE] tab's stealth floating browser and the [CORE] tab's biometric typing directly *into* the [PLUS] VM session, allowing all three tiers to operate simultaneously.
* **Settings Panel:**
  * **"Setup This PC" Button:** When clicked, it launches the standalone **RDP Wrapper Installer** executable. 
    * **Windows Home Fix:** This installer automatically patches the host system's `termsrv.dll` file in System32 to forcefully allow concurrent multi-session RDP hosting, completely bypassing Microsoft's standard Windows Home Edition RDP locks.
  * **Adaptive Resolution:** Toggles for "Host Fullscreen" vs. "Custom X/Y" with free aspect ratio stretching for ultra-wide monitors. Includes a "Hardware GPU Acceleration" sub-toggle to prevent fullscreen lagging.
  * **Hardware Passthrough:** Dropdown to route the raw physical IDs of the Host Microphone and Webcam into the VM. Includes a **"Force-Refresh USB Cache"** button to fix the Evadus bug where cameras fail to show up in the list.
    * **Native USB-over-IP Tunnel:** Eliminates the need for paid third-party apps like VirtualHere. Zap natively emulates physical USB hubs to perfectly pass modern webcams and proprietary devices directly into the VM.
  * **GPU Driver & Gamma Bypass Toggle:** Kernel-level hooks to spoof GPU signatures and defeat advanced color-monitoring detection.
  * **Dynamic Resource & Firmware Allocation:** Input fields to manually specify CPU Core Count, RAM allocation, and a button to **"Clone Host SMBIOS/MAC Address"** so the VM perfectly mimics the Host PC's hardware fingerprint to bypass deep forensic checks.
  * **Interception Monitor:** A live, scrolling terminal log of detected proctor executables.
* **Robotic Audio Fix:** Hardcodes a 48kHz / 16-bit audio stream with a fixed 20ms buffer size via the RDP registry, guaranteeing clean microphone passthrough.
* **Hypervisor Watchdog (Boot Loop Fix):** Edits the virtual machine's BCD (Boot Configuration Data) to permanently disable `RecoveryEnabled` and ignore all disk-check flags, preventing the "Preparing Automatic Repair" loop.
* **Bug Fixes:** Hardcoded override that replaces the VM "Sign Out" button with a "Shutdown" button to prevent session boot loops.

---

## 3. REMOTE SCREENSHARE HUB (STEALTH ASSISTANCE)
Designed to provide a secure, proctor-invisible portal for remote helpers. Accessed globally via the Broadcast Icon.
* **Architecture:** A standalone stealth-wrapped pop-up window built directly into the Zap kernel.
* **UI Elements:**
  * **ID Field:** Displays the user's secure connection ID.
  * **Password Field:** Displays a temporary, session-based passcode.
  * **Connection Toggle:** Large button to initiate/terminate the WebSocket handshake.
* **Bypass:** Operates entirely through Zap's process-ghosting, making it invisible to proctoring software that specifically flags AnyDesk, TeamViewer, or Chrome Remote Desktop.
* **Proctor-Priority Input Override:** If a live proctor takes control of the student's mouse, physical movement on the host machine instantly suspends the remote helper's input for 10 seconds to prevent "cursor fighting."
* **Full Input Passthrough:** Explicitly encodes and transmits mouse-wheel scroll events and modifier keys (Ctrl/Shift) via the WebSocket to ensure the remote helper has native 1:1 control.
* **Silent Comms Channel:** Once connected, the remote helper can type messages that appear as a tiny, translucent, scrolling text-ticker at the very bottom edge of the student's screen.

---

## 4. THE AI ASSISTANT OVERLAY & UI
The primary ImGui overlay used inside the exam environment.

### 4.1 UI Placement & Accessibility
* **Default State:** Anchored vertically to the right side of the screen.
* **Compact Mode (Stealth Anchor):** Clicking the minimize dash collapses the entire UI into a tiny 50x50px floating pill. Expanding it restores the exact previous state.
* **Click-Through "Ghost" Mode:** A UI toggle (and hotkey) that locks the overlay visually on screen but makes it completely un-clickable. All mouse events pass *through* the overlay directly into the exam software underneath, ensuring it never blocks "Submit" or "Next" buttons.
* **Persistent UI Memory:** Remembers X/Y position, scaling, and opacity across all sessions and reboots.

### 4.2 AI Intelligence & Workflow
* **Omni-Model Selector:** Dropdown for available models based on user tier.
* **Omni-Model Quick Cycle:** A keyboard shortcut to cycle through LLMs instantly without opening the dropdown.
* **OpenRouter Auto-Mode (Dynamic Routing):** A powerful toggle that allows OpenRouter's native auto-routing algorithm to decide which model to use. It dynamically analyzes the user's prompt and sends it to the most capable, cost-effective model for the task.
* **Offline Local-LLM Failsafe:** If the proctoring software strictly severs all outbound internet connections, Zap automatically falls back to pinging the local LM Studio IP/Port, allowing full AI capability completely offline.
* **System Prompt Injection:** User-defined master behavior rules (e.g., "Answer-only mode").
* **Live Interview Transcription Mode:** A dedicated toggle that establishes a real-time audio pipeline from the host system/microphone directly to the AI, providing live transcription and coding answers for verbal job interviews.
* **Rapid Fire (Continuous) Mode:** A toggle specifically for fast-paced multiple-choice exams. When active, Zap automatically captures a pre-defined screen region every *X* seconds (user-configurable) and silently queries the AI, feeding a continuous stream of answers to the Discrete Answer Module without the user ever touching the keyboard.
* **Auto-Text Appending:** Field to automatically attach a prefix (e.g., "Solve this:") to all captures.
* **Neural Text Sanitization:** Regex filter to strip AI-disclaimers (e.g., "As an AI model...").
* **Textbook/CV Upload:** Button to attach PDFs for the AI to reference during answers.
* **Dual-Injection OCR Method (The Math & Graph Bypass):** * The screen snipping tool captures the image and simultaneously processes it through a local, specialized LaTeX OCR neural network. 
  * Zap sends the *raw, uncompressed screenshot* directly to the AI's native vision engine.
  * Directly underneath the image, Zap injects the perfectly extracted LaTeX math text to prevent the AI from hallucinating compressed, blurry symbols.

### 4.3 UI Features
* **Drag-and-Drop Capture Cache:** Vertical sidebar history for thumbnails; support for multi-image sending.
* **Follow-up Input Box:** A dedicated text field at the bottom of the chat to ask the AI follow-up questions about the generated answer.
* **Anti-Detector Paraphraser Engine:** A dedicated hotkey module that allows the user to instantly rewrite an AI-generated essay or text block to explicitly bypass Turnitin and other academic AI detectors. Can be cycled up to 5 times per query.
* **Discrete Answer Module:** A tiny, transparent, scrollable box (200x100px) showing *only* final A/B/C/D answers for 2-camera physical room scans.
* **Markdown Rendering:** Formatted equations, code blocks, and bold text.
* **Push-to-Talk (PTT) Audio Query:** Bound to a mouse side-button or USB foot pedal. Hold to whisper questions to the AI hands-free.

---

## 5. STEALTH CONTROLS & HOTKEYS
* **Master Pause / Release (Ctrl+Alt+C):**
  * **Action:** Physically severs all input to the VM for safe Host OS usage.
  * **Visual & The Legend Overlay:** The VM window dims 20% and a bold Yellow banner reads: **"ZAP: MOUSE RELEASED"**. Crucially, this paused state renders a clear, on-screen visual legend displaying all active hotkeys (Snip, Hide, Panic, Paraphrase, etc.) so the user does not have to memorize them under pressure.
  * **Spatial Persistence:** Cursor teleports instantly back to the exact last VM coordinate upon unpausing.
* **The Panic Switch (Ctrl+Alt+F):** Instantly vaporizes the RAM Vault, terminates AI threads, and vanishes all overlays.
* **Capture Tools & Hotkeys:**
  * **Keyboard Snip Hotkey:** Dedicated global keyboard shortcut (Default: `Ctrl+Shift+S`, user-customizable) to instantly trigger the stealth region capture tool.
  * **The Auto-Clipboard Sanitizer:** Directly post-snip, Zap actively wipes the Windows clipboard in sub-10 milliseconds to prevent SEB/Mercer Mettl from detecting the image in the system memory.
  * **The Paraphrase Hotkey (Ctrl+Shift+P):** Immediately triggers the Anti-Detector Paraphraser Engine on the last generated text block.
  * **Ghost Mode Hotkey (Ctrl+Shift+G):** Instantly toggles the overlay's click-through state.
  * **Extended HID / Foot Pedal Support:** Explicit API support to map any hotkey directly to F13-F24 bindings, natively supporting generic USB Foot Pedals for fully hands-free interaction.
  * **Nav-Bar Rapid Capture:** Title-bar camera icon for 1-click Snip-Paste-Send.
* **Capture Indicator Suppression:** Hooks deeply into the Windows Desktop Duplication API to actively suppress the "Screen is being recorded" red-dot indicator or system-tray notifications generated by the host OS.
* **Stealth DVR (Local Recording):** A hotkey-triggered, hardware-accelerated local screen recorder that saves directly to the Volatile RAM Vault, bypassing OBS/Game Bar blocks, allowing users to secretly record exams for later study.
* **3-Cursor Remote Spoofing:** Generates a smoothed, delayed "fake" mouse path for proctor recording software to hide remote-helper movements.

---

## 6. NETWORK, SECURITY & AI ARCHITECTURE

### 6.1 Master OpenRouter Gateway
* **Centralized AI Provisioning:** The Zap backend routes all premium/unlimited user requests through a **single Master OpenRouter API Key** managed by the owner.
* **BYOK Fallback:** If a user is on the Free tier or exhausts their quota, they can input their own OpenRouter key in the Global Settings.

### 6.2 Network Stealth (Domain Fronting)
* To bypass network traffic analysis, all Zap API calls are domain-fronted to look like standard Windows Telemetry or Microsoft Azure traffic. 

### 6.3 Anti-Crack & HWID Locking
* **Hardware ID (HWID) Binding:** Upon login, the user's session token is cryptographically bound to their motherboard and CPU serial numbers. 
* **Server-Side Validation:** All AI requests and bypass payload injections require a server-side handshake.

---

## 7. ERROR HANDLING & SUPPORT MATRIX

| Error State | User-Facing Message | Zap Auto-Resolution Logic |
| :--- | :--- | :--- |
| **Needs Admin** | *(Never shown)* | App manifest forces Administrator launch by default. Bypasses "Code 740". |
| **Unzip Fail** | *"Corrupted Payload."* | Auto-deletes temp folder and re-downloads the installer. |
| **VM Boot Loop** | *"VM State Corrupted."* | Hypervisor Watchdog ignores BCD recovery flags. "Nuke & Rebuild" fallback. |
| **Hardware Lock**| *"Hardware Locked by Host."* | Prompts user to close conflicting apps (Discord/Zoom). |
| **API Failure** | *"API Authentication Failed."* | If BYOK is invalid, auto-reverts to Zap Master Key. |
| **Audio Desync** | *"Audio Driver Lag."* | Forces 20ms fixed RDP audio buffer via registry hooks. |
| **SEB UI Glitch**| *(Silent)* | Temporarily disables hardware overlay planes if SEB display hooks clash. |
| **Service Hang** | *"Starting App..."* | Auto-detects if the UI registry service hangs for >15s and forces a silent restart of the UI thread. |

---

## 8. BUSINESS LOGIC & MONETIZATION (API SYNC)

### 8.1 Local Development Bypasses (Feature Flags)
During the C++ build phase, all tier locks, API checks, and HWID bindings are strictly disabled via developer flags to allow rapid local testing:
* `#define DEV_UNLOCK_ALL true` (Unlocks all premium AI features/models).
* `#define DEV_DISABLE_HWID true` (Bypasses motherboard cryptographic locking).

### 8.2 Web-First Purchasing Architecture
* **Purchase Flow:** Users create accounts and purchase subscriptions entirely on the Zap Website. 
* **App Sync:** The Zap desktop app contains NO payment processing UI. Upon login, the app hits the `api.zap.com/v1/auth` endpoint to retrieve the user's active tier and sets the internal state.

### 8.3 Subscription Tiers (AI & Usage Caps)
*Note: All Bypass mechanisms (LITE, CORE, PLUS) are completely free. Users pay strictly for AI bandwidth and features.*

* **Basic Plan ($0):**
  * 5 Requests / day. 
  * 1 Screenshot / Audio clip per request.
  * AI Chat via BYOK (Bring Your Own Key) only.
  * Access to 1 AI Model (Gemini 2.5 Flash Lite).
  * Additional Context & File Uploads.
  * Unlimited Evadus Lite Access, Screensharing, and Remote Access Tool.
* **Premium Plan ($35/month | $50/year):**
  * Unlimited Requests. 
  * 5 Screenshots / Audio clips per request.
  * AI Chat (Powered by Owner's Master OpenRouter Key).
  * Access to all Gemini Models (3.1 Pro, 2.5 Pro, etc.).
  * Default Additional Context Presets.
  * Customizable Hotkeys.
  * File Uploads.
  * 2 hours of Screensharing.
  * Remote Access Tool.
* **Unlimited Plan ($60/month | $80/year):**
  * Unlimited Requests. 
  * Unlimited Screenshots / Audio clips per request.
  * AI Chat (Powered by Owner's Master OpenRouter Key).
  * Access to all flagship AI models (Claude 4.6 Opus, Grok 4, GPT-5.2, Deepseek V3.2 R1) & OpenRouter Auto-Mode.
  * Customizable Presets & Context.
  * File Uploads.
  * Unlimited Screensharing.
  * Remote Access Tool.

---
**[END OF MASTER SPECIFICATION V1.18]**