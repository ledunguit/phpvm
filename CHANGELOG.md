# Release Notes

## [v1.3.0](https://github.com/Thavarshan/phpvm/compare/v1.2.0...v1.3.0) - 2025-05-11

## Added

- Added `system` command to easily switch back to system PHP version
- Added timestamps to all log messages for better traceability and debugging
- Added log levels (INFO, ERROR, WARNING, DEBUG) for more structured logging
- Added `run_with_sudo` helper function to centralize sudo usage logic
- Added comprehensive self-tests with `phpvm test` command
- Added test for corrupted `.phpvmrc` file handling
- Added better support for detecting and using latest PHP version from Homebrew
- Added improved error messages with more detailed information
- Added ability to run self-tests with `phpvm test` command
- Added debugging capability via `DEBUG=true` environment variable

## Changed

- Changed logging format to include timestamps and log levels
- Changed sudo handling to use a centralized helper function
- Changed path expansion to use `$HOME` instead of tilde notation for better compatibility
- Changed error handling to provide more descriptive and actionable messages
- Changed test framework to be integrated directly into the script
- Changed help message to include information about the `test` command
- Improved bash/zsh shell compatibility with better sourcing logic
- Improved code organization and reduced duplication with helper functions

## Fixed

- Fixed shell crash issue when sourcing in zsh with p10k theme
- Fixed path expansion issues in Ubuntu bashrc configurations
- Fixed missing system PHP switching functionality on macOS
- Fixed detection of latest PHP version on macOS when installed via Homebrew's generic 'php' formula
- Fixed potential sudo permission issues on Linux by using `run_with_sudo` consistently
- Fixed auto-switching edge case with invalid or corrupted `.phpvmrc` files
- Fixed script execution issues when sourced from shell initialization files
- Fixed various edge cases in version detection and switching

## [v1.2.0](https://github.com/Thavarshan/phpvm/compare/v1.1.0...v1.2.0) - 2025-02-15

### Added

- **GitHub Actions CI/CD Integration:** Added workflows for running automated tests and verifying PHPVM functionality on macOS and Linux.
- **Linux Compatibility:** Implemented Homebrew mock support to allow testing on both macOS and Linux environments.
- **Extended Test Suite:** Improved BATS test coverage to handle different system environments and dependencies.

### Changed

- **Improved Homebrew Detection:** The script now properly checks for Homebrew availability and handles missing installations more gracefully.
- **Refactored Test Setup:** The `setup` function in `test_phpvm.bats` now ensures correct sourcing of `phpvm.sh` and mocks Homebrew on Linux.
- **Better Error Messages:** Adjusted error outputs for clarity when Homebrew or PHP versions are unavailable.

### Fixed

- **Fixed Ubuntu Compatibility Issues:** The tests no longer fail due to missing Homebrew; instead, they mock Homebrew behavior on Linux.
- **Resolved Test Failures:** The `install_php`, `use_php_version`, and `auto_switch_php_version` tests now properly execute across different OS platforms.
- **Prevented Test Cleanup Failures:** The `teardown` function now ensures `.phpvmrc` and other temporary files are removed only if they exist.

## [v1.1.0](https://github.com/Thavarshan/phpvm/compare/v1.0.0...v1.1.0) - 2025-02-09

### Added

- Added comprehensive error handling to the main `phpvm` script for robust operations.
- Added checks for command availability (e.g., `curl`) in the installation script.
- Added a suite of unit tests using BATS for automated testing of core functionalities.
- Added clear and informative, color-coded terminal messages for user interactions.

### Changed

- Enhanced the installation script to safely modify user shell profiles and avoid duplicate entries.
- Updated the main `phpvm` script to use strict mode (`set -euo pipefail`) for improved reliability.
- Improved overall error reporting to capture and relay issues during directory creation, downloading, and setting file permissions.

### Fixed

- Fixed various shellcheck warnings such as:
  - SC2034 (unused variables)
  - SC2086 (unquoted variables)
  - SC2155 (variable declaration and assignment in one line)
  - SC2128 (incorrect array handling)
- Fixed potential issues with word splitting and globbing by ensuring proper quoting of variables in command calls.

## [v1.0.0](https://github.com/Thavarshan/phpvm/compare/v0.0.1...v1.0.0) - 2025-02-04

### Added

- Auto-switching PHP versions based on `.phpvmrc`.
- Improved support for macOS Homebrew installations.
- Enhanced installation script for easy setup using `curl` or `wget`.
- More robust error handling and output formatting.
- Extended compatibility with `bash` and `zsh` shells.

### Fixed

- Resolved issues with Homebrew PHP detection on macOS.
- Prevented terminal crashes due to incorrect sourcing in shell startup scripts.
- Improved handling of missing PHP versions.

## [v0.0.1](https://github.com/Thavarshan/phpvm/compare/v0.0.0...v0.0.1) - 2024-10-05

Initial release for public testing and feedback.
