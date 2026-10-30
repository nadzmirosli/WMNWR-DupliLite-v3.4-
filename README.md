# WMNWR-DupliLite-v3.4-
A lightweight Microsoft Edge (Chromium) extension that automatically detects and highlights duplicate words and numbers on any webpage, with no manual search or trigger needed.

WMNWR DupliLite (v3.4)
One-line summary

A lightweight Microsoft Edge (Chromium) extension that automatically detects and highlights duplicate words and numbers on any webpage, with no manual search or trigger needed.

CV-ready version (short)

WMNWR DupliLite: Browser Extension (Edge/Chromium)

Built a Manifest V3 browser extension that auto-scans webpages and highlights repeated words and numbers in real time.
Implemented configurable detection: word length (2–20), digit count, minimum occurrences (2–20), case sensitivity, and a common-word filter.
Designed a user-defined date/time format filter (tokens like DD/MM/YYYY, HH:MM:SS) that converts to regex, so dates and times are excluded from number matching.
Optimized the DOM engine to stop highlight flashing and scroll-triggered re-scans, using a debounced MutationObserver that ignores its own changes.
Created a single-screen popup UI with live statistics, custom highlight colors, and a context-menu toggle.
Detailed description

Problem: Existing duplicate-text extensions require manual triggering. This one runs automatically on page load and when new content appears.

Core features

Three modes: Words, Numbers, or Both, each with its own highlight color.
Detection controls: min word length (2–20), min digit count for numbers (1–20), min occurrences (2–20).
Filters:
Built-in common-word ignore list
Case-sensitive toggle
Custom date and time formats, entered as editable tags
Auto-rescan: Detects newly added page content (e.g. infinite scroll) and re-highlights it after a debounce delay.
Popup UI: Live stats (total, unique words, unique numbers), color pickers with preview, and a manual “Scan now” button.
Extras: Right-click context menu to toggle on/off; settings persist across sessions and devices via chrome.storage.sync.

Technical implementation

Manifest V3 with a service worker (background), content script, and popup
TreeWalker for text-node traversal, skipping script/style/input and similar elements
Regex-based tokenization for words and numbers, with named capture groups for highlighting
MutationObserver limited to childList changes, paused during scans to prevent feedback loops
Messaging between popup, content script, and background via the Chrome extension API
<mark> elements tagged with a data- attribute for fast clean-up and statistics

Tech stack: JavaScript (ES6+), HTML5, CSS3, Chrome Extensions API (Manifest V3), Regular Expressions, DOM APIs

Version history (if you want to show iteration)

v1: Basic auto-highlighter for words
v2: Added numbers mode and mode switching
v3: Date/time filtering, custom formats, min digit count, redesigned UI
v3.4 / DupliLite: Single-screen UI, performance optimization, scroll-flash fix
