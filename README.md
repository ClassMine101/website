# ClassMine101 — website

Source for **classmine101.com**, served by GitHub Pages from the `ClassMine101` organization.

Planning and production notes live in the private [ClassMine101/internal](https://github.com/ClassMine101/internal) repo.

## Branches

| Branch | Role |
|---|---|
| `dev` | Default branch. All work happens here. Nothing is published from it. |
| `prod` | Release branch. Every push here deploys to the live site. |

## Daily workflow

```bash
git switch dev
# ...edit files...
git add -A
git commit -m "Describe the change"
git push
```

## Release to production

```bash
git switch prod
git merge dev
git push
```

The push to `prod` triggers `.github/workflows/deploy.yml`, which publishes the
repository root to GitHub Pages. A release takes about a minute.

## Live setup

- Site: https://classmine101.com (and https://www.classmine101.com)
- Pages source: GitHub Actions (workflow)
- Domain: Pages setting plus `CNAME`; apex A records 185.199.108-111.153, `www` CNAME to `classmine101.github.io`
- HTTPS: enforced; GitHub-managed certificate on classmine101.com and www

The site is plain HTML/CSS/JS and needs no build step. If a framework is added later,
build it in a job step of the deploy workflow and upload the build output directory
instead of `.`.
