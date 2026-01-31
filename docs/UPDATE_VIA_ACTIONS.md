# Update Sources via GitHub Actions (Step-by-Step)

This repo includes a workflow that replaces a branch with the contents of an archive.
The script `build-daemon-ubuntu.sh` is always removed, even if it exists in the archive.

## 1) Prepare the source archive
1. Create a `tar.gz` or `zip` with the new sources.
2. Ensure it does not include build artifacts (`build/`, `contrib/depends/`, etc.).
3. If the archive contains `build-daemon-ubuntu.sh`, it will still be removed.

## 2) Host the archive at a public URL
Examples:
- GitHub Release asset (direct link)
- Any public HTTPS URL

## 3) (Optional) Compute SHA256
For integrity verification:
```
sha256sum source.tar.gz
```

## 4) Run the workflow
1. Open the repo on GitHub.
2. Go to **Actions** → **Replace Source From Archive**.
3. Click **Run workflow**.
4. Fill in:
   - `archive_url` — direct link to the archive.
   - `archive_sha256` — optional checksum.
   - `target_branch` — usually `master`.
5. Run it.

## 5) Verify
After a successful run:
- the branch is replaced with the archive contents,
- `build-daemon-ubuntu.sh` is removed,
- the workflow remains for future updates.

---

If you need private URLs, tell me and I’ll add secrets support.
