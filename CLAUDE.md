# CLAUDE.md

## Project Overview

**Solar Anamnesis Store** is a multilingual meteorite thin section microphotography store. The site presents a collection of high-resolution meteorite images organized by meteorite type, displayed using the Galleria.js slideshow library, with print-on-demand purchasing powered by Fotomoto.

**Live Site:** https://store.solaranamnesis.com/

**Technical Stack:**
- Static HTML/CSS (vanilla, no JavaScript frameworks)
- [Galleria.js 1.6.1](https://cdnjs.cloudflare.com/ajax/libs/galleria/1.6.1/galleria.min.js) for image gallery/slideshow
- jQuery 1.11.1 (Galleria dependency)
- [Bulma 1.0.2](https://cdn.jsdelivr.net/npm/bulma@1.0.2/css/bulma.min.css) for the store index pages
- Fotomoto widget for print-on-demand purchasing
- Deployed as a static site via HTTPS

---

## Repository Structure

```text
/
├── index.html                  # English store front page (source of truth)
├── index-{lang}.html           # Localized store front pages (48+ languages, BCP-47 codes)
├── README.md                   # Language index with links
├── LOCALIZATION.md             # Localization guide and translations reference
├── robots.txt
├── sitemap.xml
│
├── AcapulcoiteMeteorites/      # Collection directory
│   ├── index.html              # Galleria.js gallery page
│   ├── *.jpg                   # Full-resolution images
│   └── thumbs/                 # Thumbnail images
├── AngriteMeteorites/
├── AubriteMeteorites/
├── BrachiniteMeteorites/
├── EnstatiteChondrites/
├── GigapixelGallery/           # Uses .webp images with titles/descriptions
│   ├── index.html
│   ├── *.webp
│   └── thumbs/
├── HEDMeteorites/
├── HighMetalGroup/
├── IndividualMicroShots/
├── IronMeteorites/
├── KaroondaGroup/
├── LodraniteMeteorites/
├── LunarMeteorites/
├── MartianMeteorites/
├── MesosideriteMeteorites/
├── MigheiGroup/
├── Misc/
├── OrdinaryChondrites/
├── OrnansGroup/
├── PallasiteMeteorites/
├── RenazzoGroup/
├── RumurutiChondrites/
├── STRESSStyleThinSections/
├── UnclassifiedMeteorites/
├── UngroupedAchondriteMeteorites/
├── UreiliteMeteorites/
└── VigaranoGroup/
```

---

## Coding Standards

### HTML Formatting

Collection gallery pages (`{Collection}/index.html`) use **Prettier** formatting (2-space indentation). Store front pages (`index.html`, `index-{lang}.html`) use **js-beautify** formatting (2-space indentation, no line-length wrap).

To re-format all root HTML files:

```bash
npx html-beautify --indent-size 2 --wrap-line-length 0 --preserve-newlines --unformatted "" -r *.html
```

**Requirements:**

- 2-space indentation throughout.
- No line-length wrapping on store front pages.
- Attribute values are unquoted where possible on front pages (matching existing style).

### Galleria.js Gallery Pages

Each collection directory contains an `index.html` with a Galleria.js slideshow. The standard structure is:

```html
<!doctype html>
<html lang="en">
  <head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width,initial-scale=1" />
    <title>Solar Anamnesis - {Collection Name}</title>
    <meta name="description" content="{description}" />
    <style>
      .galleria { height: 100vh; background: #000; }
      @media (min-width: 768px) { .galleria { height: 1280px; } }
      body { background-color: rgb(0, 0, 0); }
    </style>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/1.11.1/jquery.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/galleria/1.6.1/galleria.min.js"></script>
    <link rel="icon" type="image/png" href="favicon.jpg" />
  </head>
  <body>
    <div class="galleria"></div>
    <script>
      var gallery1Data = [
        { image: "filename.jpg", thumb: "thumbs/filename.jpg" },
        // ...
      ];

      (function () {
        Galleria.loadTheme(
          "https://cdnjs.cloudflare.com/ajax/libs/galleria/1.6.1/themes/classic/galleria.classic.min.js"
        );

        Galleria.ready(function () {
          this.attachKeyboard({ left: this.prev, right: this.next });
          this.lazyLoadChunks(10, 500);
        });

        Galleria.run(".galleria", {
          imageCrop: false,
          swipe: true,
          dataSource: gallery1Data,
          thumbnails: "lazy",
        });
      })();
    </script>
    <!-- Fotomoto purchase widget -->
    <script type="text/javascript"
      src="https://widget.fotomoto.com/stores/script/{store-key}.js"></script>
    <noscript>If Javascript is disabled...</noscript>
  </body>
</html>
```

**Key Galleria configuration options:**
- `imageCrop: false` — show full image without cropping.
- `swipe: true` — enable touch swipe navigation.
- `thumbnails: "lazy"` — lazy-load thumbnails for performance.
- `lazyLoadChunks(10, 500)` — load images in chunks of 10 with 500ms delay.
- Keyboard navigation: left/right arrow keys mapped to prev/next.

### Image Conventions

- **Most collections:** `.jpg` format for full images and thumbnails.
- **GigapixelGallery:** `.webp` format; data entries include `title` and `description` fields (HTML allowed in `description`).
- Thumbnails live in a `thumbs/` subdirectory within each collection directory.
- Image filename pattern: `{meteorite-name}---{type}_{flickr-id}_o.{ext}`
  - Types: `gigapixel`, `hdr`, `xpl-hdr` (cross-polarized light HDR)

### Store Front Pages (Bulma-based)

The root `index.html` and all `index-{lang}.html` files use Bulma CSS for layout:

```html
<section class="section">
  <div class="container">
    <h1 class="title has-text-centered">{Collections heading}</h1>
    <div class="columns is-multiline">
      <div class="column is-one-third">
        <div class="card">
          <div class="card-content">
            <p class="title">
              <a href="https://store.solaranamnesis.com/{CollectionPath}">{Name}</a>
            </p>
          </div>
        </div>
      </div>
    </div>
  </div>
</section>
```

- Dark space-themed background: `linear-gradient(to bottom, #013, #036)`.
- Card style: `background-color: rgba(0, 51, 102, 0.9); border: 1px solid #fff`.
- Link hover color: `gold`.

### RTL Language Support

RTL languages (`ar`, `fa`, `he`, `ur`) require `dir="rtl"` on the `<html>` element.

---

## Localization

The English `index.html` is the **source of truth** for structure. All `index-{lang}.html` files mirror its structure with translated content. See `LOCALIZATION.md` for full translations reference.

### Supported Languages (48)

| Code | Language | RTL |
|------|----------|-----|
| `ar` | Arabic | ✓ |
| `fa` | Persian | ✓ |
| `he` | Hebrew | ✓ |
| `ur` | Urdu | ✓ |
| `am` | Amharic | |
| `bn` | Bengali | |
| `bo` | Lhasa Tibetan | |
| `de` | German | |
| `el` | Greek | |
| `es` | Spanish | |
| `eu` | Basque | |
| `fi` | Finnish | |
| `fr` | French | |
| `gu` | Gujarati | |
| `ha` | Hausa | |
| `hi` | Hindi | |
| `hu` | Magyar | |
| `hy` | Armenian | |
| `id` | Bahasa Indonesia | |
| `it` | Italian | |
| `ja` | Japanese | |
| `jv` | Javanese | |
| `ka` | Georgian | |
| `kn` | Kannada | |
| `ko` | Korean | |
| `la` | Latin | |
| `mn` | Mongolian (Latin script) | |
| `mr` | Marathi | |
| `new` | Nepal Bhasa | |
| `nl` | Dutch | |
| `or` | Odia | |
| `pa` | Punjabi | |
| `pl` | Polish | |
| `pt` | Portuguese | |
| `ru` | Russian | |
| `si` | Sinhala | |
| `sv` | Swedish | |
| `sw` | Kiswahili | |
| `ta` | Tamil | |
| `te` | Telugu | |
| `th` | Thai | |
| `tl` | Tagalog | |
| `tr` | Turkish | |
| `tt` | Tatar | |
| `vi` | Vietnamese | |
| `yo` | Yoruba | |
| `zh` | Chinese | |

### Adding a New Language

1. Copy any existing `index-{lang}.html` as a starting point.
2. Rename to `index-{new_lang}.html` using the correct BCP-47 code.
3. Update `<html lang="...">` (add `dir="rtl"` if needed).
4. Update `<title>` and translate the `<h1>` "Collections" heading.
5. Translate each collection link's display text (do **not** change `href` values).
6. Add an entry to `README.md`.
7. Add translations to `LOCALIZATION.md`.

### Translation Notes

- Scientific meteorite type names (Acapulcoite, Angrite, etc.) often retain their Latin/international form across languages.
- Group names (Karoonda Group, Mighei Group, etc.) may remain as proper nouns.
- **"STRESS Style Thin Sections"** is a specific product name — kept in English in all languages.
- **"High Metal Group"** and **"Individual MicroShots"** are product-specific terms generally kept in English.
- All translations should be verified with native speakers before production use.

---

## Common Tasks

### Adding Images to a Collection

1. Add the full-resolution image file to `{Collection}/`.
2. Add a thumbnail to `{Collection}/thumbs/` (same filename).
3. Add an entry to the `gallery1Data` array in `{Collection}/index.html`:
   ```js
   { image: "filename.jpg", thumb: "thumbs/filename.jpg" }
   ```
   For GigapixelGallery, also include `title` and `description` fields.

### Adding a New Collection

1. Create a new directory (e.g., `NewCollectionMeteorites/`).
2. Add images and a `thumbs/` subdirectory.
3. Create `index.html` following the Galleria.js template above.
4. Add a card link to `index.html` (and all `index-{lang}.html` files).
5. Add the collection to `LOCALIZATION.md` with translations.
6. Add the URL path to the Collections reference table in `LOCALIZATION.md`.

### Formatting Gallery HTML Files

```bash
# Format a single collection gallery page
npx prettier --write {Collection}/index.html

# Format all root store front pages
npx html-beautify --indent-size 2 --wrap-line-length 0 --preserve-newlines --unformatted "" -r *.html
```

---

## Security Considerations

- All pages served over HTTPS only.
- No dynamic user input or server-side code.
- jQuery and Galleria.js loaded from cdnjs (trusted CDN); Bulma from jsDelivr.
- Fotomoto purchasing widget loaded from `widget.fotomoto.com`.
- No mixed content — all asset URLs must be HTTPS.

---

## Testing Checklist

Before deploying changes:

- [ ] Gallery pages display and navigate correctly in browser.
- [ ] New images appear in correct order in the slideshow.
- [ ] Thumbnails load correctly from `thumbs/` directory.
- [ ] Fotomoto purchase widget loads and functions.
- [ ] Store front page links all resolve correctly.
- [ ] All language files have consistent collection links.
- [ ] RTL languages render correctly (`dir="rtl"` present, layout intact).
- [ ] Responsive design tested on mobile/tablet/desktop.
- [ ] HTTPS enforced; no mixed content warnings.

---

## Contact & Support

- **Repository:** https://github.com/solaranamnesis/solaranamnesis-store
- **Live Site:** https://store.solaranamnesis.com/
- **Main Site:** https://www.solaranamnesis.com/
