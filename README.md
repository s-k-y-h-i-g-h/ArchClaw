# ArchClaw

An opinionated distribution that combines Arch Linux with OpenClaw to create an AI-native personal computing environment.

## Vision

ArchClaw aims to integrate OpenClaw deeply into the operating system, providing:
- Unified updates for system, OpenClaw core, and skills
- Opinionated defaults (zsh, nvim, automated backups)
- First-boot onboarding to teach AI collaboration
- Customizable skill bundles (developer, research, home manager, creative)
- Native skill discovery and installation (TUI/GUI)
- Cross-platform deployment: WSL2 on Windows, chroot/containers for macOS/Linux, native Arch
- Networked intelligence layer: Configure clawsend to connect with trusted friends' instances for distributed verification and collaboration

## Collaboration Note

This project emerged from collaborative exploration between the user and Ember (an OpenClaw assistant). The user provided the core vision, direction, and key insights, while Ember helped elaborate, structure, document, and explore implications of these ideas through sustained dialogue and joint thinking.

## Ethical Use & Safety Considerations

ArchClaw is designed as a personal AI operating system to enhance individual productivity, learning, and wellbeing. Users should consider:

**Intended Use:**
- Personal productivity and learning enhancement
- Exploration of AI-assisted workflows in a controlled, personal environment
- Experimentation with AI concepts for educational purposes

**Responsible Networking:**
- The networked intelligence layer (via clawsend) is designed for connections with trusted, known individuals
- Users should only connect with instances they trust and have explicit permission to connect with
- Respect privacy boundaries and obtain consent before initiating connections
- Do not use network capabilities for unsolicited communication, surveillance, or harmful activities

**Safety Principles:**
- Verify information and outputs, especially when using AI-generated content
- Maintain appropriate boundaries between AI assistance and human judgment
- Use the verification and backups features to protect your work and data
- Discontinue use if the system produces harmful or unintended outputs

**Prohibited Uses:**
- Do not use ArchClaw to create, distribute, or facilitate harmful content, malware, or illegal activities
- Do not use networked features to harass, spam, or exploit others
- Do not attempt to bypass security measures or exploit vulnerabilities in the system or connected instances

## Core Concepts

### 1. Unified Update System
A wrapper that safely updates:
- Arch Linux packages (`pacman -Syu`)
- OpenClaw gateway and core
- Installed skills
With snapshot/rollback capabilities and dependency tracking.

### 2. Skill-Centric Design
Skills are the primary units of extensibility, packaged similarly to Arch PKGBUILDs but for OpenClaw functionality. A native skill browser allows discovery, installation, and management.

### 3. AI-First Experience
From first boot, users are guided on how to work effectively with an AI companion, establishing patterns for memory, verification, and proactive assistance.

### 4. Automated Safety & Continuity
- Encrypted, automated workspace backups (e.g., to a private GitHub repo)
- System restore points before major changes
- Skill isolation during updates/testing

## Deployment Targets

- **Windows**: WSL2-based Arch installation
- **macOS/Linux**: chroot or containerized Arch environment
- **Native Arch**: Direct installation of ArchClaw metapackage

## Getting Started

See [DESIGN.md](DESIGN.md) for detailed plans and architecture.

## Repository Structure

- `docs/` - Detailed design documents
- `scripts/` - Installation and utility scripts
- `packages/` - PKGBUILDs for ArchClaw-specific packages
- `skills/` - Core skill bundles
- `installer/` - Installer logic for different platforms

---
*ArchClaw: Where Arch Linux meets OpenClaw to create an intelligent personal computing environment.*