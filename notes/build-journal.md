# Build Journal
This journal tracks each phase of the lab build, including setup work, issues encountered, fixes applied, and evidence captured.

## Entry 1 — Phase 1 Project Setup

- Date: [today]
- Phase: 1 — Project Planning and Repository Setup

### Objective
Set up the project structure, create the GitHub repository, and prepare the documentation and evidence framework for the lab.

### What I Completed
- Created the local project folder and organized the repository structure
- Added core folders for documentation, screenshots, notes, architecture, and configs
- Created starter files including:
  - README.md
  - environment.md
  - schedule.md
  - architecture-notes.md
  - project-scope.md
  - screenshot-log.md
  - recruiter-talking-points.md
  - tooling-notes.md
- Initialized the local Git repository
- Connected the project to GitHub
- Created and pushed the initial commit
- Created the first version of the architecture diagram
- Began documenting screenshots and project planning notes

### Problems I Hit
- Initially ran into a Git remote configuration issue because the GitHub username/repository URL was entered incorrectly
- Also hit a push error because the branch had been renamed to `main` before creating the first commit

### How I Fixed Them
- Verified the current remote with `git remote -v`
- Corrected the remote using `git remote set-url origin <correct-repo-url>`
- Added and committed files locally before trying to push
- Re-ran the push successfully after the initial commit existed

### Evidence Captured
- GitHub repository homepage
- Initial README
- Architecture diagram v1
- Git remote fix screenshot

### Outcome
Completed the initial project scaffolding and created a recruiter-visible GitHub foundation for the lab.

### Lesson Learned
Git setup issues are easy to fix if I check the repo state methodically using `git status`, `git remote -v`, and commit history before pushing.

### Next Step
Build the VirtualBox lab environment with Wazuh Server, Windows Endpoint, and Linux Endpoint.

## Entry 2 — Phase 2 Networking Issue

- Date: [today]
- Phase: 2 — Lab Environment Setup

### Objective
Configure dual-network adapters for the Wazuh server VM so the lab can support both internet access and internal communication.

### What I Completed
- Reviewed VirtualBox network settings
- Confirmed the Host-Only network existed and was configured with the 192.168.56.0/24 range
- Validated that Adapter 1 was set to NAT
- Identified why Adapter 2 settings were unavailable

### Problems I Hit
- I was unable to click or configure Adapter 2 for the Wazuh server VM in VirtualBox because the settings appeared locked

### Root Cause
- The VM was still in a running or saved state, and VirtualBox prevents hardware and network configuration changes while a VM is active

### How I Fixed It
- Fully powered off the VM instead of saving state
- Re-opened the VM settings
- Successfully configured:
  - Adapter 1: NAT
  - Adapter 2: Host-Only Adapter

### Evidence Captured
- Host-Only network configuration screenshot
- VM network settings screenshot
- Screenshot showing the corrected Adapter 2 configuration

### Outcome
Successfully enabled dual-network segmentation for the Wazuh server VM, which is required for:
- internet access through NAT
- internal lab communication through Host-Only networking

### Lesson Learned
VirtualBox locks network configuration when a VM is running or saved. Before changing adapters, I need to ensure the VM is fully powered off.

### Next Step
Apply the same dual-adapter configuration to the Windows and Linux endpoint VMs, then validate IP addressing and ping connectivity across all systems.