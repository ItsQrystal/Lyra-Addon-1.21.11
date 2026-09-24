# AGENTS.md

## Project overview
This repo is a Fabric mod add-on for Meteor Client, focused on creative-mode utilities and server automation. The main entry point is [src/main/java/com/lyra/addon/Addon.java](src/main/java/com/lyra/addon/Addon.java), with feature modules under [src/main/java/com/lyra/addon/modules](src/main/java/com/lyra/addon/modules), commands under [src/main/java/com/lyra/addon/commands](src/main/java/com/lyra/addon/commands), and shared helpers under [src/main/java/com/lyra/addon/utils](src/main/java/com/lyra/addon/utils).

Use the existing project docs as the source of truth: [README.md](README.md) and [src/main/resources/fabric.mod.json](src/main/resources/fabric.mod.json).

## Build and validation
- Build the mod with: `./gradlew build`
- This project targets Java 21 and uses Fabric Loom + Meteor Client.
- Mod metadata and version info are declared in [build.gradle](build.gradle) and [gradle.properties](gradle.properties).

## Code conventions
- Keep new functionality aligned with the package layout already used by the project.
- Prefer adding new features as a module under `com.lyra.addon.modules` when they are user-facing toggles or behaviors.
- Put command handlers under `com.lyra.addon.commands` and shared logic under `com.lyra.addon.utils`.
- Do not introduce unrelated frameworks, dependency injection patterns, or broad refactors without a clear reason.
- Match the repo’s existing naming and style: class names in PascalCase, package names lower-case, and Meteor/Fabric API usage already present in the codebase.

## When changing code
- Read the relevant module or command class before editing nearby code.
- Preserve existing registration patterns and metadata wiring in `Addon.java`.
- Prefer minimal, local fixes over rewrites.
- Keep compatibility with the project’s Fabric + Meteor target versions in [gradle.properties](gradle.properties).

## Important notes
- This is not a generic Java app; it is a Minecraft client mod and should be treated like one.
- Avoid assumptions about vanilla Minecraft APIs outside the Fabric/Meteor environment already used by the project.
