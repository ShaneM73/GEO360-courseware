# GEO360-courseware

Interactive teaching modules for **GEO 360 – Aerial Photo Interpretation**, integrated into a single web app with a guided learning path.

Open `index.html` (or the GitHub Pages URL) to start. Every module is also a standalone page in `modules/` and can be linked or projected on its own.

## Learning path

| # | Unit | Module | File |
|---|------|--------|------|
| 1 | Geometric Foundations | Similar Triangles | `modules/01-similar-triangles.html` |
| 2 | Geometric Foundations | Geometry on a Sphere (spherical triangle) | `modules/02-spherical-triangle.html` |
| 3 | Image Acquisition | SLR vs Mirrorless Exposure | `modules/03-camera-exposure.html` |
| 4 | Image Acquisition | GPS Trilateration | `modules/04-gps-trilateration.html` |
| 5 | Image Acquisition | Drone Flight Mission Planner | `modules/05-mission-planner.html` |
| 6 | Photo Geometry & Measurement | Relief Displacement (d = hr/H) | `modules/06-relief-displacement.html` |
| 7 | Photo Geometry & Measurement | Relief Patterns & Terrain | `modules/07-relief-patterns.html` |
| 8 | Photo Geometry & Measurement | Stereo Vision & Parallax | `modules/08-stereo-parallax.html` |

**Why this order:** similar triangles give photo scale (f/H) → the sphere module shows where flat-plane geometry stops working → the camera and GNSS modules explain how a photo and its position are captured → mission planning combines scale, footprint and overlap → relief displacement is the first geometric distortion in a single photo → parallax between overlapping photos (whose air base comes from forward overlap) recovers height.

`data/spherical-triangle.kml` is the original Google Earth file for Module 2 (downloadable from inside the module).

## Repository layout

```
index.html            course shell: navigation, lesson briefs, progress
modules/              one self-contained HTML file per module
data/                 supporting data (KML)
.nojekyll             serve files as-is on GitHub Pages
```

## Publish on GitHub Pages

1. Push this folder to the `GEO360-courseware` repository.
2. **Settings → Pages → Build and deployment → Deploy from a branch**, choose `main` and `/ (root)`.
3. The site appears at `https://<your-username>.github.io/GEO360-courseware/`.

Deep links work per module, e.g. `.../GEO360-courseware/#/stereo-parallax`.

## Adding or reordering modules

Put the new HTML file in `modules/`, then add an entry to the `MODULES` array near the top of the script in `index.html` (slug, unit, file, title, objectives, connection, activity). The sidebar, overview page and Prev/Next order all follow that array.

## Notes

- No build step and no external dependencies; everything runs offline from the files.
- "Explored" progress is stored in the student's browser (localStorage) only.
- Opening `index.html` directly from disk works in most browsers; if a browser blocks the module frames on `file://`, serve locally with `python -m http.server` and visit `http://localhost:8000`.
