# DJ Artwork Generator

This repository hosts a static DJ Artwork Generator that:
- Loads a Photoshop template (`template.psd`) with PSD.js
- Fetches show data from a Google Apps Script JSON endpoint
- Renders dynamic text and images onto an HTML5 canvas
- Allows downloading the generated artwork as a PNG

## Project Structure

```
my-dj-artwork/
├── public/
│   ├── template.psd         # Your Photoshop template
│   ├── fonts/
│   │   ├── NeueHaasDisplayThin.ttf
│   │   └── … (all your font files)
│   └── index.html           # Main generator HTML page
├── vercel.json              # Vercel config for CORS & headers
└── README.md                # This file
```

- **public/**: All static assets. Vercel serves these at the root of your domain.
- **template.psd**: The PSD template parsed by PSD.js. Must live in `public/`.
- **fonts/**: Custom font files loaded via CSS/FontFace.
- **index.html**: The single-page app for generating artwork.
- **vercel.json**: Adds CORS headers to allow PSD.js to fetch `template.psd`.
- **README.md**: Project overview and deployment instructions.

## Deployment on Vercel

1. **Connect** this repo to Vercel (via GitHub/GitLab/Bitbucket).
2. Ensure **Root Directory** is set to `/` and **Output Directory** left blank.
3. Vercel will serve `public/index.html` at `https://<your-app>.vercel.app/`.
4. Confirm in DevTools → Network that `template.psd` is served with:
   - `access-control-allow-origin: *`
   - `content-type: application/vnd.adobe.photoshop`

## Embedding in Squarespace

Use a Code Block in Squarespace:

```html
<div style="position:relative; width:100%; padding-bottom:100%; overflow:hidden;">
  <iframe
    src="https://<your-app>.vercel.app/"
    style="position:absolute; top:0; left:0; width:100%; height:100%; border:none;"
    allow="clipboard-write"
  ></iframe>
</div>
```

This will embed the generator—every push to Vercel instantly updates the iframe content.

## License

MIT © Your Name
