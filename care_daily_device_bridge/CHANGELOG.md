## 1.0.1
- docs(cloud-observations): log 2026-11-13 sandbox verification (4ff702d)
- fix(ui): replace personal mqtt topic placeholder with generic example (a9ef522)
- fix(ui): replace personal phone number placeholder with 111-456-7890 (70f2da5)

## 1.0.0
- feat(release)!: pin ubuntu-24.04 on release/deploy workflows and prepare v1.0.0 (184f42b)
- docs(cloud-observations): log 2026-11-12 sandbox verification (7eca94e)
- fix(ci): pin ubuntu-24.04 runner, add playwright browser cache, and bound job timeouts (61ff98a)
- docs(cloud-observations): log 2026-11-11 sandbox verification (b6958be)
- docs(cloud-observations): log 2026-11-10 sandbox verification (bd3f419)
- docs(cloud-observations): log 2026-11-09 sandbox verification (d2cd0b1)
- docs(cloud-observations): log 2026-11-08 sandbox verification (2361460)
- fix(telemetry): discriminate multi-destination queues and assert bridge cache update sequence (01dcf6b)
- fix(telemetry): resolve race conditions and ordering boundaries in ordered transition queue (4fd6a29)
- fix(telemetry): address code review findings for ordered transition queue (867f557)
- feat(telemetry): FIFO ordered transition queue for state changes (0d251dd)
- fix(mqtt): resend state that changed while a registry add waited, and list each device once (861388b)
- refactor(mqtt): share registry_add building between registry_get and the reconciler (f758f7b)
- fix(mqtt): keep other devices' state changes after a registry add, and stop refetching all HA states (65069d9)
- fix(mqtt): stop registry_get from stalling state publishing or over-registering (3322690)
- feat(mqtt): re-send registry_add for one device on a cloud registry_get command (6ac9694)

## 0.18.0
- ci(gitlab): install git and node for the test job (9cde43a)
- ci(gitlab): run the GitHub CI gates on every branch pushed to the GitLab mirror (c83005e)
- fix(mqtt): back off failed cloud MQTT connects and keep exception text out of error messages (0cd1334)
- fix(mqtt-server): make static IP and DHCP changes work through the Home Assistant sidebar (984de42)
- fix(security): trust only the Supervisor ingress proxy for credential backup (77a7a89)
- fix(credentials): restore real cloud backups ready to reconnect (673397d)
- fix(registry): auto-add only devices created after auto-add was turned on (84bbbde)
- fix(registry): stop cloud-deleted devices from being re-registered (dada868)
- feat(config): hide Early Preview Features behind a Show Experimental Features add-on option (af13eff)
- fix(workers): wake the cloud registry reconciler loop on stop (1b5b5d5)
- fix(mqtt): keep publisher wake-ups that arrive mid-publish so stop() ends the thread promptly (c2c7a65)
- fix(workers): check root log handlers before logging from background workers (761836a)
- fix(mqtt): route MqttStatePublisher and ZwaveConfigService logging through shutdown-safe _safe_log (c920274)
- docs(contracts): add MQTT registry_delete command specification (1e7a189)
- docs(ledger): update cloud observations ledger for November 5 (028339b)

