# Reusable .NET CI baseline

This template includes `.github/workflows/dotnet-ci.yml` for downstream .NET repositories created with **Use this template**.

## What it does

The workflow is intentionally explicit about verification boundaries:

```text
.NET 10.0.400
    -> Restore
    -> Build
    -> Test
    -> Windows x64 Publish
    -> Published-output validation
    -> Artifact
```

The build/test job runs automatically when the repository contains a .NET solution, project, or `global.json`. It looks for a solution first and otherwise uses the first project it finds.

Tests are automatically discovered using the conventional `*Tests.csproj` and `*Test.csproj` naming patterns. Projects without a conventional test project still get build verification.

After Build and Test succeeds, the Windows x64 publish job creates a self-contained single-file publish and uploads it as `dotnet-win-x64`.

## Action versions

The baseline uses the current Node 24-based major versions:

- `actions/checkout@v7`
- `actions/setup-dotnet@v6`
- `actions/upload-artifact@v6`

The .NET SDK is pinned to `10.0.400` for deterministic CI. NuGet caching is disabled by default so a downstream template clone does not require a `packages.lock.json` file just to start CI.

## Customization boundary

This workflow is a template baseline, not a mandatory Luna development methodology. A downstream repository can replace or remove it when the repository's own build, test, deployment, security, or runtime requirements differ.

For a project-specific workflow, keep the useful structure—explicit Restore, Build, Test, Publish, validation, and artifact boundaries—and change the project selection, runtime, SDK, and publish commands to match the project.
