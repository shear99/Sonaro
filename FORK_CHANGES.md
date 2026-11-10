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
| `app/build.gradle` | `applicationId` is `"app.sonaro"` instead of `namespace`. | Sonaro installs as its own app next to Auxio. `namespace` and the Kotlin packages stay `org.oxycblt.auxio`. |
| `app/src/main/res/values/donottranslate.xml`, `app/src/debug/res/values/donottranslate.xml` | `info_app_name` is `Sonaro` / `Sonaro Debug`. `pkg_authority_cover` uses the `app.sonaro` / `app.sonaro.debug` IDs. | App label. The provider authority must equal the application ID + `.image.CoverProvider` (see `CoverProvider.AUTHORITY`) and be unique on the device. |
| `app/src/main/java/org/oxycblt/auxio/Auxio.kt` | The copyleft-notice logger treats `app.sonaro` and `app.sonaro.debug` as the official IDs. | With upstream's IDs in the check, every log line of a Sonaro build is replaced by the notice. |
| `app/src/main/java/org/oxycblt/auxio/settings/AboutFragment.kt`, `app/src/main/res/layout/fragment_about.xml` | Source and issue links point at Sonaro. The author card is headed "Based on Auxio" and gains a row linking to upstream. The supporters card and the feedback email row are hidden. The icon's content description is the app name. | Credits Auxio and its author without presenting them as Sonaro's maintainers, and keeps Sonaro feedback away from upstream's tracker and mailbox. |
| `app/src/main/java/org/oxycblt/auxio/home/ErrorDetailsDialog.kt` | The bug report link opens Sonaro's issue form, with no assignee. | Sonaro crashes must not land in Auxio's tracker. |
| `app/src/main/java/org/oxycblt/auxio/tasker/Start.kt` | The Tasker blurb replaces "Auxio" with the app name at runtime. | `lng_tasker_start` names Auxio in every translation. Editing them all would conflict with upstream translation updates. |
| `app/src/main/res/values-ja/strings.xml` (`lbl_about`), `app/src/main/res/values-nn/strings.xml` (`set_rewind_prev_desc`, `set_task_exit_desc`) | "Auxio" replaced with "Sonaro". | The only other translated strings on screen that name the app. On conflict, take upstream's line and replace the name again. |
| `app/src/main/res/drawable/ic_launcher_foreground.xml`, `ic_launcher_background.xml`, `ic_splash_anim.xml`, `ic_auxio_24.xml`, `app/src/main/res/mipmap-*/ic_launcher.webp` | Redrawn as the Sonaro icon (tuning fork with resonance arcs, teal on `#121212`). | Own icon. File names are unchanged so the manifest, notification, widget and Android Auto references stay as upstream has them. |
| `fastlane/metadata/android/en-US/images/icon.png`, `featureGraphic.png`, `fastlane/metadata/android/{en-US,ko}/full_description.txt` | Sonaro icon, feature graphic and description. | Store listing. The other locales' descriptions still say Auxio. Before a store release run `sed -i 's/Auxio/Sonaro/g' fastlane/metadata/android/*/full_description.txt` and review `ar-IQ`, `ar-SA` and `he`, which do not use the Latin name. |
| `README.md`, `.github/CONTRIBUTING.md`, `.github/ISSUE_TEMPLATE/*.yml`, `.github/PULL_REQUEST_TEMPLATE.md` | Sonaro name and links, credit to Auxio, no default assignee on issue forms. | Repository front matter. On conflict keep Sonaro's version and port upstream's wording changes by hand. |
| `.github/FUNDING.yml` | Deleted. | It put a Sponsor button for upstream's author on Sonaro's repository. The README credits section links to it instead, labeled as supporting Auxio. |

Deliberately left as upstream has them, so they are not changes: the Kotlin package and class names
(`org.oxycblt.auxio`, `Auxio`, `AuxioService`), resource and style names (`Theme.Auxio.*`,
`ic_auxio_24`, `desc_auxio_icon`), `rootProject.name`, the per-file license headers, the
`org.oxycblt.auxio` namespace inside music UIDs (a data format shared with Auxio playlists), and
`versionName` / `versionCode`.

## Build flavors (foss / gms)

| File | Change | Why |
|------|--------|-----|

## CI

| File | Change | Why |
|------|--------|-----|
