# Versioning

Use the repository's declared version as the release source of truth.

For SemVer-like versions:

- `Version` is the authoritative application version.
- `v<Version>` is the default Git tag convention unless the repository defines another prefix.
- A pre-release suffix may be preserved when the repository intentionally uses one.
- Existing tags are immutable for release purposes; bump the version instead of overwriting a tag.
