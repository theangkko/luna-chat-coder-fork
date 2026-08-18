# Luna Chat Coder entry point

When substantial repository development is performed from a chat surface with a disposable or sandboxed code-execution environment, read `.agents/skills/luna-chat-coder/SKILL.md` before making substantial changes.

Loading the skill is a readiness step, not a reason to use GitHub Actions. Normal engineering work should stay in the chat sandbox work container when it is available and sufficient.

The repository itself defines its runtimes, services, dependencies, architecture, build system, and verification requirements. Luna Chat Coder supplies continuity and missing execution capability; it does not introduce a development methodology or substitute technologies merely because they are easier to run.

Treat exact GitHub commit and PR state as durable source truth, preserve unrelated work, and do not make access to the user's computer a dependency of the workflow.

When this repository is used as a template, keep this entry point and add the project's own engineering instructions alongside it.

## Optional template CI baseline

This template also provides `.github/workflows/dotnet-ci.yml` as a reusable baseline for downstream .NET repositories. When a downstream repository contains a .NET solution/project, the workflow uses .NET SDK 10.0.400 to restore, build, and run conventional `*Tests.csproj` / `*Test.csproj` projects on Windows. A second job publishes a Windows x64 self-contained artifact after the build/test job succeeds.

The workflow is template infrastructure, not a requirement imposed by Luna. A downstream repository may replace or remove it when the project's own runtime, build, test, deployment, or security requirements call for a different CI design. The important reusable pattern is evidence-based CI with explicit build/test/publish boundaries and durable artifacts.