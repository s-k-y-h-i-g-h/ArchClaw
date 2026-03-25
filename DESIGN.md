# ArchClaw Design Document

## Overview

ArchClaw is an opinionated distribution combining Arch Linux with OpenClaw to create an AI-native personal computing environment where the AI assistant is deeply integrated into the system experience.

## Collaboration Note

This project emerged from collaborative exploration between the user and Ember (an OpenClaw assistant). The user provided the core vision, direction, and key insights, while Ember helped elaborate, structure, document, and explore implications of these ideas through sustained dialogue and joint thinking.

## Core Principles

1. **Integration over Installation**: OpenClaw isn't just an app—it's a core system component
2. **Progressive Disclosure**: Complexity is revealed as needed, not all at once
3. **Safety by Default**: Updates, backups, and isolation are automatic
4. **Extensible Foundation**: Skills are the primary unit of functionality
5. **Cross-Platform Consistency**: Similar experience regardless of host OS

## System Architecture

### Layers
1. **Host OS** (Windows/macOS/Linux)
2. **Virtualization Layer** (WSL2, chroot, container, or native)
3. **Arch Linux Base** (minimal, rolling release)
4. **OpenClaw Core** (gateway, session management, basic tools)
5. **ArchClaw Metapackage** (opinionated configs, default skills, update wrapper)
6. **User Workspace & Skills** (customizable, backed up)

### Key Components

#### Unified Update Wrapper (`archclaw-update`)
- Handles pacman updates with pre/post snapshots
- Updates OpenClaw core via npm/git
- Updates skills with dependency checking and isolated testing
- Provides rollback capability
- User-configurable update channels (stable, testing, bleeding-edge)

#### Skill Management System
- Skills packaged similarly to Arch PKGBUILDs
- Central repository (could start as GitHub repo, evolve to dedicated index)
- Native TUI installer (`archclaw-skill`) for browsing/searching/installing
- Skills declare dependencies, conflicts, and provided capabilities
- Isolated testing environment for skill updates

#### First-Boot Experience (`archclaw-welcome`)
- Guided tour of OpenClaw concepts:
  - Memory system (MEMORY.md vs daily notes)
  - Skill discovery and installation
  - Agent spawning and subagent workflows
  - Heartbeats and proactive assistance
  - Verification and early warning concepts
- Helps user set up:
  - Basic identity (IDENTITY.md)
  - Initial skill bundle selection
  - Backup configuration (private repo setup)
  - Preferred thinking models/token budgets

#### Backup & Continuity System
- Automatic, encrypted workspace backups
- Integration with private GitHub repo (user-owned)
- Snapshot-like restore points for major changes
- Workspace portability between devices

#### Networked Intelligence Layer (via clawsend)
- Configure clawsend skill during installation to enable peer-to-peer messaging
- Allows instances to connect with trusted friends' ArchClaw instances
- Supports distributed verification: submit implementations for independent review by network peers
- Enables collaborative development: multiple users can coordinate on requirement documents and agent workflows
- Facilitates knowledge and skill sharing: instances can recommend effective skill configurations or verify each other's outputs
- Builds a web of trust for validation, extending verification protocols beyond the local instance
- Implements opt-in, privacy-preserving connections with user-controlled sharing boundaries

#### Cross-Platform Deployment
- **Windows**: Installer checks/enables WSL2, deploys Arch rootfs
- **macOS**: Uses `proot-docker` or Lima to run Arch container
- **Linux**: Uses chroot or systemd-nspawn container (or native install)
- **Native Arch**: Standard pacman installation of `archclaw` metapackage

## Implementation Roadmap

### Phase 1: Foundation (0-1 month)
- Create ArchClaw metapackage with opinionated defaults
- Build basic update wrapper script
- Create first-boot welcome system
- Document skill packaging format
- Set up initial GitHub repo structure

### Phase 2: Skill Ecosystem (1-2 months)
- Develop native skill TUI installer
- Convert several existing OpenClaw skills to package format
- Create developer/research/home manager/creative skill bundles
- Implement basic dependency checking

### Phase 3: Safety & Polish (2-3 months)
- Add snapshot/rollback system (btrfs or snapper-based)
- Implement automated backup to private GitHub
- Refine cross-platform installers
- Add update channels and metadata
- Comprehensive testing

### Phase 4: Community & Growth (3+ months)
- Public skill repository/index
- Documentation and tutorials
- Community contribution guidelines
- Integration testing matrix

## Open Questions & Considerations

1. **Update Safety**: How to handle kernel/initramfs updates vs skill updates differently?
2. **Resource Isolation**: Should skills have resource limits (CPU/memory)?
3. **Security Model**: How to validate skill integrity and prevent malicious packages?
4. **User Expertise Gradient**: How to serve both beginners and advanced users?
5. **Performance**: Impact of containerization/chroot on OpenClaw responsiveness?
6. **Integration Depth**: Should OpenClaw manage system services or just interact with them?

## Philosophy

ArchClaw embodies the belief that personal computing should be:
- **Intelligent**: The system learns and adapts with you
- **Transparent**: You understand how it works and why it does what it does
- **Empowering**: It extends your capabilities rather than replacing judgment
- **Resilient**: It protects your work and recovers gracefully from issues
- **Extensible**: You can shape it to fit your evolving needs

By combining Arch's flexibility and minimalism with OpenClaw's agent-based AI architecture, ArchClaw aims to create a computing environment that feels less like using tools and more like working with a thoughtful, capable partner.