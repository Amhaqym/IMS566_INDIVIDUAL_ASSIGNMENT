# ScentVault — Phase 2

This release fixes the navigation that was missing in the earlier Phase 1.4 FAQ update.

- **My Collection** is a single clickable label with no arrow; its submenu has Owned, Wishlist and Full Catalogue.
- **Brand Directory** now expands to All Brands, Arabian, Malaysian, Indonesian and International Designer. Choosing a region opens `brands.html?region=...` and preselects the corresponding filter.
- **Analytics** now expands to Overview, Fragrance Insights, Financial Insights and Catalogue Insights. Each option navigates to a real section anchor.
- The decorative navigation numbers (01–06), menu-item counts and the decorative list numbers in Brand Directory are removed. KPI totals remain unchanged.
- On desktop, hover and click work. On touch devices, tap toggles menus. Keyboard users can press Enter/Space and Escape.
- No browser storage is used. All perfume prices and data, FAQ, About, Contact, and Bootstrap framework are preserved.

# ScentVault — Phase 2

**A curated personal perfume collection and fragrance reference website.**

ScentVault uses an editorial black, warm ivory, and brushed-gold visual identity. It includes a fixed catalogue of 24 fragrance brands, 72 perfumes, an illustrative 12-perfume owned collection, an 8-item wishlist, and analytics calculated from those records. Its UI is intended to look like a finished collection tool rather than an assignment template.

## Quick start (VS Code)

1. Extract the current `ScentVault_Phase2_Refined.zip`.
2. Open the **ScentVault_Phase2** folder in Visual Studio Code (the folder containing `index.html`).
3. Right-click `index.html` and select **Open with Live Server**. You can also open `index.html` directly, though Live Server is recommended.
4. The sign-in screen already contains the sample credentials:

   - **Email:** `demo@scentvault.com`
   - **Password:** `demo123`

5. Click **Enter ScentVault** to go to the dashboard. On desktop, navigate through the **left sidebar**; on mobile, use the **Menu** button.

No installation, database configuration, PHP server, or internet access is required for the basic site. Bootstrap 5.3.6 is bundled locally. Charts use Chart.js when the CDN can be loaded and switch to the locally bundled Canvas renderer if the internet is unavailable. Google Fonts are optional; the site includes system-font fallbacks.

## What's in Phase 1.4

| Feature | Implementation |
| --- | --- |
| Login | Pre-filled, hardcoded sample credentials; shows an error for incorrect credentials; no guest box or registration form |
| Visual design | Balanced Luxury editorial style; premium black-bottle still life on login and dashboard hero |
| Navigation | Persistent **left-hand directory** on desktop, open/close drawer on narrow screens, keyboard-accessible links |
| Dashboard | Eight calculated KPIs, two collection charts, recent perfumes and wishlist priorities |
| My Collection | 12 seeded owned perfumes (each valued at RM1,000 or less) |
| Wishlist | Eight seeded wishlist entries, including aspirational higher-priced fragrances |
| Catalogue | 24 brands × 3 perfumes each = **72 entries** |
| Browsing | Search, origin/brand/family filters, sorting, grid/table view, working pagination and perfume details dialog |
| Brand Directory | 24 typographic brand rows, prices, perfumes, and working brand-to-catalogue links |
| Analytics | Seven charts plus separate *Owned by Brand* and complete *Catalogue by Brand* tables |
| Ratings | Seeded values range from 1 to 5 stars, plus an **unrated** perfume |
| Prices | User-chosen **fixed price per brand** in RM, not claimed to be current retail prices |
| Bottle variants | Concentration and bottle size provided for each fragrance. Real product sizes may be 32, 35, 40, 50, 100, 105 ml, etc. |

**Important distinction:** There are 24 catalogue brands, but the owned-collection table counts only brands represented among the 12 seeded owned perfumes. It is correct for these two tables to show different row counts.

### Catalogue status

The Opai products are **Summer Rock, Victory, and Oasis**, all displayed as 40 ml Extrait de Parfum and RM120 each (fixed, collector-set price). **Velixir** replaces Hausser and contains Morpheus, Icarus, and Uranus. **Versace** replaces the earlier Baccarat/MFK proposal and contains Eros EDP, Eros Flame EDP, and Dylan Blue EDT.

Six extra catalogue items are **provisional suggestions awaiting the collector's approval**:

- Khadlaj: Shiyaaka Sky, Island, Cream Velvet.
- Alchemist: Onirique, Bois et Musc, Got My Mojo Back.

They are labelled *Suggested option* in fragrance listings and details. Product family, concentration and size information marked as reference/indicative should be checked against actual packaging before purchase.

## How the data works (no browser storage)

The project deliberately uses **hardcoded JavaScript data**, according to the project-owner's request:

