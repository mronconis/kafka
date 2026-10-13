# Changelog

All notable changes to the `saiello.kafka` Ansible collection will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/).

## [0.0.11] - 2026-10-13

### Added

- Add support to install and configure Kafka Connect cluster ([#18](https://github.com/mronconis/kafka/issues/18))
- Create/update/delete connector via REST API
- Deploy connect plugins
- Add connect security configs

### Fixed

- Fix connect configurations
- Fix molecule connect scenario
- Fix molecule/connect podman name resolution
- Refactor some molecule scenarios
- Fix KRaft override kafka_server_properties_file var
- Fix KRaft broker format storage options
- Fix galaxy conf
- Fix ansible lint conf
- Fix too many blank lines
- Fix too many blank lines and too many spaces

## [0.0.10] - 2026-10-06

### Added

- Add CI and release workflows
- Add migration support from ZooKeeper to KRaft with role and test adjustments
- Add auto-discovery kafka_home in verify
- Add systemd after configuration

### Fixed

- Update README.md links
- Review some variables and their controls
- Fix template
- Fix plugin minor changes
- Improve migration procedure
- Add controller default vars
- Fix molecule minor changes

## [0.0.9] - 2026-07-27

### Added

- Add upgrade playbook
- Add verify playbook
- Add support for Kafka in KRaft mode
- Add support for Cruise Control
- Add local archive dir conf

### Fixed

- Fix TLS admin client configuration in plugin
- Add minor update changes
- Rename handlers to avoid collisions
- Fix setup admin

## [0.0.8] - 2025-07-25

### Added

- Add support for Kafka in KRaft mode

### Fixed

- Fix molecule tests

## [0.0.7] - 2024-06-13

### Added

- Add new versions of Kafka and AMQ Streams in the catalog
- Add AMQ Streams 2.6.0

## [0.0.6] - 2023-10-04

### Added

- Add authentication to admin client
- Add support to AMQ Streams versions 2.4, 2.5 and related upstream versions

### Fixed

- Fix ansible lint warnings

## [0.0.5] - 2023-05-11

### Added

- Add support for ZooKeeper quorum Kerberos integration

### Fixed

- Add default value when TLS and authz are not set

## [0.0.4] - 2023-04-17

### Added

- Integrate server configuration generator for OAuth and Kerberos
- Add a new version of Kafka and AMQ Streams
- Add separate versions catalog for Kafka and AMQ Streams
- Support server.properties as YAML configuration
- Add implementation for download the AMQ Streams tarball from Red Hat CSP

### Changed

- Simplify interface according to the catalog
- Update readme

### Fixed

- Fix var name __admin_config
- Set property snapshot.trust.empty to false as default value
- Fix user and group on kafka_home

## [0.0.3] - 2022-09-21

### Added

- Allow using a custom server.properties template
- Add day-2 playbooks
- Add a Vagrant example

### Fixed

- Fix become issue when running with non-root user

## [0.0.2] - 2022-08-10

### Added

- Add ansible-lint

## [0.0.1] - 2022-08-09

### Added

- Add galaxy files
- Add readme files
- Add LICENSE
- Add support to ZooKeeper and Kafka clusters
- Add kafka_systemd_broker role
- Add kafka_systemd_zookeeper role
- Add kafka_install role
