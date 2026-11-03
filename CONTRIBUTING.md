# Contributing

Thanks for considering a contribution to Clipth.

The most useful contributions are focused, reproducible, and mindful that this app stores sensitive local clipboard data.

## Development Setup

Requirements:

- macOS 14.0 or later
- Xcode 16.0 or later recommended
- Swift toolchain included with Xcode

Open the project:

```bash
open Clipth.xcodeproj
```

Build from the command line:

```bash
xcodebuild \
  -project Clipth.xcodeproj \
  -scheme Clipth \
  -configuration Debug \
  -destination 'platform=macOS' \
  -derivedDataPath build \
  -skipMacroValidation \
  CODE_SIGN_IDENTITY="-" \
  CODE_SIGNING_REQUIRED=NO \
  CODE_SIGNING_ALLOWED=NO \
  build
```

## Code Signing

Local development can use unsigned builds with `CODE_SIGNING_ALLOWED=NO`, as in the command above.

Public releases use a stable self-signed certificate (`Clipth Self-Signed`) so macOS keeps Accessibility permission across rebuilds and updates. Without a stable signing identity, that permission can be invalidated after each build even when the System Settings toggle still appears enabled. The certificate is self-signed, not a Developer ID, so the first launch can still show a Gatekeeper warning. See the Install section in the README for what users should do.

Maintainers, run this once per machine to create and install the certificate:

```bash
scripts/generate-signing-cert.sh
```

The script prints `SIGNING_CERT_P12_BASE64` and `SIGNING_CERT_PASSWORD`. Add both as GitHub Actions secrets before publishing a signed release.

Do not generate a second certificate. A new identity changes the designated requirement and drops existing Accessibility grants. The script refuses to replace an existing `Clipth Self-Signed` identity unless you pass `--force`.

## Pull Request Guidelines

Before opening a PR:

- Keep the change focused.
- Explain the user-visible behavior change.
- Mention any privacy, security, or MCP impact.
- Update README or docs when behavior changes.
- Add or update tests when the change touches parsing, persistence, search ranking, or data deletion.
- Run the Debug build command above, or explain why you could not run it.

## Good First Contributions

Good starting areas:

- Documentation improvements
- Localization fixes
- URL sanitizer test cases
- Search token parser test cases
- MCP resources and prompts
- Accessibility and keyboard-navigation polish
- Performance profiling with large histories

## Privacy Bar

For clipboard-related features, describe:

- What data is read
- What data is stored
- How users can disable or delete it
- Whether it is visible to MCP clients
- Whether it can trigger network access

If the answer is unclear, open an issue before implementing.

## Release Notes

User-facing changes should be reflected in `docs/release-notes/<version>.md` in the [wavever/clipth-website](https://github.com/wavever/clipth-website) repo when preparing a release — the notes live there alongside the homepage. The release workflow checks that repo out and uses those files to generate the GitHub Release body and Sparkle appcast notes, so write them *before* pushing the tag.
