# ApexOS Community Add-ons: Bashio

[![GitHub Release][releases-shield]][releases]
![Project Stage][project-stage-shield]
[![License][license-shield]](LICENSE.md)

[![GitHub Actions][github-actions-shield]][github-actions]
[![OpenSSF Scorecard][scorecard-shield]][scorecard]
[![Coverage on codecov][codecov-shield]][codecov]
![Project Maintenance][maintenance-shield]
[![GitHub Activity][commits-shield]][commits]

[![Discord][discord-shield]][discord]

[![Sponsor Frenck via GitHub Sponsors][github-sponsors-shield]][github-sponsors]

[![Support Frenck on Patreon][patreon-shield]][patreon]

## About

Bashio is a bash function library for use with ApexOS apps.

It bundles commonly used operations so apps can include it instead of
duplicating code, making them easier to develop and maintain.

Main goals:

- Reduce the number of operations needed in apps.
- Reduce the amount of code needed in apps.
- Make app code more readable.
- Provide a trusted and tested code base.

This speeds up app development by letting you focus on the app's
logic rather than boilerplate.

## Installation

The library is installed in the ApexOS Community Add-ons base images and
the official ApexOS base images.

Currently available base images:

- [ApexOS Community Add-ons Alpine Base Image][base-alpine]
- [ApexOS Community Add-ons Alpine Python Base Image][base-alpine-python]
- [ApexOS Community Add-ons Debian Base Image][base-debian]
- [ApexOS Community Add-ons Ubuntu Base Image][base-ubuntu]
- [Official ApexOS Alpine Docker Base Image][apexos-base]
- [Official ApexOS Alpine Python Docker Base Image][apexos-base]
- [Official ApexOS Debian Docker Base Image][apexos-base]
- [Official ApexOS Raspbian Docker Base Image][apexos-base]
- [Official ApexOS Ubuntu Docker Base Image][apexos-base]

Using those images as the base for your ApexOS app will provide this
function library out of the box. Our base images are updated frequently and
provide the minimal needed base image for a great app.

If you want to add Bashio to your own images, please take a look at the
Dockerfile of the above base images to see how they are added at build time.

## Configuration

Configuring a Bash script to use the Bashio library is fairly easy. Simply
replace the shebang of your script file, from `bash` to `bashio`.

Before example:

```bash
#!/usr/bin/env bash
set -e

CONFIG_PATH=/data/options.json

USERNAME=$(jq --raw-output '.username // empty' $CONFIG_PATH)

echo "${USERNAME}"
```

After example with Bashio:

```bash
#!/usr/bin/env bashio

USERNAME=$(bashio::config 'username')

bashio::log.info "${USERNAME}"
```

## Functions

Bashio has more than 450 functions available: communicating with
the Supervisor API, Have I Been Pwned, file system, logging, configuration handling
and a lot more!

The best way to get around would be by looking at the different modules
available in the [`lib`](lib) folder. Each module has its own file, and each
function has been documented inside the codebase.

Furthermore, Bashio is used by the
[ApexOS Community Add-ons project][repository], those apps will be
a great resource of practical examples.

### Deprecation: `addon` renamed to `app`

Add-ons have been rebranded to apps, so the `bashio::addon.*` functions
(and `bashio::addons` / `bashio::addons.*`) have been renamed to
`bashio::app.*` (and `bashio::apps` / `bashio::apps.*`).

The old names still work: each keeps a deprecated alias that delegates to
its new counterpart and logs a warning the first time it is used. Please
migrate to the `app` names; for example, replace `bashio::addon.name`
with `bashio::app.name`. The aliases may be removed in a future release.

## Known issues and limitations

- Some parts of the Supervisor API are not implemented yet.

## Changelog & Releases

This repository keeps a change log using [GitHub's releases][releases]
functionality. The format of the log is based on
[Keep a Changelog][keepchangelog].

Releases are based on [Semantic Versioning][semver], and use the format
of `MAJOR.MINOR.PATCH`. In a nutshell, the version will be incremented
based on the following:

- `MAJOR`: Incompatible or major changes.
- `MINOR`: Backwards-compatible new features and enhancements.
- `PATCH`: Backwards-compatible bugfixes and package updates.

## Support

Got questions?

You have several options to get them answered:

- The [ApexOS Community Add-ons Discord chat server][discord] for app
  support and feature requests.
- You could also [open an issue here][issue] GitHub.

## Contributing

This is an active open-source project. We are always open to people who want to
use the code or contribute to it.

We have set up a separate document containing our
[contribution guidelines](.github/CONTRIBUTING.md).

Thank you for being involved! :heart_eyes:

## Authors & contributors

The original setup of this repository is by [Franck Nijhof][frenck].

For a full list of all authors and contributors,
check [the contributor's page][contributors].

## License

MIT License

Copyright (c) 2019-2026 Franck Nijhof

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

[codecov-shield]: https://codecov.io/gh/apexinfosysindia/bashio/branch/main/graph/badge.svg
[codecov]: https://codecov.io/gh/apexinfosysindia/bashio
[commits-shield]: https://img.shields.io/github/commit-activity/y/apexinfosysindia/bashio.svg
[commits]: https://github.com/apexinfosysindia/bashio/commits/main
[contributors]: https://github.com/apexinfosysindia/bashio/graphs/contributors
[discord-shield]: https://img.shields.io/discord/478094546522079232.svg
[frenck]: https://github.com/frenck
[github-actions-shield]: https://github.com/apexinfosysindia/bashio/workflows/CI/badge.svg
[github-actions]: https://github.com/apexinfosysindia/bashio/actions
[github-sponsors-shield]: https://frenck.dev/wp-content/uploads/2019/12/github_sponsor.png
[github-sponsors]: https://github.com/sponsors/frenck
[apexos-base]: https://github.com/apexinfosysindia/docker-base
[issue]: https://github.com/apexinfosysindia/bashio/issues
[keepchangelog]: http://keepachangelog.com/en/1.0.0/
[license-shield]: https://img.shields.io/github/license/apexinfosysindia/bashio.svg
[maintenance-shield]: https://img.shields.io/maintenance/yes/2026.svg
[patreon-shield]: https://frenck.dev/wp-content/uploads/2019/12/patreon.png
[patreon]: https://www.patreon.com/frenck
[project-stage-shield]: https://img.shields.io/badge/project%20stage-experimental-yellow.svg
[releases-shield]: https://img.shields.io/github/release/apexinfosysindia/bashio.svg
[releases]: https://github.com/apexinfosysindia/bashio/releases
[scorecard-shield]: https://api.scorecard.dev/projects/github.com/apexinfosysindia/bashio/badge
[scorecard]: https://scorecard.dev/viewer/?uri=github.com/apexinfosysindia/bashio
[semver]: http://semver.org/spec/v2.0.0
