# Nazihah Noor — personal site

A Jekyll static site for GitHub Pages. Replaces the WordPress version at nazihahnoor.com.

## File map

```
_config.yml                  Site title, tagline, email, social links, custom domain
index.md                     Home (portrait + bio)
about.md                     About Me (with full logo lockup)
research.md                  Research themes and publications
media.md                     Press, interviews, podcasts
reflections.md               Reflections index (lists posts automatically)
contact.md                   Contact
_reflections/                One Markdown file per reflection
_layouts/                    HTML templates (rarely edited)
_includes/                   Header (with logo), footer, head (rarely edited)
assets/css/main.css          All styling
assets/images/logo-mark.svg  Mark-only logo (header, favicon)
assets/images/logo-full.svg  Full lockup (used on About Me page)
assets/images/               Put your other photos here (including portrait.jpg)
```

## Quick edits

- **Change your bio, email, LinkedIn, etc.**: edit `_config.yml`.
- **Edit any page**: open its `.md` file, change the text, commit.
- **Add a reflection**: create a file in `_reflections/` named `YYYY-MM-DD-slug.md`. Copy the front matter from any existing one. Set `category` to any string (e.g. `Field Notes`, `Science Comms`, `Book Reviews`); it will show as a tag on the index.
- **Add your portrait**: save your photo as `assets/images/portrait.jpg`, then in `index.md` uncomment the `<img>` line and delete the placeholder div below it.
- **Add a CV PDF**: drop it at `assets/cv.pdf` and link to it from `about.md` or `research.md`.

## Publishing to GitHub Pages (step by step)

1. **Create the repo.** On github.com, click New repository.
   - For a user site (lives at `https://<username>.github.io`), name it exactly `<username>.github.io`.
   - For a project site (lives at a subpath), name it anything.
2. **Push these files to the `main` branch.** Easiest option: on the empty repo page, click "uploading an existing file" and drag the unzipped contents of this folder in. Or use `git`:
   ```
   git init
   git add .
   git commit -m "initial site"
   git branch -M main
   git remote add origin https://github.com/<username>/<repo>.git
   git push -u origin main
   ```
3. **Turn on Pages.** In the repo on GitHub: Settings → Pages. Set:
   - Source: Deploy from a branch
   - Branch: `main`, folder: `/ (root)`
   - Save.
4. Wait a minute. Your site will be live at `https://<username>.github.io/` (or `https://<username>.github.io/<repo>/` if it's a project site).

## Keeping nazihahnoor.com

Your domain was bought via WordPress, so first check whether your WordPress plan lets you edit DNS directly. Open your WordPress dashboard, go to Upgrades → Domains → nazihahnoor.com → DNS records. If you can see and edit DNS records, do this:

1. **In GitHub**: Settings → Pages → Custom domain. Enter `nazihahnoor.com` and save. GitHub will create a `CNAME` file in the repo.
2. **In WordPress DNS**: add these records:
   - Four `A` records on the apex (`@`), pointing to:
     `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`
   - One `CNAME` record on `www`, pointing to `<username>.github.io`
   - Remove any existing `A` records for `@` or `CNAME` for `www` that point at WordPress.
3. **In GitHub**: wait up to 24 hours, then tick Enforce HTTPS once the certificate provisions.
4. **In `_config.yml`**: set `url: "https://nazihahnoor.com"`.

If WordPress doesn't let you edit DNS on your current plan, you have two options:

- **Point WordPress's name servers at Cloudflare** (free): sign up at cloudflare.com, add your domain, Cloudflare gives you two name servers, enter those in WordPress's domain settings, then manage DNS from Cloudflare using the same records above.
- **Transfer the domain to another registrar** (around $10/year): providers like Namecheap, Porkbun, or Cloudflare Registrar all give you full DNS control. Takes about a week to transfer.

Either way, your WordPress site at nazihahnoor770c8f9617-pvyxb.wordpress.com stays available at that URL as a backup until you cancel the WordPress plan.

## Running locally (optional)

If you want to preview changes on your laptop before pushing:

```
bundle install
bundle exec jekyll serve
```

Open http://localhost:4000. Not required — you can edit on GitHub's web interface and see changes at the live URL in about 60 seconds.
