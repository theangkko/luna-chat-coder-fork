---
name: release-engineering
description: Standardize verified versioned releases from repository-defined version metadata through build, test, publish, tag, and GitHub Release.
license: MIT
metadata:
  version: "0.1.0"
---

# Release Engineering

Use this skill when creating a repository release or designing a release workflow.

## Release sequence

```text
read repository-defined version
  -> validate version/tag
  -> restore/build
  -> test
  -> publish
  -> validate artifact
  -> create tag at exact verified commit
  -> create GitHub Release
  -> attach artifact
```

Never create a release before required build and test checks pass. Never overwrite an existing version tag.

## Version source

The repository decides where the version comes from. Prefer a single authoritative project metadata source such as a `.csproj` `<Version>` rather than duplicating the version in workflow YAML.

## Artifact evidence

Validate that the expected artifact exists, has the expected target/runtime, and is non-empty before publishing it. Keep the workflow artifact and release asset naming deterministic.

## Exact target

The Release must point to the exact commit that passed verification. Do not silently move a mutable branch between verification and publication.
