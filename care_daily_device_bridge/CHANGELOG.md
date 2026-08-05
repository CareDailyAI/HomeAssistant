## 0.9.0
- feat: Implement setup wizard and enhance device on-boarding features (#50) (f31d29d)

## 0.8.0
- feat: Auto-assign default cloud and MQTT topic for newly exposed devices (#48) (6d0aa7d)
- chore: improve test coverage (95ebb21)

## 0.7.2
- fix: select all functionality breaks with a large number of devices (#49) (f932837)
- docs: evaluate Phase 2 performance roadmap and add readiness criteria (#44) (#47) (25aabef)

## 0.7.1
- fix: Device state not updated on cloud after receiving a command (#43) (887962c)

## 0.7.0
- feat: Add Select All and Bulk Action Capabilities (#42) (8310b96)

## 0.6.2
- revert: reverting change to package name (9e574c6)

## 0.6.1
- fix: errors with pipeline (d6de2af)

## 0.6.0
- fix(ci): streamlining CICD pipeline (e0768a8)
- feat: organizing attributes into map (#33) (b9c0182)
- chore: Fix pkg resources warning (#21) (5becdd0)

## 0.5.0
- feat: migrate ghcr package namespace to peoplepower organization (cd64e69)

## 0.4.1
- fix(ci): specify correct platforms and setup QEMU in build step (0463ad6)

## 0.4.0
- feat(ci): updating build and config pipeline for multi-architecture support (#32) (3da2bf1)

## 0.3.3
- fix(ci): checking for malformed secret value (85b88f6)

## 0.3.2
- fix(ci): tagging updates (dc93b73)
- fix(ci): targeting homeassistant repo for installtion token (#31) (0f89886)
- fix(ci): Publish job inherits secrets from calling job (#30) (57bd984)
- fix(ci): mint token for CareDailyAi organization (#29) (443b7c3)
- Fix(ci): adding github project to deploy workflow (#28) (0b40608)

## 0.3.1
- fix(ci): fixing release publish job (#27) (662ee43)
- chore: updating Publish release workflow (#26) (5d5abb1)

## 0.3.0
- feat: Implement Area on devices (#25) (b47b8b1)
- chore: addressing bandit issue discovered (#23) (f23e600)
- adding inovelli switch to Supported Devices md (#22) (4c04a33)

## 0.2.0
- [feat] Implementing MQTT command subscription (#20) (4112e53)
- [feat] merging hub device schema for MQTT state (#19) (a1be6fb)
- feat: introduce virtual hub device for health reporting and system metadata (#13) (569652f)
- refactor: transition device selection and registry management from entities to devices (e332e2a)
- feat: implement sensor life cycle (#12) (68c708a)
- fix(docs): Adding proposed state payload contract document (1c3839f)
- feat: Rename and rebrand the Home Assistant app as Care Daily Bridge (#6) (da37fcb)
- fix(ci): move release automation to GitHub Actions (#5) (b840fa8)

## 0.1.2
- fix(ci): migrate CI and release automation to GitHub Actions (25c0a43)
- fix(ci): adding new pipeline to run tests and increment version tags (3a4a976)

## 0.1.1
- refactor: reduce code duplication to improve maintainability (e30eb7d)
- feat: create MQTT payload mapping service (1ac0930)
- refactor: adjust sensor_unique_id length (96d9fe3)
- feat: add sensor_unique_id to UI (dca62b8)
- refactor: adjust sensor_unique_id structure (3a2179c)
- fix: add device flow (826b145)
- feat: persist database and certificate storage (07c0f34)
- feat: add sensor_unique_id and shorten hub_unique_id (1c977a0)
- refactor(ui): update CSS styles (8228368)
- chore: add AGENTS.md instructions (039c3f1)
- feat: implement login modal and device registration (2e01b3b)
- feat: add clear logs function for cloud services (98d6c1c)
- feat: implement login flows for email code and username/password (49a5e01)
- feat: add device details button to device cards (39be4de)
- feat: add additional logging metrics (663f112)
- feat: add initial logging and metrics collection (18a120d)
- feat: persist login data across sessions (76270fa)
- feat: add Home Assistant device details modal dialog (0b2177d)
- refactor: application factory and transaction-managed DB writes (0e2f9c8)
- chore(ci): update build and push job networking options (2a44871)
- chore(ci): update build and push workflow configurations (c59510a)
- fix(ci): repair GitLab CI runner job execution (c05708e)
- refactor: centralize system configuration settings (72fd5d8)
- refactor: optimize and organize backend code structure (f886cf9)
- refactor: general performance optimizations (43402d3)
- feat: support list of Care Daily URLs in settings (e50e08c)
- refactor: clean up device filtering and onboarding flows (dee5232)
- feat: implement application state management (875a80d)
- refactor: align integrations for Home Assistant compatibility (79d23d6)
- feat: add initial prototype application codebase (d00bcbc)
- chore: initial commit (3e34fb9)
- chore: initial commit (fccf66e)

