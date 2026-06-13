# Changelog

All notable changes to InterceptSuite are documented in this file.

---

## [1.2.0] - 2025-11-09

### 🆕 New Features
- **Upstream Proxy Support** — Chain InterceptSuite with another SOCKS5/HTTP proxy for advanced routing setups.
- **DTLS MITM (Pro Version)** — Full DTLS interception and decryption support for UDP-based protocols.
  > ⚠️ HTTP/3 support is still pending and will be added in an upcoming release.

### 🛠️ Fixes
- Fixed intercepted data stuck issue caused by packet ID collision ([#11](https://github.com/InterceptSuite/InterceptSuite/issues/11)).
- Improved GUI performance — faster interface loading and smoother user interactions.

### 💼 Pro Improvements
- **Manual License Activation** — Pro users can now activate InterceptSuite offline.

---

## [1.1.1] - 2025-08-28

### 🛠️ Fixes
- Fixed TLS SNI error for IP address.
- Added bidirectional TCP packet support.
- Fixed connection delay in plaintext TCP and TLS Upgrade.
- Fixed multiple TLS errors.
- Improved STARTTLS detection.

---

## [1.1.0] - 2025-08-24

### 📦 Edition Changes
InterceptSuite introduced two editions:
- **Standard Edition** (formerly Open Source) — Free and open source
- **Pro Edition** — Premium features for professionals and enterprises

### ✨ New Features
- **Python Extension APIs** — Comprehensive APIs for custom extensions and plugins; extensible architecture for community contributions.
- **TLS Upgrade Detection (Pro)** — Automatic detection of TLS upgrades for SMTP (StartTLS), PostgreSQL, MySQL, POP3, and more.
- **Project File Support (Pro)** — Save/load project configurations, manage multiple testing scenarios, import/export settings.
- **PCAP File Export (Pro)** — Export captured traffic to PCAP format, compatible with Wireshark and other analysis tools.
- **HTTP/2 Support** — Complete protocol support, binary frame inspection, stream multiplexing analysis.
- **UDP Relay Server** — New relay functionality, enhanced UDP traffic handling and performance.
- **Certificate Regeneration** — Generate new certificates directly from the application, no external tools required.

### 🔧 Major Improvements
- **Intercept Feature Rewrite** — Completely rewritten from scratch:
  - Efficient large queue handling
  - FIFO queue processing
  - Proper connection timeout handling
  - Enhanced stability and multiple bug fixes
- **TLS Handshake Improvements** — Better compatibility with various TLS implementations, improved error handling and debugging.
- **Enhanced Filtering & Search** — Improved filter performance, faster result processing.
- **Auto-Start Proxy** — Proxy server now starts automatically on application load, reducing setup time.

### 🐛 Bug Fixes
- Fixed UDP plaintext handling issues.
- Fixed application crash on large proxy history.
- Fixed buffer overflow vulnerabilities.
- Fixed Time-of-Check Time-of-Use (TOCTOU) security vulnerability.
- Multiple stability improvements, memory leak fixes, performance optimizations, and UI responsiveness enhancements.

### 📋 Technical Details
- Improved memory management and multi-threading support.
- Enhanced input validation and error handling.
- Faster startup times, reduced memory footprint, improved response times for large datasets.

---

## [1.0.1] - 2025-06-08

### 🚀 What's New
- **Cross-Platform Support** — InterceptSuite now supports Windows (x64), macOS (Apple Silicon/ARM64), and Linux (x64).
- **Certificate Export Feature** ([#1](https://github.com/Anof-cyber/InterceptSuite/issues/1)) — Easy certificate export to streamline usage across environments; improved certificate handling for cross-platform compatibility.
- **Standardized Application Data Storage** — Logs, configuration, and app data now stored in platform-appropriate directories:
  - Windows: `%LOCALAPPDATA%\InterceptSuite\`
  - macOS: `~/Library/Application Support/InterceptSuite/`
  - Linux: `~/.local/share/InterceptSuite/`
- **Plaintext UDP Protocol Support** — Added interception and analysis support.
- **TLS SNI Error Fix** ([#2](https://github.com/Anof-cyber/InterceptSuite/issues/2)) — Resolved Server Name Indication handling issues causing connection failures.
- **MQTT over TLS** — Initial support for IoT-specific protocols, enhanced TLS handling for persistent IoT connections.

### 🛠️ Technical Changes
- **Rust + Tauri GUI Framework** — Complete rewrite of the GUI from .NET Framework to Rust with Tauri for cross-platform support and modern UI.
- No more .NET dependency — GUI no longer requires .NET Framework/Runtime installation.
- UI built with HTML, CSS, and JavaScript powered by Tauri's Rust backend.

### 🐛 Bug Fixes
- Fixed TLS SNI error causing connection problems with certain servers ([#2](https://github.com/Anof-cyber/InterceptSuite/issues/2)).
- Improved stability across different operating systems.
- Enhanced error handling and logging.

### 📋 Known Issues
- DTLS (Datagram Transport Layer Security) not yet supported.
- Protocol dissection for binary formats (Protocol Buffers, MessagePack, etc.) not yet supported.
- Non-standard TLS handshake protocols (PostgreSQL, MySQL TLS) not yet supported.

**Full Changelog**: [v1.0.0...v1.0.1](https://github.com/Anof-cyber/InterceptSuite/compare/v1.0.0...v1.0.1)

---

## [1.0.0] - 2025-05-31

### 🚀 First Public Release

Initial release of InterceptSuite, a network traffic interception tool designed for TLS/SSL inspection, analysis, and manipulation at the network level.

### ✨ Key Features
- Protocol-agnostic TLS interception — works with any application or protocol.
- SOCKS5 proxy integration — compatible with any app that supports SOCKS5 configuration.
- Real-time traffic analysis — view and modify decrypted traffic as it flows through the proxy.
- Connection management — track and monitor active network connections.
- Certificate Authority management — automatic generation and management of CA certificates.
- User-friendly, modern GUI.
- DLL integration option — embed interception capabilities into custom applications.

### 🔧 Technical Details
- Built with C++11 and .NET 8.0.
- Windows 10/11 (64-bit) support.
- Available as a portable version.

---
