# Failure classification

Use the smallest accurate class before choosing a fix.

| Class | Typical evidence | First response |
|---|---|---|
| Workflow/runtime | action runtime deprecation, runner/setup failure | update workflow/runtime configuration |
| Dependency/SDK | restore, package, SDK mismatch | inspect declared versions and lock state |
| Compile/build | compiler or linker errors | inspect exact source and package APIs |
| Test/fixture | assertion, generated fixture, harness failure | verify semantic expectation and fixture validity |
| Product logic | integration test exposes incorrect output | fix production implementation and add regression coverage |
| Packaging/publish | missing executable/artifact, publish validation failure | inspect publish settings and artifact contents |
| Permissions/policy | token, environment, branch or release permission failure | inspect GitHub policy and required permissions |
