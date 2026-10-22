# Birthday Surprise Website

A static, vanilla HTML/CSS/JavaScript birthday experience with an audio-choice opening screen, responsive gallery, cake interaction, love letter, timeline, and final surprise.

## Run locally

Serve the project over HTTP so `content/birthday.json` can load:

```bash
python3 -m http.server 8000
```

Open <http://localhost:8000>.

## Edit the experience

Edit [`content/birthday.json`](content/birthday.json) for recipient text, opening copy, music, gallery captions and paths, timeline entries, letter content, and footer copy. The provided `content.js` remains a fallback for direct `file://` previews.

Place permitted local images under an `assets/` directory and reference them from the JSON. The supplied `HAPPY BIRTHDAY INSTRUMENTAL.mp3` is used by default.

## Audio behavior

The opening screen is a custom choice screen, not a browser permission dialog. No audio playback is attempted before a visitor chooses. Music playback is attempted only after **Enter with music**. **Enter without music** keeps audio silent until a visitor uses a music control. The choice is stored in `sessionStorage` for the current visit.

## Deployment

The existing website repository is `https://github.com/Zero-day-Exploit-np/birthday-surprise-site`. GitHub Pages and Netlify can deploy this folder as a static site. Keep `index.html`, `content/`, `content.js`, and the audio/image assets together.

Separate CSS/JS repositories were not created because GitHub CLI/authentication is unavailable in this environment. Splitting the current inline CSS and JavaScript into independently deployed repositories would add external runtime dependencies without improving this static site; a future split should use versioned release assets or GitHub Pages URLs rather than repository HTML URLs.
