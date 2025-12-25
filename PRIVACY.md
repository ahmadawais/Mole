# Mole Privacy Policy

**Last Updated:** December 25, 2025

## Overview

Mole is a **100% local, privacy-first** macOS maintenance tool. We believe your data belongs to you and should stay on your device.

## What Data Does Mole Access?

Mole accesses your local system to perform cleaning, scanning, and monitoring operations:

- **File System**: Reads and deletes cache files, logs, and temporary files (only with your permission)
- **System Information**: Reads CPU, memory, disk, and network statistics for display in `mo status`
- **Application Data**: Scans installed applications for the uninstall feature
- **User Preferences**: Stores whitelist and configuration in `~/.config/mole/`

**Important:** All of this data stays on your Mac. Mole never uploads, transmits, or shares this information with anyone.

## What Data Does Mole Collect?

**None.** Mole does not collect any data about you or your usage.

- ✅ **No telemetry or analytics**
- ✅ **No usage tracking**
- ✅ **No crash reports sent remotely**
- ✅ **No user identifiers**
- ✅ **No IP address logging**
- ✅ **No behavioral tracking**

## Network Operations

Mole performs **minimal, optional network operations** only when you explicitly request them:

### 1. Version Check (Optional, Non-Blocking)
- **When**: Background check when you open the main menu, or when you run `mo update`
- **What**: Fetches the latest version number from GitHub API
- **Data Sent**: Your request includes standard HTTP headers (User-Agent, etc.) but no personal information
- **Purpose**: To notify you if a newer version is available
- **Can Be Disabled**: This check times out after 3 seconds and never blocks the application

### 2. Software Updates (On-Demand Only)
- **When**: Only when you explicitly run `mo update`
- **What**: Downloads the latest Mole installation script from GitHub
- **Data Sent**: Standard HTTP request headers only
- **Purpose**: To update Mole to the latest version

### 3. Initial Installation
- **When**: Only during the initial `curl | bash` installation
- **What**: Downloads Mole source files from GitHub
- **Data Sent**: Standard HTTP request headers only
- **Purpose**: To install Mole on your system

### Network Monitoring Display
- **Feature**: `mo status` shows network upload/download speeds
- **How It Works**: Reads local network interface statistics from your operating system (similar to Activity Monitor)
- **Data Sent**: **Nothing** - This is a read-only display of local system information

## Third-Party Services

The only third-party service Mole contacts is:

- **GitHub** (github.com / api.github.com) - For version checks and software updates only

We do not use:
- Analytics services (Google Analytics, Mixpanel, etc.)
- Crash reporting services (Sentry, Crashlytics, etc.)
- Ad networks
- Any other third-party tracking or data collection services

## Data Storage

Mole stores minimal configuration data locally:

- `~/.config/mole/whitelist` - User-defined protected paths (optional)
- `~/.cache/mole/` - Temporary cache for version check messages and session state

This data is **never uploaded** anywhere and stays on your Mac.

## Open Source Transparency

Mole is **fully open source** under the MIT License. You can:

- Audit the entire codebase at [github.com/tw93/mole](https://github.com/tw93/mole)
- Verify there is no hidden telemetry or data collection
- Build Mole from source yourself
- Modify it to meet your needs

## Code Verification

You can verify Mole's privacy claims by reviewing these files:

1. **Network operations**: 
   - `mole` (main script, lines 34-83) - Version check only
   - `install.sh` - Installation download only
   - `lib/check/all.sh` - Optional version check

2. **No HTTP client in Go code**:
   ```bash
   # This command will show zero results:
   grep -r "net/http" cmd/
   ```

3. **No telemetry**:
   ```bash
   # This command will show zero results for data collection:
   grep -ri "telemetry\|analytics\|tracking" . --include="*.go" --include="*.sh"
   ```

## Changes to This Policy

If we ever change our privacy practices (which would require adding network features), we will:

1. Update this document
2. Clearly announce the changes in release notes
3. Make changes opt-in, never opt-out

## Questions?

If you have questions about Mole's privacy practices:

- Open an issue: [github.com/tw93/mole/issues](https://github.com/tw93/mole/issues)
- Review the code: [github.com/tw93/mole](https://github.com/tw93/mole)

---

**Summary**: Mole operates entirely on your local system. Your data never leaves your Mac. The only network operations are optional version checks and updates that you explicitly request.
