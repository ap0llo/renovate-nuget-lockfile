# Renovate NuGet Lock File example

This repository demonstrates the handling of NuGet package lock files in [renovate](https://github.com/renovatebot/renovate).

Currently, package lock files are not updated if the package reference is defined in a included MSBuild file (like `Directory.Build.props`).

This repository references two packages

- Newtonsoft.Json is referenced in `Application/Application.csproj`
- Microsoft.Extensions.Logging.Abstractions is referenced in `Directory.Build.props`

When renovate updates these packages, the lock file at `Application\packages.lock.json` is only updated in one case as can be seen in the following PRs created by renovate:

- [#4 (Updates Newtonsoft.Json)](https://github.com/ap0llo/renovate-nuget-lockfile/pull/4): `packages.lock.json` is updated as expected
- [#3 (Updates Microsoft.Extensions.Logging.Abstractions)](https://github.com/ap0llo/renovate-nuget-lockfile/pull/3): Reference is updated but `packages.lock.json` is not

For the corresponding discussion, see https://github.com/renovatebot/renovate/discussions/26065