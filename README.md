# mediawiki_extension
Ansible role for installing MediaWiki extensions via Composer or tar.gz archives.

Compatible with https://github.com/robertdebock/ansible-role-mediawiki

## Usage

| Variable | Type | Description | Default | Example
|---|---|---|---|---
| `mediawiki_extension_name` | String | Name of the extension used during registration in LocalSettings | | `Mermaid`
| `mediawiki_extension_registration_type` | String | One of "wfLoadExtension", "require_once" | wfLoadExtension | `wfLoadExtension` 
| `mediawiki_extension_install_type` | String | One of "composer" or "tar" | composer | `composer`
| `mediawiki_extension_strip_components` | Integer | Strip NUMBER leading components from file names on extraction | 1 |
| `mediawiki_extension_disabled` | Boolean | Decide, if the extension shall be installed but disabled (commented out) | false | `false`
| `mediawiki_extension_source` | String | | composer: name on packagist.org |  `mediawiki/mermaid`
| `mediawiki_extension_source_version` | String | The extension version as used by the source | | `3.0.1`
| `mediawiki_extension_config` | String | Any extension specific configuration that should be added to LocalSettings after extension registration |

## Examples

**Composer**
```yaml
- name: install Mermaid extension
  include_role:
    name: gesinnit.mediawiki_extension
  vars:
    mediawiki_extension_name: "Mermaid"
    mediawiki_extension_install_type: "composer"
    mediawiki_extension_disabled: false
    mediawiki_extension_source: "mediawiki/mermaid"
    mediawiki_extension_source_version: "2.1.0"
```

**TAR**
```yaml
- name: install AdminLinks extension
  include_role:
    name: gesinnit.mediawiki_extension
  vars:
    mediawiki_extension_name: "AdminLinks"
    mediawiki_extension_install_type: "tar"
    mediawiki_extension_disabled: false
    mediawiki_extension_source: "http://gitlab.local.gesinn.it/mediawiki-extension/AdminLinks/repository/archive.tar.gz?ref=0.4"
```

## Versioning
We use [SemVer](http://semver.org/) for versioning. For the versions available, see the [tags on this repository](https://github.com/gesinn-it/QRLite/tags). 

## Author(s)
* Alexander Gesinn (gesinn.it GmbH & Co. KG)
