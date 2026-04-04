# Changelog
All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

## [8.0.0] - 2026-04-04
### Added
- `persistence.config.override` (default: `false`) — set to `true` to keep Helm authoritative over config, always overwriting `config.yml` on pod start (e.g. for GitOps workflows). Replaces `ephemeralWritableConfigYaml`.
- Input validation: `helm install/upgrade` now fails with a clear error if `persistence.config.override: true` is set without `persistence.config.enabled: true`.
### Changed
- `persistence.config.enabled: true` now seeds `config.yml` from Helm values only if the file does not already exist, allowing Frigate's UI to manage configuration persistently across pod restarts and Helm upgrades. This aligns the chart with the Docker Compose installation model.
- The `checksum/configmap` pod annotation is suppressed when `persistence.config.enabled: true` (without `override`), preventing unnecessary pod restarts when `values.config` changes in Helm.
### Removed
- `persistence.config.ephemeralWritableConfigYaml` — replaced by `persistence.config.override`.

## [6.3.1] - 2022-05-27
### Fixed
- Frigate container no longer hard-coded to run as root
- README errors
### Updated
- `securityContext` now configurable
- Frigate to `v0.10.1`

## [6.3.0] - 2022-01-05
### Added
- CHANGELOG
- ReadMe template to be utilized by helm-docs
### Updated
- Documentation
### Removed
- `replicaCount` configuration option as this is not supported >1

## [6.2.0] - 2022-01-05
### Updated
- added helper function to allow imageTag to be pulled from appVersion
