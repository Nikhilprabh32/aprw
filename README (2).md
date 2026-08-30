# ajayprabhu.com

A modernized rebuild of Ajay Prabhu's real estate site — Realtor with Beam Real
Estate and licensed loan officer with Sure Fund Mortgage, serving the DFW
Metroplex.

Everything lives in **`index.html`**. One file: no build step, no dependencies,
no install. Open it in a browser and it runs.

## Editing

Open `index.html` on GitHub and hit the pencil icon, or clone and edit locally:

```bash
git clone https://github.com/Nikhilprabh32/ajayprabhu.com.git
cd ajayprabhu.com
open index.html          # macOS  (Windows: start index.html)
```

The file is organized top to bottom:

| Section | What's there |
| --- | --- |
| `:root` tokens | Colors, fonts, spacing. Change the navy in one place and the whole site follows. |
| CSS blocks | Commented per section — nav, hero, testimonials, blog, footer. |
| `REVIEWS` | Client reviews. Add an object to the array and it appears everywhere. |
| `POSTS` | Blog posts. Same idea. |
| `PAGES` | One function per page, returning that page's HTML. |
| Router | Hash-based (`#/blog`, `#/about`). No server needed. |

### Adding a review

Find the `REVIEWS` array and add an entry. Ratings are 1–5.

```js
{ n:'Client Name', c:'Frisco', d:'01/15/2026', r:5, q:'What they said.' },
```

### Adding a blog post

Find the `POSTS` array. `tag` is the category chip; `m` is the meta line.

```js
{ t:'Post title', tag:'Buying', m:'Frisco, TX' },
```

Slugs and detail-page links generate automatically.

## Adding photos — no coding required

Upload your photos to the **`images/`** folder using these exact names, and
they appear on the site automatically:

| Filename | Where it shows up |
| --- | --- |
| `hero-1.jpg` … `hero-6.jpg` | The homepage slideshow, in order |
| `ajay.jpg` | Ajay's photo — About, Mortgage and Contact pages |
| `contact.jpg` | Photo beside the homepage contact form |
| `beam-logo.png` | Beam Real Estate logo, footer of every page |

To upload straight from GitHub: open the `images/` folder → **Add file → Upload
files** → drag them in → **Commit changes**.

**Nothing breaks if a photo is missing.** That spot shows a colored placeholder
until the file exists, so you can add them one at a time. If a photo doesn't
appear, the name is almost certainly off — names are case-sensitive, and
`hero-1.png` won't match `hero-1.jpg`.

Keep each file under about 1 MB so the page loads quickly. Any free "compress
jpeg" site will shrink a 5 MB photo to a few hundred KB with no visible loss.

See `images/README.md` for the full guide, including how to add a 7th slideshow
photo or use fewer.

### Where the filenames are defined

Near the bottom of `index.html` there's a clearly-marked block:

```js
var IMAGES = {
  hero: [ 'images/hero-1.jpg', 'images/hero-2.jpg', ... ],
  headshot: 'images/ajay.jpg',
  contact:  'images/contact.jpg',
  beamLogo: 'images/beam-logo.png'
};
```

That's the only place filenames live. Change them here to match your own files
instead of renaming your photos.

## Publishing

To put it online free via GitHub Pages: **Settings → Pages → Source: Deploy from
a branch**, pick the branch and `/ (root)`. It'll serve at
`nikhilprabh32.github.io/ajayprabhu.com`. Pointing the real domain at it takes a
DNS change plus a `CNAME` file.

## Known gaps

- **Contact forms don't send.** They're styled and validate, but there's no mail
  service wired up. Formspree or Netlify Forms would take about ten minutes.
- **Blog articles have no body text.** Every post has a working page with a
  marked block where the copy goes; the titles are real, the articles aren't
  written.
- **A few town guides may be missing** — some of the "Ultimate Guide" posts
  between Lewisville and Plano weren't captured from the live site.
