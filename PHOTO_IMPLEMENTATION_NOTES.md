# Phase 1.5 — product image integration

Completed: **72 of 72 catalogue photos** are present as local JPG files.

- Input: user-uploaded `GAMBAR MINYAK WANGI WEBSITE.zip` (72 JPGs).
- Images: `assets/images/perfumes/sv-001.jpg` through `sv-072.jpg`.
- Product mapping and original upload names: `assets/images/perfumes/IMAGE_MAPPING.csv`.
- Rendering: `SV.photo()` in `js/app.js` is shared by the catalogue, Owned, Wishlist, Dashboard, and Details. It keeps a plain text fallback for a missing/unreadable image.
- `js/data.js` now references the 72 local `.jpg` files without any external image URL or persistent browser storage.
- The login and dashboard branded SCENTVAULT bottle remains the existing local visual; the black marble design remains unchanged.

These are the pictures the user provided. Accuracy of visual product variant and public redistribution rights should be verified before going live.
