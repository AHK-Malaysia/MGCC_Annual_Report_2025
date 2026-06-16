# MGCC Annual Report 2025

Single-file HTML annual report (with embedded video) for the Malaysian-German Chamber of Commerce and Industry (AHK Malaysia / MGCC), auto-deployed to GitHub Pages.

## Files

| File | Purpose |
|------|---------|
| `index.html` | The full report — self-contained, video and all images embedded (~44 MB) |
| `.github/workflows/deploy.yml` | GitHub Actions workflow that publishes to Pages on every push to `main` |
| `.nojekyll` | Disables Jekyll so the site is served as plain static files |

## One-time setup

1. Create a new repository on GitHub (or use an existing one).
2. Push these files to the `main` branch (see commands below).
3. In the repo: **Settings → Pages → Build and deployment → Source → GitHub Actions**.

That's it. Every push to `main` rebuilds and republishes automatically. You can also trigger it manually from the **Actions** tab (the workflow has `workflow_dispatch` enabled).

## Push commands

From inside this folder:

```bash
git init
git add .
git commit -m "Add MGCC Annual Report 2025"
git branch -M main
git remote add origin https://github.com/<YOUR-USER-OR-ORG>/<REPO-NAME>.git
git push -u origin main
```

Replace `<YOUR-USER-OR-ORG>` and `<REPO-NAME>` with your own. For the AHK Malaysia org it would be something like `https://github.com/ahk-malaysia/MGCC_Annual_Report_2025.git`.

## Live URL

After the first successful Actions run, the report is available at:

```
https://<YOUR-USER-OR-ORG>.github.io/<REPO-NAME>/
```

## Note on the embedded video

The video is base64-encoded directly inside `index.html`, so the whole 44 MB downloads before the page renders — kept this way per request for a single self-contained file. The file is comfortably under GitHub's 100 MB hard limit, but if load times become a problem later, extracting the video to a separate `.mp4` and referencing it with a `<video src>` tag would let the page render immediately and let browsers cache the video separately.
