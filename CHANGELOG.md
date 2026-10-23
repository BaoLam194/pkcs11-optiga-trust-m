## [2.26.0] - 2026-10-23
* Add ECC, RSA support for OpenSSL Provider interface
* OpenSSL Engine and Provider now support ECC256/384/521 and RSA1024/2028
* Upgrade submodule to v5.8.3, change API from MbedTLS 2.x to PSA API 1.x

## [2.25.0] - 2026-01-23
* Added RSA1024/2048 support for PKCS11 tools and OpenSSL Engine interface
* Added ECC256 support for OpenSSL Engine interface

## [2.24.1] - 2024-11-29
* Changed Hardware in which build was running
* Fixes the release package.

## [2.24.0] - 2024-08-21
* Fixed the GPIO issue for the latest RPI OS Kernel 6.6 by using libgpiod
* Fixed segmentation fault for sign and verify functions under error conditions

## [2.23.0] - 2024-06-24
* Update README.md and images
* Update/adjust repository to adapt to hostlib v5.0.0
* Fix submodule and installation scripts
* AWS Python examples improvement and release mode codes updates
* Added a release script
* Added Blackduck scan via GitLab CI
* First release 2.x
