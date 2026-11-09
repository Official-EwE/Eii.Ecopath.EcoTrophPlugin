# Eii.Ecopath.EcoTrophPlugin

Ecotroph plug-in for EwE

## Package

- **Package ID:** `Eii.Ecopath.EcoTrophPlugin`
- **License:** EUPL-1.2
- **Icon:** `EII_plain_128x128.png`

The package automatically places `EwEEcoTrophPlugin.dll` and its accompanying symbols and XML documentation (when copied) in `Plugins\EcoTrophPlugin\` beneath the consuming project's build output. SDK-style publish output uses the same layout, including publishing with `--no-build`. PackageReference consumers also inherit these rules through transitive package references.

Dependencies keep their normal output locations. The host must load the plugin from this subdirectory; installing the package does not configure assembly probing. The NuGet cache layout is unchanged.

## Build

Build the solution on Windows with the .NET SDK and .NET Framework 4.8 targeting pack:

``powershell
dotnet build .\Eii.Ecopath.EcoTrophPlugin.slnx --configuration Release
``

Create a local NuGet package with:

```powershell
dotnet pack .\EcoTrophPlugin\EwEEcoTrophPlugin.vbproj --configuration Release --output .\nuget /p:PackageVersion=1.0.0
```

Packages are versioned by GitVersion in CI. The `Eii.*` dependencies require access to the Ecopath International Initiative GitHub Packages feed.

## CI/CD

The `master` branch is protected and requires pull requests to merge. Pull requests must pass the build check. Merges to `master` publish the NuGet package.