- `js/data.js`: catalogue of all fragrances, brand prices, selected owned perfume records and wishlist entries.
- Dashboard statistics, all Analytics charts and the Brand Directory are **derived from those same arrays**, not independently typed numbers.
- Browser storage is **not used**. There are no `localStorage` or `sessionStorage` API calls, databases, or network requests for collection data.
- Refreshing or changing pages loads the original hardcoded dataset again. There is **no persistent account registration, ownership editing, importing, or exporting** in Phase 1.4. Search, filters, sorting, pagination, details, display switching and navigation work normally.

### Authentication limitation

The login is deliberately **client-side presentation logic only**. Its credentials are visible in the source and it does **not secure private pages** or create a persistent authenticated session. Opening an internal HTML page directly is possible. This is intentional for a static academic demonstration, **not** a suitable design for a real user-account website. Do not reuse a personal password.

## Rubric compliance

### 4.1 Front-end framework

**Bootstrap 5** (`css/vendor/bootstrap.min.css`, v5.3.6) is included on **all five HTML pages**, using Bootstrap responsive grid classes (such as `row`, `col-*`), forms, buttons and responsive utilities. A custom stylesheet provides the project's art direction.

### 4.2 Code organisation

HTML, CSS and JavaScript are separated and commented; a single shared data module is consumed by page-specific scripts. Each page has its own relevant semantic elements and data-driven content. No inline script logic is needed in the HTML.

### 4.3 Responsive design

Responsive styles include sidebar-to-drawer navigation and adaptable tables, charts, grids, forms and headings. Tested at **1440 × 900** (desktop) and **390 × 844** (mobile) using a Chromium rendering harness. All five pages rendered without script exceptions or document-level horizontal overflow at those sizes.

### 4.4 Content management

Pages have unique `<title>` and description metadata, named sections, labelled controls, semantic page content, a consistent information hierarchy, and structured product fields (brand, origin, country, concentration, volume, fragrance family, notes, price, status). The directory and analytics views use one consistent catalogue data source.

## Source directory

```text
ScentVault_Phase1_3/
├── index.html             Login
├── dashboard.html         Collection overview
├── collection.html        Owned / wishlist / catalogue
├── brands.html            24-brand editorial directory
├── analytics.html         Seven charts and two brand tables
├── css/
│   ├── style.css          Custom Balanced Luxury design system
│   └── vendor/
│       └── bootstrap.min.css
├── js/
│   ├── data.js            24 brands, 72 perfume entries and seed records
│   ├── auth.js            Presentation-only sign-in logic
│   ├── app.js             Sidebar, mobile drawer and common helpers
│   ├── dashboard.js
│   ├── collection.js
│   ├── brands.js
│   ├── analytics.js
│   └── offline-charts.js  Canvas fallback if Chart.js CDN is unavailable
├── assets/
│   ├── images/noir-bottle.jpg
│   ├── images/scentvault-branded-bottle.jpg
│   ├── images/black-marble.webp
│   ├── images/perfumes/sv-001.jpg … sv-072.jpg
│   ├── images/perfumes/IMAGE_MAPPING.csv
│   ├── favicon.svg
│   └── catalogue-selection.json (reference snapshot)
├── CATALOGUE.md
├── THIRD_PARTY_NOTICES.md
└── README.md
```

## Testing notes

Automated rendering tests checked the login form's prefilled credentials and invalid-password message; Dashboard's eight KPIs; Collection's 12 owned items, filter, modal, and table/grid switching; the 24-brand directory; seven analytics canvases; and 24 rows in the complete catalogue summary. The menu was also opened and closed on mobile. The test harness used the exact page HTML/CSS/JS injected into Chromium because the environment blocked direct localhost and local-file navigation. **The complete end-to-end redirect after successful sign-in should also be checked on your own VS Code Live Server.**

## Credit and dependencies

The black bottle image was generated for this ScentVault design, with no borrowed product label or trademark. Third-party dependency details and licenses are in `THIRD_PARTY_NOTICES.md`.


## Phase 1.4: interactive edition

**Pages:** `index.html`, `dashboard.html`, `collection.html`, `brands.html`,
`analytics.html`, `about.html`, and `contact.html`.

