# ScentVault product photos — locally included

This folder includes **72 user-uploaded JPG photographs**, one for each perfume in the catalogue.

- Filenames `sv-001.jpg` to `sv-072.jpg` match `catalogue` records defined in `js/data.js`.
- `IMAGE_MAPPING.csv` maps each perfume to its original uploaded filename.
- Photos display without internet access in Full Catalogue, Owned, Wishlist, Dashboard and Perfume Details.
- They are locally served by Live Server; no image URLs, browser storage or external image API is required.
- To replace a photo, overwrite the corresponding `sv-###.jpg` with an image of the **same fragrance**. Hard-refresh the browser afterwards.

The images are provided by the user. Before publishing the site publicly, check that each image may be used or redistributed.
