# Sphere Studio — Browser 360° Creator

A free, local-first browser application for guided panorama capture, approximate spherical image compositing, panorama JPEG downloads, browser gallery, and standalone HTML virtual-tour exports. No account, paid SDK, or backend needed.

## Run locally

Serve the folder through localhost (camera APIs require a secure context):

```sh
cd sphere-web
python3 -m http.server 8000
```

Then open http://localhost:8000 . Desktop browsers can import existing equirectangular panoramas. For camera capture on an iPhone, deploy these static files to an **HTTPS** origin such as GitHub Pages, Cloudflare Pages, or Netlify and open the site in Safari. Grant the prompted camera and motion permissions. iOS Safari requires motion permission from a direct user gesture.

## Features

- Guided, 32-position camera capture with manual fallback
- On-device equirectangular JPEG assembly and export
- WebGL touch-and-drag 360° viewer
- Import external 2:1 panoramas
- IndexedDB local panorama gallery
- Multi-scene virtual-tour builder
- Single-file, offline-viewable HTML tour exports and JSON scene manifests

## Limitations / accurate expectations

**This is a functional browser prototype, not photogrammetry-grade panorama stitching.** The browser engine approximates orientation from device motion, projects camera images onto the sphere, averages overlaps and fills small holes. It does *not* identify keypoints, perform bundle adjustment, compensate for parallax, auto-level exposure, or remove moving objects. Large unobserved areas remain dark. The camera's assumed field of view is 69 degrees, which may differ significantly from specific devices. To improve quality, replace the projection routine with an OpenCV/WASM or native stitching engine, or add device-specific camera calibration.

Browser motion sensor axes vary with device orientation and browser implementation. Guided target tracking may not be accurate on some iPhones; manual capture is provided. Large images may exhaust memory on older phones. Storage in IndexedDB can be cleared by the browser or privacy modes. Back up files by downloading them.

## Project files

- `index.html` — Responsive app shell and controls
- `style.css` — Design system, responsive layout
- `app.js` — Capture, stitching, IndexedDB, WebGL preview and standalone export

## Deployment

This is a static site. Upload all 3 files to any HTTPS static web host. No API keys, third-party libraries or cloud database required. Publishing the site does not automatically upload users' photos: everything is processed locally.

## License

MIT. See LICENSE.