**New interactions**
- Sidebar: accessible My Collection submenu for Owned, Wishlist and Full Catalogue. Opens on desktop hover/focus or through the explicit toggle button; phone navigation uses a drawer and tap.
- Dashboard: interactive scent finder filters the 72 catalogue perfumes by scent family and budget; results link to the correct fragrance search.
- My Collection: searchable/filterable and sortable grid/table; add a perfume to Owned or Wishlist; edit purchase price, acquisition date, 1–5 rating, favourites, priority and notes; remove entries; pagination; native detail/edit dialogs; export Owned to CSV.
- Brand Directory: live search and origin filters, and comparison of two or three selected brands in an accessible dialog.
- Analytics: retains seven existing graphs and adds interactive price-range, concentration and bottle-size comparisons across Owned, Wishlist and Catalogue. Budget planner, collection completion progress and collection/value share are computed from seed data.
- About: editorial content architecture with interactive FAQ accordions.
- Contact Us: validated form builds a copyable message; **no email is sent** without a backend/inbox. No fake successful submission.

**Data and persistence:** All 24 brand reference prices and 72 catalogue entries stay in `js/data.js`. Owned and wishlist start from 12 and 8 entries respectively. Modifications live in JavaScript memory in `collection.html` only: changes revert upon refresh or page navigation. No cookies, `localStorage`, `sessionStorage` or server are used. The front-end login is illustrative and not secure authentication.

**Technical compliance:** Local Bootstrap 5 stylesheet; semantic HTML headings/sections; separated commented HTML, CSS and JavaScript; responsive desktop/tablet/phone layout; focus styles, keyboard-accessible controls and native dialogs. A local Canvas chart fallback is included when the optional Chart.js CDN cannot load. Manual tests should confirm all interactions in the target browser (Chrome/Edge) using Live Server.


## Editorial polish (1.4.1)

- Login no longer displays implementation notes below the sign-in form. Credentials remain prefilled for straightforward access.
- About now includes seven practical perfume-care questions, implemented as accessible native HTML `<details>` / `<summary>` accordions.
- Contact no longer calls the website a front-end project in user-facing text; its copy-only message workflow remains transparent.
- Removed accidentally duplicated `<!doctype html><html>` opening tags from `about.html` and `contact.html`.

Fragrance-care editorial references (the site is not a medical or product-authority source):
- Mugler, application and fragrance storage: https://www.mugler.com/mugler-mag/inspiration/tips-on-how-to-apply-perfume/how-to-apply-perfume.html
- Rabanne, perfume application and clothing precautions: https://www.rabanne.com/ww/en/the-rabanne-edition/article/fragrance/how-to-apply-perfume
- Basenotes, production maceration versus home bottle resting: https://basenotes.com/articles/stop-home-macerating-your-shop-bought-perfume-a-fragrance-expert-explains-why.20733/


## Phase 1.5 — Local perfume image support

Fragrance imagery for Catalogue, Owned, Wishlist, Details, Dashboard Recent and Scent Finder uses local paths from `js/data.js` with a shared rendering utility in `js/app.js`. No external product-photo URL is used by the runtime.

**Completed:** All **72 user-supplied JPG product images** are included in `assets/images/perfumes/`, numbered `sv-001.jpg` to `sv-072.jpg`. See `assets/images/perfumes/IMAGE_MAPPING.csv` for the image-to-fragrance mapping and the original uploaded filenames. The website needs no internet connection to display these product pictures. A neutral text fallback is kept only for missing or unreadable files.

This update leaves the original 24 brands, 72 fragrances, 12 owned records, fixed price defaults, dropdown navigation and in-memory editing behavior unchanged.


## Branded bottle visual

The login and dashboard hero use `assets/images/scentvault-branded-bottle.jpg`, an original promotional illustration featuring the gold SCENTVAULT wordmark on the black bottle. The About image now also uses the branded SCENTVAULT bottle visual. The local catalogue-photo folder now contains 72 user-supplied perfume images. Blanco perfume names were updated to Most Wanted, Captivate and Ovanilla; non-verified specifications for new names must be checked before publishing.


## Black marble visual accents

The site uses a **local** decorative marble texture at
`assets/images/black-marble.webp` on selected pre-existing dark surfaces:
sidebar, Dashboard Scent Finder and dark KPI tile, About CTA, and Contact side panel.
All other content remains on warm ivory for contrast and legibility. No remote
image dependency was added. The marble texture is a generated decorative asset,
not a fragrance product photo. The existing branded perfume bottle is unchanged.


## Phase 1.5 — User-uploaded photo completion

Uploaded `GAMBAR MINYAK WANGI WEBSITE.zip` was matched by perfume ID against all 72 catalogue entries. Every image is saved locally under `assets/images/perfumes/`, as `sv-001.jpg` … `sv-072.jpg`. See `IMAGE_MAPPING.csv` for the correspondence between the uploaded filename, fragrance brand/name, and stored file. No product image is loaded from a remote image URL. For offline fonts, the webpage still requests Google Fonts when connected, falling back to local fonts without internet; core Bootstrap and Charts have local assets/fallbacks. The user supplied product photographs; rights to republish publicly should be checked before GitHub Pages deployment.
