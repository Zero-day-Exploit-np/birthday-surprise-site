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

### Configure gallery photos

Add photo entries to the `photos` array. New entries are rendered automatically; no HTML or JavaScript change is needed:

```json
"photos": [
  {
    "url": "https://your-image-host.example/photos/photo1.jpg",
    "caption": "My favorite memory",
    "date": "",
    "alt": "A special memory together"
  },
  {
    "url": "https://your-image-host.example/photos/photo2.webp",
    "caption": "A beautiful day",
    "date": "Summer 2025",
    "alt": "A beautiful day together"
  }
]
```

Use a direct, publicly reachable image URL: upload the image to an image host, object-storage bucket, CDN, or your own website, then copy the URL that points directly to the image file. Test it by opening the URL in a private browser window. The URL should return the image itself, not an HTML preview page, login page, or share page. JPG, JPEG, PNG, WebP, GIF, and other browser-supported formats are accepted. Keep `date` empty when no date label should be shown. Use `alt` to describe the image for visitors using assistive technology.

Unavailable URLs are converted into a friendly placeholder. An empty `photos` array displays an empty-gallery message. Captions, dates, and alt text are inserted as text rather than HTML.

### Configure music

Set the music source and loop behavior in the single `music` object:

```json
"music": {
  "src": "https://your-audio-host.example/audio/birthday-music.mp3",
  "loop": true,
  "enabledByDefault": false
}
```

The provided `HAPPY BIRTHDAY INSTRUMENTAL.mp3` is used by default. The actual audio element receives the configured `loop` value. Playback still requires the visitor to choose **Enter with music** or explicitly press Play; pausing never automatically restarts the song. Missing or unsupported audio shows a usable error state without blocking the page.

## Audio behavior

The opening screen is a custom choice screen, not a browser permission dialog. No audio playback is attempted before a visitor chooses. Music playback is attempted only after **Enter with music**. **Enter without music** keeps audio silent until a visitor uses a music control. The choice is stored in `sessionStorage` for the current visit. Set `"loop": true` in `music` to repeat continuously while playing.

## Deployment

The existing website repository is `https://github.com/Zero-day-Exploit-np/birthday-surprise-site`. GitHub Pages and Netlify can deploy this folder as a static site. Keep `index.html`, `content/`, `content.js`, and the audio/image assets together.

Separate CSS/JS repositories were not created because GitHub CLI/authentication is unavailable in this environment. Splitting the current inline CSS and JavaScript into independently deployed repositories would add external runtime dependencies without improving this static site; a future split should use versioned release assets or GitHub Pages URLs rather than repository HTML URLs.
