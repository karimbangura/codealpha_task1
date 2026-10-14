# codealpha_task2
# Photo Gallery
A responsive photo gallery I built with plain HTML, CSS and JavaScript. No libraries, no frameworks, just three files and a folder of images.

You can filter the photos by category, click any photo to open it full screen, and flip through the set with buttons, arrow keys or a swipe.

<!-- Add a screenshot: save it as screenshot.png in this folder, then remove these comment marks -->
<!-- ![Gallery screenshot](screenshot.png) -->

## What it does

- Grid layout that adjusts to the screen size, from one column on a phone to four or more on a wide monitor
- Category filters: All, Nature, City, Animals and Technology, each with a live photo count
- Lightbox (full-screen viewer) with a caption and a counter like `3 / 12`
- Next and previous buttons, and they wrap around, so after the last photo you go back to the first
- Next and previous only go through the photos in the category you picked
- Hover effects: the card lifts, the photo zooms in slightly, the border turns yellow and the caption slides up
- Smooth transitions everywhere: cards fade when you filter, the lightbox fades in, and photos fade when you change them
- Dark, high-contrast design with a yellow accent
- Works with the mouse, the keyboard and touch

## How to run

1. Put `index.html`, `style.css` and `script.js` in one folder.
2. Make an `images/` folder next to them and add your photos (see the next section).
3. Open `index.html` in your browser.

You don't need to install anything or run a server. If you use VS Code, the Live Server extension also works.

The font (Bricolage Grotesque) loads from Google Fonts. If you're offline it falls back to your system font and everything still works.

## Folder setup

```
gallery/
├── index.html   the structure: filters, grid, lightbox
├── style.css    the look: layout, hover effects, transitions
├── script.js    the logic: filtering, lightbox, navigation
├── README.md    this file
└── images/
    ├── nature-1.jpg      nature-2.jpg      nature-3.jpg
    ├── city-1.jpg        city-2.jpg        city-3.jpg
    ├── animals-1.jpg     animals-2.jpg     animals-3.jpg
    └── technology-1.jpg  technology-2.jpg  technology-3.jpg
```

Name your photos exactly like this, or open `index.html` and change the `src` and `alt` of each card to match your file names.

If a photo is missing, its card shows a dark tile with the caption, so the layout doesn't break.

Tip: keep each photo around 1200px wide and under about 500 KB. Big photos make the page slow to load.

## Controls

| Action | Mouse / touch | Keyboard |
|---|---|---|
| Filter by category | Click a filter button | Tab to a button, then Enter |
| Open a photo | Click or tap the card | Tab to the card, then Enter |
| Next photo | Click `›` or swipe left | `→` |
| Previous photo | Click `‹` or swipe right | `←` |
| Close the viewer | Click `×` or the dark background | `Esc` |

While the lightbox is open, Tab only moves between its three buttons, so you can't tab into the page behind it. When you close it, focus goes back to the card you opened.

## How it works

Every photo card in `index.html` has a `data-category` attribute, like `data-category="nature"`. The filter buttons have a matching `data-filter` attribute.

`script.js` does the rest:

- `applyFilter()` fades out the cards that don't match, hides them after the fade, and updates the "Showing N photos" line.
- `visibleCards()` returns only the cards currently shown. The lightbox uses this list, which is why next and previous stay inside the chosen category.
- `show()` swaps the photo, caption and counter, and wraps around at both ends.
- `openLightbox()` and `closeLightbox()` handle opening, closing, scroll locking and focus.

I also used `loading="lazy"` on the photos, and the lightbox preloads the next and previous photo, so flipping through feels instant.

## Things I had to handle

- **Missing images.** A broken photo would leave an ugly empty gap, so the card shows a dark tile with its caption instead.
- **No hover on phones.** Touch screens can't hover, so captions are always visible there.
- **Small screens.** Under 600px wide, the lightbox arrows move to the bottom so they don't cover the photo.
- **Page scrolling.** The page behind the lightbox is locked while it's open.
- **Screen readers.** The lightbox is marked as a dialog, the buttons have text labels, and the photo count is announced when you change filters.
- **Reduced motion.** If the system is set to reduce motion, the transitions are switched off.

## Task checklist

- [x] Image gallery using an HTML and CSS layout
- [x] JavaScript navigation: next and previous buttons
- [x] Lightbox view
- [x] Hover effects and smooth transitions
- [x] Responsive design for different screen sizes
- [x] Bonus: categories and filters

## Customizing

- **Add a photo:** copy one `<button class="card">...</button>` block in `index.html`, then change `data-category`, `src`, `alt` and the caption text.
- **Add a category:** add a `<button class="filter" data-filter="food">Food <span class="count"></span></button>` to the `<nav>`, then give your cards `data-category="food"`. The counts and filtering update by themselves.
- **Colors:** change the variables at the top of `style.css` (`--bg`, `--accent` and so on).
- **Card shape:** change `aspect-ratio: 4 / 3` on `.card` to `1 / 1` for squares or `3 / 4` for portrait.
- **Card size:** change the `260px` in the `.grid` rule to make the cards bigger or smaller.

## Ideas for later

- Masonry layout with photos of different heights
- Zoom and pan inside the lightbox
- A slideshow button that plays through the photos automatically
- A search box on top of the category filters

## Author

Built by Bangura.