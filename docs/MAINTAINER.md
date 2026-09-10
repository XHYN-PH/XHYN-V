# GitHub setup and release maintenance

[Back to the project](../README.md)

## Repository details

| Setting | Prepared value |
| --- | --- |
| Repository name | `XHYN-V` |
| Description | Documentation, guides, compatibility and release information for XHYN V, the community Android launcher by XHYN_PH. |
| Initial visibility | Private draft |
| Main branch | `main` |
| Website | `https://youtube.com/@xhyn_ph` |
| Topics | `android`, `arm64`, `gtav`, `dxvk`, `turnip`, `touch-controls`, `xhyn-v` |
| Issues | Enable for bug reports, compatibility reports and documentation feedback |
| Wiki | Optional; guides already live under `docs/` |

The package contains only Markdown/text documentation and the project logo. Remote creation and APK publication are separate steps. A private initial repository lets XHYN_PH review the description, contents and license status before changing visibility.

## Create through GitHub's website

1. Extract the repository ZIP. Open the inner **XHYN-V** folder; `README.md` must end up at the repository root.
2. Open [New repository](https://github.com/new), choose your account and enter the name/description above.
3. Choose Private initially. Do not add a generated README, license or ignore template; upload the prepared documentation as supplied.
4. Create the repository, then use its upload-files option to add the extracted contents. Upload folders in batches if the browser interface requires it. Upload the actual files, not the ZIP as a single repository file.
5. Commit the upload and open README, the logo and the guide links to verify the result.

See GitHub's [repository creation instructions](https://docs.github.com/en/repositories/creating-and-managing-repositories/creating-a-new-repository).

## Create using Git and GitHub CLI

On a computer with Git and the GitHub CLI installed, sign in using `gh auth login`. From the extracted **XHYN-V** directory:

```bash
git init -b main
git add .
git diff --cached --stat
git commit -m "Add XHYN V documentation and user guides"
gh repo create XHYN-V --private --source=. --remote=origin --push --description "Documentation, guides, compatibility and release information for XHYN V, the community Android launcher by XHYN_PH." --homepage "https://youtube.com/@xhyn_ph" --disable-wiki
```

Git uses your configured commit name/email. Set those to your own preferred GitHub identity before committing if they are not already configured. The command uses the authenticated account as owner; it does not guess XHYN_PH's GitHub username. If `XHYN-V` already exists, inspect that repository before choosing a different name or pushing anything into it. [GitHub CLI reference](https://cli.github.com/manual/gh_repo_create).

After creation, set the topics above in the About panel. No code, tests or automated build workflow are included in this documentation package.

## Documentation and APK releases

APKs belong in release assets rather than the documentation tree. Keep this repository limited to its guides, notices, release information and logo. See [GitHub's large-file guidance](https://docs.github.com/en/repositories/working-with-files/managing-large-files/about-large-files-on-github) for binary hosting limits.

This documentation package does not itself publish a game, APK, driver binary or game data. Review the applicable component/distribution terms before attaching binaries; the project's anti-piracy notice is an attribution/usage statement, not a substitute for those terms.

## Prepare the 0.10 release

Use tag **v0.10**, title **XHYN V 0.10 — Controls and renderer customization**, and [the prepared release notes](releases/v0.10.md). Save a draft first. Leave phone confirmation marked pending until a revision 10 device report is available.

For a draft containing the release notes and checksum file, after the repository has been created and pushed:

```bash
gh release create v0.10 docs/releases/v0.10-SHA256SUMS.txt --draft --target main --title "XHYN V 0.10 — Controls and renderer customization" --notes-file docs/releases/v0.10.md
```

This creates a draft and does not attach the APK. Before publishing, attach the intended distributable files or make it explicit that the release contains documentation only. A checksum for an APK is not a download of that APK. The CLI supports draft creation and notes files as documented in [GitHub's release command reference](https://cli.github.com/manual/gh_release_create).

The prepared release-note body uses community URLs and plain repository paths, so it can be pasted into a draft without guessing a GitHub account name. Add the final APK download link to README after its release asset is available.

## Before making the project public

Confirm that the current feature/status text matches what is actually shipped and tested, and select a license scope for original contributions if you intend to grant reuse rights. Retain component notices. Do not describe this as the complete open-source GTA V engine or an official Rockstar release.

The files contain no game-data download links or signing credentials. Keep private signing backups outside the repository and release assets. Public certificate digests in the docs are intentionally included for APK verification.

## Updating later releases

Update README status, CHANGELOG, compatibility reports and versioned release metadata together. Generate fresh checksums and validation evidence for each new APK. Keep historical records tied to their original build, and separate host results from actual device observations.

Add real screenshots or a gameplay link when supplied; do not use fabricated gameplay images or unsupported performance badges. The existing logo is the user-supplied purple V asset extracted unchanged from the APK.
