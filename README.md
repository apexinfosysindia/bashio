# Bashio

Bashio is a bash function library used by ApexOS add-ons and base images.

It provides a set of commonly used operations for add-on shell scripts:
logging, configuration access, service discovery, and a jq-based client
for the ApexOS Supervisor API.

## Usage

The library is installed into ApexOS base images at `/usr/lib/bashio`
(with `/usr/bin/bashio` as the entry point). Add-on scripts source it via
the shebang:

```bash
#!/usr/bin/env bashio
```

## Versioning

Tags follow the upstream library versioning (`v0.17.5`). Base images pin
the version via the `BASHIO_VERSION` build argument and fetch the release
archive of this repository at build time.
