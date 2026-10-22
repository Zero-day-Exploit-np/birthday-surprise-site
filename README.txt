BIRTHDAY SURPRISE WEBSITE

FILES
- index.html: website layout, styles, animations and behavior.
- content.js: edit this file to change the wording, letter, photo captions, timeline text and optional song path.
- content/birthday.json: central editable content loaded when the site is served over HTTP. content.js remains as an inline fallback for file:// previews.
- assets/: place your music and image files here (create this folder).

EDIT TEXT
Open content.js in a text editor and change the text between quotes/backticks. Keep commas between fields. For a quote inside a quoted string, use \". The letterText uses backticks and can contain apostrophes and new lines.

ADD PHOTOS
Option A: open the website and use “Add our photos” and the hero photo area. These previews are temporary for that browser session.
Option B: put images in assets/ and set each memories item image to a path such as "assets/photo1.jpg" in content.js. To set the main hero photo permanently, change the hero image in index.html or ask for a follow-up customization.

ADD MUSIC
Set audioSrc in content/birthday.json to the relative path of your audio file. The included configuration points to the provided "HAPPY BIRTHDAY INSTRUMENTAL.mp3" file. You can instead create an assets folder beside index.html and use a path such as "assets/our-song.mp3".

MUSIC CONSENT
The opening screen is a custom audio-choice screen, not a browser permission request. No audio is attempted before a choice is made. “Enter with music” stores the choice for the current browser tab session and attempts playback only after the tap. If playback fails, the visitor still enters and can use “Start birthday music.” “Enter without music” keeps the player silent until the visitor explicitly presses a music control.

CAKE CUTTING
Tap “Cut the cake” to play the knife and slice animation. Tap “Reset cake” to replay it.

TEST LOCALLY
Keep index.html and content.js together. For reliable local testing, open a terminal in this folder and run:
  python3 -m http.server 8000
Then visit http://localhost:8000
Serving the folder is required for content/birthday.json to load; opening index.html directly still uses the content.js fallback.

OPENING EXPERIENCE
The first screen asks whether the visitor wants music. Both choices always open the website, and the choice is stored only in sessionStorage for the current visit.

PHOTO LIGHTBOX
Click or focus a loaded gallery photo to open the viewer. Use the previous/next buttons, swipe left/right on touch devices, or the Left/Right arrow keys. Press Escape to close it.

HOSTING
Upload index.html, content.js, and the assets folder together to GitHub Pages or Netlify. Keep the same folder structure.
