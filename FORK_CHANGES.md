# Fork changes

Sonaro is a hard fork of [Auxio](https://github.com/OxygenCobalt/Auxio) that keeps merging
upstream. To keep those merges cheap, every edit to a file that also exists upstream is:

1. marked in place with a `FORK:` comment (`// FORK: ...` in Kotlin/Gradle/C++,
   `<!-- FORK: ... -->` in XML, `# FORK: ...` in YAML/properties), and
2. listed in this file with the reason.

When an upstream merge conflicts, this list is what gets re-applied. Files that exist only
in Sonaro are not listed here. Add rows at the end of the table of the section you are
working on.

## Branding (name, icon, applicationId)

| File | Change | Why |
|------|--------|-----|

## Build flavors (foss / gms)

| File | Change | Why |
|------|--------|-----|

## CI

| File | Change | Why |
|------|--------|-----|
| `.github/workflows/android.yml` | Runs for pull requests and `main` only, with concurrency and read-only permissions. Setup steps replaced by the shared `.github/actions/setup-android-build` action. `packageDebug` -> `:app:assembleDebug`, APKs uploaded by glob as `Sonaro_Canary`. Actions moved to their current major versions. | Upstream ran on every branch push (two runs per pull request) and used deprecated Node 20 actions. `assembleDebug` and the glob keep working once foss/gms flavors exist. |
| `.github/workflows/lint.yml` | Same triggers and shared setup, so it builds with JDK 21 instead of 17. Adds the app's unit tests (through `.github/ci.init.gradle`) and Android lint (`:app:lint`), and uploads reports when a check fails. | Upstream used a different JDK than the build needs, tested only `musikr`, and never ran Android lint. |
| `app/build.gradle` | `lint { baseline = file("lint-baseline.xml") }` added at the end of the `android` block. | Upstream never ran Android lint and its code has 64 errors and 79 warnings (mostly the vendored Material bottom sheet backport). `app/lint-baseline.xml` records them so CI fails only on new issues. Regenerate with `./gradlew :app:updateLintBaseline`. |
