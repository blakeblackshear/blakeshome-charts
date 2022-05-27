# Changelog
All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

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
