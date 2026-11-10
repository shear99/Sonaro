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