## 0.17.14
- feat(registry): implement self-healing cloud device registry reconciliation (#168) (74c1806)

## 0.17.13
- docs(contracts): remediate clinical fall safety and register semantics in Inovelli parameter guide (#167) (8e26a4b)
- refactor(sensor_identity): replace natural sort key length capping with arbitrary-length digit tuple comparison (#165) (3bab3c8)
- fix(bridge): suppress closed stream logging errors on teardown in background worker (8d4ad51)
- docs(ledger): update cloud observations ledger through October 29 (7d127a2)
- docs(ledger): update cloud observations ledger through October 25 and document local CI policy (63d3d86)

## 0.17.12
- fix(registry): harden natural area sorting and child area inference (#163) (d80f53e)

## 0.17.11
- ci(workflows): disable automatic CI and Release pipeline triggers on develop (#162) (ec2f4bc)
- refactor(registry): address code review refinements for area-based device registration (#161) (5786f3a)
- fix(docs-tooling): keep verify running when the check stage cannot start (9ad6598)

## 0.17.10
- fix(bridge): guard background worker logging against closed stream errors on shutdown (#159) (5a66b8f)

## 0.17.9
- refactor(registry): extract device_sort_key_by_area and lock unicode sort ordering (#158) (3060f07)

## 0.17.8
- fix(sensor_identity): pre-index device area map and harden natural sort tie-breaking (#156) (de3663d)

## 0.17.7
- fix(sensor_identity): prevent loop variable leak in area resolution and sanitize natural sorting (#155) (453aa16)

## 0.17.6
- fix(ci): trigger pull_request workflow on develop and main branches (#154) (766822c)
- ci(release): restrict version calculation to merge and push on develop (8df42aa)
- ci(workflows): limit test runs to main PRs and run version bump only on develop (601b809)

## 0.17.5
- docs(ledger): record October 14 daily audit verification in cloud observations ledger (357a525)
- fix(security): harden credential backup and restore against unauthenticated export and SSRF (#153) (f29ec0d)

## 0.17.4
- fix(preview): enforce early preview feature gate on all MQTT Server routes (#147) (f4a6a0f)
- test(routes): improve integration test coverage for device_routes error branches (#149) (e14535b)
- test(mqtt): improve unit test coverage for mqtt command subscriber (#148) (86fc175)

## 0.17.3
- perf(bridge): avoid full entity dictionary copying on state reads (#144) (b8b5b9c)
- fix(ci): prevent script injection in branch-guard workflow by using environment variables (#142) (d3bed02)

## 0.17.2
- fix(security): address credential backup and restore security audit findings (#152) (f747635)

## 0.17.1
- test(devices): update remove selected device integration test assertion to expect expose 0 (6e48816)
- fix(devices): ensure device unexposure sets expose to false in remove workflow (a516b81)

## 0.17.0
- feat(security): harden credential backup and restore against unauthenticated exfiltration and partial writes (#151) (14f6854)
- test(services): improve unit test coverage for mqtt_state_publisher delta publishing (#150) (012d463)

## 0.16.6
- fix(ci): preserve existing release tag commit in apply_release_tag (362d404)

## 0.16.5
- fix(security): sanitize and validate interface names in Supervisor network API routes (#146) (bb39b85)

## 0.16.4
- fix(network): treat Supervisor 5xx responses as failures instead of pending (88612d4)

## 0.16.3
- fix(mqtt): reject malformed config parameter alias keys instead of falling back to parameter 0 (750510f)

## 0.16.2
- fix(mqtt): parse bracketed bitmask keys on parameter alias fields (3d670e9)

## 0.16.1
- fix(bridge): resolve live entities fallback and force bridge refresh on update (8616e71)
- ci(release): add workflow_dispatch trigger to release workflow (7f732ae)

## 0.16.0
- ci(release): increment version on develop and apply tag on main (bd09c18)
- docs(tooling): accumulate verify failures across check and links stages (410780a)
- chore(workflow): enforce develop as canonical development and PR target branch (504cbcb)
- fix(parity): resolve lexical scope leakage and default export bindings in parity guard (832fe44)
- fix(frontend): address review corrections for baseline SSE attributes and parity assertion relevance (be2c675)
- fix(frontend): address review corrections for SSE merge and parity guard (7aed245)
- fix(frontend): address review findings for pure-logic modules and parity guard (7607d82)
- feat(frontend): extract pure logic into lib modules and add Vitest suite (0436c12)
- chore(attributes): filter number slider bounds and improve test hygiene (fc6015e)
- docs: update generated options tables for slider bounds (6cd9c06)
- docs(testing): use homeassistant.local in the example UI test config (59ba668)
- test(cloud): stop the device-register test hitting the real cloud (4e38350)
- feat(mqtt): drop number entity slider bounds from published attributes (2d1c8d5)
- docs: add field installation guide pipeline (e1ea615)
- docs: add field installation guide pipeline (aaccf88)
- build(docs): installation setup guide and automated PDF generation pipeline (242789c)
- feat(network): configure a static IP via the Supervisor network API (#126) (5adecbe)
- fix(network): treat Supervisor 4xx as refusal instead of pending (30c0347)
- feat(network): configure a static IP via the Supervisor network API (#126) (a1b3d25)
- docs: editorial accuracy pass on docs/ (#93) (89f0e58)
- build(changelog): strip internal ticket references from generated customer changelogs (b6688da)
- ci(git): establish dev branch workflow and FCI ticket commit hygiene (b1deb85)
- docs(agents): document Playwright UI test suite execution and headless environment (cd102fb)
- docs: editorial accuracy pass on docs/ (#93) (6e74638)
- ci(git): establish develop branch workflow and main branch protection (7ca69f1)
- feat(ui): add Early Preview Features and hide MQTT Server behind it (ccc334d)
- docs(tooling): make verify run both stages and accumulate all failures (0e51f7f)
- test(tooling): enforce the PyYAML-free import layering, don't just assert it (#134) (08ac42b)
- docs(tooling): make the missing-dependency message work for PyYAML too (#132) (f5e7304)
- docs(tooling): gate environment variables alongside the other documented surfaces (#131) (23dc33d)
- docs(tooling): gate environment variables alongside the other surfaces (4e5f630)
- docs: automate product documentation generation and verification (137046a)
- docs(tooling): report a missing runtime dependency instead of a traceback (6705057)
- docs: automate product documentation generation and verification (18c6a82)

## 0.15.1
- fix(mqtt): trust cloud-forwarded commands, drop life-safety opt-in gate (#127) (5f267e3)

## 0.15.0
- feat(mqtt): Local Mosquitto Broker Setup and Management Interface (#125) (6665bbb)

## 0.14.2
- fix: allow config parameter writes on devices with auxiliary button entities (#119) (8e4dc1b)

## 0.14.1
- fix(ui): resolve setup wizard login spinner lockup and launch button navigation (#118) (e21a41c)

## 0.14.0
- feat(security): encrypt cloud API keys and device auth tokens at rest (#116) (4cec0bc)

## 0.13.0
- feat: Rebrand application to Care Daily Edge (#115) (4e431b2)
- feat!: key config_parameters by the device catalog's own parameter string (#113) (296ff2c)

## 0.12.4
- sec: enforce a shared command deny-list on the MQTT and HTTP control paths (#112) (1014a6e)

## 0.12.3
- fix: make the devices table rebuild atomic against a crash (#107) (338e6c7)

## 0.12.2
- fix: normalize db path comparison to prevent false orphan warnings (#106) (8e25b86)
- ci: stop concurrent release runs from double-publishing a version (#105) (b4c489d)

## 0.12.1
- fix: cap cloud_log retention so the database stops growing without bound (#103) (c36b2f2)
- fix: honor the db_path add-on option instead of silently ignoring it (#102) (89f1dc7)

## 0.12.0
- feat: add CSRF protection to every state-changing endpoint (#104) (18ede0f)

## 0.11.0
- feat(ui): brand-aligned CSS token layer (Phase 1, #96) (#101) (511e2ea)

## 0.10.0
- feat: Expose Z-Wave device configuration parameters to cloud via MQTT (#88) (ff0fa04)

## 0.9.6
- fix: filter unmapped device parameter noise and correct publish-path inconsistencies (#89) (bf471b7)

## 0.9.5
- fix(security): harden the add-on container image (d8cd281)
- chore: disable default direct access port mapping for Web UI in config (#61) (f091903)
- chore: update GitHub Actions to latest versions and remove deprecated Node.js environment variable (726ed42)

## 0.9.4
- chore: update CI workflows to install dependencies from requirements-dev.txt (8577145)
- fix: changing cloud doesn't properly re-register device (#57) (c1ff725)

## 0.9.3
- fix: bug requesting login code (#56) (5d1b786)

## 0.9.2
- fix: Device filtering to remove noisy device updates (#52) (736e419)

## 0.9.1
- refactor: normalizing device sensors and optimizing command queues (12b79ff)

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

