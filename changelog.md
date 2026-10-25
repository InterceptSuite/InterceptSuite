# Changelog

All notable changes to InterceptSuite are documented in this file.

---

## [2.1.0] - 2026-10-25

### 🆕 New Features
- **Traffic redirect (Windows)** - Send selected applications through InterceptSuite without changing their proxy settings. Open **Proxy > Redirect**, add rules by application, host or IP, and port, and choose to send the traffic through the proxy, let it go direct, or block it. Rules are saved with the project, redirect is off until you press **Start**, and **Pause** stops it for new connections without losing your rules. InterceptSuite itself is never redirected. Powered by [ProxyBridge](https://github.com/InterceptSuite/ProxyBridge) and the WinDivert driver.
- **Install Certificate** - Install the InterceptSuite CA certificate from the app instead of doing it by hand.
- **Optional redirect setup in the installer** - A checkbox on the last page sets up the redirect service for you. Windows asks for administrator permission once; InterceptSuite itself keeps running without it.

### 🛠️ Fixes
- The app no longer keeps running after you close the window, and the proxy no longer uses a core at 100% after a failed accept.
- The window no longer shows "Not responding" under heavy traffic.

### 📋 Known Limitations
- Traffic redirect is Windows-only for now.

---

## [2.0.0] - 2026-10-04

### 🆕 New Features
- **Replay** - Send your own packets over TCP, TLS, STARTTLS, UDP, DTLS and QUIC, in as many tabs as you need. Sessions are saved with the project.
- **Interception rules** - Hold only the packets you want, separately for client to server and server to client, with and/or rules on host, port, protocol, size, payload and Scope.
- **Scope** - Define your targets, add them from Proxy History with a right-click, and filter by in-scope or out-of-scope traffic.
- **TLS pass-through** - Relay selected targets untouched, for apps that pin certificates.
- **Proxy History filters** - Wireshark-style expressions such as `port == 443 and data contains "token"`.
- **Host and ALPN columns** in Proxy History, for every protocol.
- **AI access (MCP)** - Let an AI agent such as Claude Code or Claude Desktop read your history, change settings, use Replay and work the Intercept queue. Controlled from Settings, local only, and logged.
- **HTTP/3 through the proxy** - HTTP/3 support via QUIC.
- **New Settings tab** for upstream proxies, Scope and AI access.
- **Extensions** now receive the host, ALPN, protocol and packet id of each packet, and their tabs appear only when they apply.
- **Hex Editor** - The Hex Data tab now lets you edit data in hex format.

### 🔧 Improvements
- QUIC: every stream of a connection is relayed, and several connections from one application all work.
- DTLS and TLS: correct server names are sent to the real server, which fixes sites behind CDNs.
- UDP: one slow server no longer stalls other clients, and multi-datagram replies are relayed in full.
- Faster TLS connection setup, a Proxy History search that no longer freezes on large histories, and lower memory use.
- Faster, safer project saving, with a "Saving..." indicator for large backlogs.
- The log now explains failed connections from clients that use Encrypted Client Hello (ECH).

### 🔒 Security
- The certificate authority's private key is now readable only by your user account.
- Updates are only accepted from secure links and must be signed by InterceptSuite.
- Many crashes and memory problems in the proxy were fixed.

### 🛠️ Fixes
- **Linux:** the app now starts on current distributions (Ubuntu 22.04 and later, Fedora 35 and later). It no longer fails when `libdl.so` is missing.
- Interception now works on Linux and macOS.
- Interception no longer hangs after 100 held packets or when stopping the proxy.
- Proxy History is no longer empty after opening a saved project.
- Replay: no false "SSL read error", no DTLS freeze on disconnect, and binary data is sent unchanged.
- PCAP export: correct addresses in both directions, and QUIC and DTLS exported as UDP.
- Many fixes for crashes, hangs and lost data during long sessions.
- Encrypted Client Hello (ECH) detection.

### ⬆️ Upgrading from 1.3.0
- Existing projects open as they are, and the new features start empty or off.
- The interception direction switches moved to **Proxy > Settings**, next to the rules.
- Connection ID is no longer a rule check, and the IP checks are now one **Server host or IP** check. Saved rules keep working.
- Updates now require an installer signed by InterceptSuite.

### 📋 Known Limitations
- Connections that use Encrypted Client Hello (ECH) cannot be intercepted.

---

## [1.3.0] - 2026-06-30

### 🆕 New Features
- **QUIC Protocol Interception** - InterceptSuite Pro now intercepts and decrypts QUIC traffic. All QUIC sessions appear in Proxy History just like HTTP/TLS: inspect, modify, and replay with the same workflow you already know.
- **DTLS Interception** - Full support for DTLS traffic over UDP. Encrypted DTLS sessions are now decrypted and visible in Proxy History alongside your existing TCP/TLS captures.
- **Project Management** - Open and save projects directly from the application. You can now launch InterceptSuite Pro with a project file path as an argument to jump straight into a saved session.

### 🔧 Improvements
- More reliable session cleanup - no stale sessions left behind after disconnect.
- Smoother application startup and shutdown.
- Minor UI refinements across dialogs and the main window.

### 🛠️ Fixes
- Fixed a crash that could occur when closing active sessions.
- Fixed an issue where the application could hang on exit with active connections.

---

## [1.2.1] - 2026-06-15

### 📢 Important Announcement
Starting with v1.2.1, **InterceptSuite is closed-source and Pro-only.** The community/standard (free) edition has been discontinued, and InterceptSuite is no longer open source. This ensures the continued development and maintenance of both InterceptSuite and [ProxyBridge](https://github.com/InterceptSuite/ProxyBridge), which remains fully open-source. See the [project README](https://github.com/InterceptSuite/InterceptSuite) for details.

### 💼 Pro Edition
- A **trial version** is now available - no purchase required to evaluate InterceptSuite.
- Students, researchers, or individuals with a valid non-commercial use case can email support@interceptsuite.com with the subject **"Community License"** to request a free Pro license.
- [Purchase InterceptSuite Pro](https://interceptsuite.com)

### 🛠️ Fixes
- Minor stability improvements and bug fixes.
- Fixed UDP session timeout.

---

## [1.2.0] - 2025-11-09

### 🆕 New Features
- **Upstream Proxy Support** - Chain InterceptSuite with another SOCKS5/HTTP proxy for advanced routing setups.
- **DTLS MITM (Pro Version)** - Full DTLS interception and decryption support for UDP-based protocols.
  > ⚠️ HTTP/3 support is still pending and will be added in an upcoming release.

### 🛠️ Fixes
- Fixed intercepted data stuck issue caused by packet ID collision ([#11](https://github.com/InterceptSuite/InterceptSuite/issues/11)).
- Improved GUI performance - faster interface loading and smoother user interactions.

### 💼 Pro Improvements
- **Manual License Activation** - Pro users can now activate InterceptSuite offline.

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
- **Standard Edition** (formerly Open Source) - Free and open source
- **Pro Edition** - Premium features for professionals and enterprises

### ✨ New Features
- **Python Extension APIs** - Comprehensive APIs for custom extensions and plugins; extensible architecture for community contributions.
- **TLS Upgrade Detection (Pro)** - Automatic detection of TLS upgrades for SMTP (StartTLS), PostgreSQL, MySQL, POP3, and more.
- **Project File Support (Pro)** - Save/load project configurations, manage multiple testing scenarios, import/export settings.
- **PCAP File Export (Pro)** - Export captured traffic to PCAP format, compatible with Wireshark and other analysis tools.
- **HTTP/2 Support** - Complete protocol support, binary frame inspection, stream multiplexing analysis.
- **UDP Relay Server** - New relay functionality, enhanced UDP traffic handling and performance.
- **Certificate Regeneration** - Generate new certificates directly from the application, no external tools required.

### 🔧 Major Improvements
- **Intercept Feature Rewrite** - Completely rewritten from scratch:
  - Efficient large queue handling
  - FIFO queue processing
  - Proper connection timeout handling
  - Enhanced stability and multiple bug fixes
- **TLS Handshake Improvements** - Better compatibility with various TLS implementations, improved error handling and debugging.
- **Enhanced Filtering & Search** - Improved filter performance, faster result processing.
- **Auto-Start Proxy** - Proxy server now starts automatically on application load, reducing setup time.

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
- **Cross-Platform Support** - InterceptSuite now supports Windows (x64), macOS (Apple Silicon/ARM64), and Linux (x64).
- **Certificate Export Feature** ([#1](https://github.com/Anof-cyber/InterceptSuite/issues/1)) - Easy certificate export to streamline usage across environments; improved certificate handling for cross-platform compatibility.
- **Standardized Application Data Storage** - Logs, configuration, and app data now stored in platform-appropriate directories:
  - Windows: `%LOCALAPPDATA%\InterceptSuite\`
  - macOS: `~/Library/Application Support/InterceptSuite/`
  - Linux: `~/.local/share/InterceptSuite/`
- **Plaintext UDP Protocol Support** - Added interception and analysis support.
- **TLS SNI Error Fix** ([#2](https://github.com/Anof-cyber/InterceptSuite/issues/2)) - Resolved Server Name Indication handling issues causing connection failures.
- **MQTT over TLS** - Initial support for IoT-specific protocols, enhanced TLS handling for persistent IoT connections.

### 🛠️ Technical Changes
- **Rust + Tauri GUI Framework** - Complete rewrite of the GUI from .NET Framework to Rust with Tauri for cross-platform support and modern UI.
- No more .NET dependency - GUI no longer requires .NET Framework/Runtime installation.
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
- Protocol-agnostic TLS interception - works with any application or protocol.
- SOCKS5 proxy integration - compatible with any app that supports SOCKS5 configuration.
- Real-time traffic analysis - view and modify decrypted traffic as it flows through the proxy.
- Connection management - track and monitor active network connections.
- Certificate Authority management - automatic generation and management of CA certificates.
- User-friendly, modern GUI.
- DLL integration option - embed interception capabilities into custom applications.

### 🔧 Technical Details
- Built with C++11 and .NET 8.0.
- Windows 10/11 (64-bit) support.
- Available as a portable version.

---
