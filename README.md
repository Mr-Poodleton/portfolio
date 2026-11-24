# Jaynier V. Gonzaga: Portfolio

A single-page personal portfolio with a James Bond theme: a gun-barrel opening, a 3D tunnel background, a scroll-driven title sequence, and widescreen project scenes. It is plain HTML, CSS, and JavaScript with no build step, so it deploys to Vercel as a static site.

- **Live site:** https://portfolio-xi-plum-65.vercel.app
- **GitHub:** https://github.com/Mr-Poodleton
- **LinkedIn:** https://www.linkedin.com/in/jaynier-gonzaga
- **Email:** gonzagajaynier2004@gmail.com

---

## 1. Folder structure

Everything must sit in the **root** of the repository, with these exact lowercase file names:

```
portfolio/
├── index.html        <- the whole site (already written, do not rename)
├── photo.jpg         <- YOUR PHOTO (to add)
├── resume.pdf        <- YOUR RESUME (to add)
├── README.md         <- this file
└── media/            <- project screenshots and demo videos (to add)
    ├── pesoscan.mp4      (or pesoscan.jpg)
    └── vehicle.mp4       (or vehicle.jpg)
```

## 2. Files still needed

| File | What it is | Tips |
|---|---|---|
| `photo.jpg` | Portrait shown in the hero frame | Portrait crop (4:5), under about 500 KB. Until added, the initials "JG" show. |
| `resume.pdf` | Opened by the "Download resume" button | Export the final resume as PDF. Until added, the button gives a 404. |
| `media/pesoscan.mp4` or `.jpg` | Screen recording or screenshot of PesoScan | MP4 should be short, silent, and under about 10 MB. Either file works. |
| `media/vehicle.mp4` or `.jpg` | Clip or screenshot of the vehicle counter | Same tips. |

If a media file is missing, the page automatically shows a drawn detection-box illustration instead, so nothing breaks.

## 3. Preview locally (optional)

1. Open the folder in VS Code (File, then Open Folder).
2. Install the **Live Server** extension.
3. Right-click `index.html` and choose **Open with Live Server**.

The opening sequence plays once per browser session. Click or press any key to skip it. To see it again, open the site in a new private window.

## 4. Publish to GitHub

### Option A: VS Code Source Control (no commands)
1. Open the Source Control tab (branch icon).
2. Click **Initialize Repository**.
3. Type a message such as `Add portfolio`, then click **Commit** (stage all changes if asked).
4. Click **Publish Branch**, sign in to GitHub if asked, name the repo `portfolio`, and choose Public or Private. Vercel can deploy either.

### Option B: Terminal (with the GitHub CLI)
```bash
git init
git add .
git commit -m "Add portfolio"
git branch -M main
gh repo create portfolio --public --source=. --remote=origin --push
```
If `gh` is not installed or logged in: `winget install GitHub.cli`, then `gh auth login`.

## 5. Deploy on Vercel

### Option A: Dashboard (recommended)
1. Go to https://vercel.com and sign up with GitHub.
2. Click **Add New**, then **Project**, and import the `portfolio` repo.
3. Set **Framework Preset** to **Other**. Leave Build Command and Output Directory empty. There is nothing to build.
4. Click **Deploy**. A link like `portfolio-xxxx.vercel.app` appears in about a minute.

### Option B: Vercel CLI
```bash
npm install -g vercel
vercel login
vercel          # first deploy (preview). Accept the defaults.
vercel --prod   # production deploy
```

## 6. Updating the site

Edit files in VS Code, then commit and push (Source Control: Commit, then Sync Changes). Vercel redeploys automatically after every push to `main`.

Optional custom domain: Vercel project, Settings, Domains.

## 7. Where to edit things in `index.html`

| To change | Look for |
|---|---|
| Name in the hero | `<h1 id="title"` |
| About text | `<section id="about">` |
| The three title-sequence cards | `<section id="seq"` (the `.card` paragraphs) |
| Project scenes (PesoScan, Vehicle Detection) | `<article class="scene">` |
| Smaller projects (chatbot, team projects) | the `.more` block |
| Skills, experience, certifications | `<section id="skills">` and `<section id="record">` |
| Email, GitHub, LinkedIn links | `<section id="contact">` |
| Colors | CSS variables at the top of `<style>` (`--gold`, `--blood`, `--ink`, `--mute`) |

## 8. Troubleshooting

- **Photo or resume not showing:** the file name or location is wrong. It must be exactly `photo.jpg` or `resume.pdf` in the repo root, in lowercase.
- **Media not showing:** files must be inside `media/` and named exactly `pesoscan` or `vehicle` with `.mp4` or `.jpg`.
- **No animations or 3D tunnel:** the page loads GSAP and Three.js from cdnjs.cloudflare.com. If that is blocked or offline, the site falls back to a plain static layout. This is expected. Visitors with "reduce motion" turned on also get the static layout.
- **Changes not appearing:** make sure you pushed to GitHub, then check the Deployments tab in Vercel.

---

## Instructions for GitHub Copilot (Agent mode)

Follow this README to get the portfolio live. Rules:

1. **Do not redesign or rewrite `index.html`.** Only make the edits the user asks for.
2. Confirm that `photo.jpg`, `resume.pdf`, and the `media/` files exist in the repo root. If any are missing, tell the user which ones. Never create fake or placeholder versions.
3. Do not commit large video files over about 25 MB. Ask the user to compress them first.
4. Walk through sections 4 and 5. Run each terminal command only after showing it to the user, and ask before anything that publishes or deploys.
5. At the end, report the live URL and a checklist of anything still missing.
