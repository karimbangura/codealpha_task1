# codealpha_task2
# Photo Gallery
A responsive photo gallery I built with plain HTML, CSS and JavaScript. No libraries, no frameworks, just three files and a folder of images.

You can filter the photos by category, click any photo to open it full screen, and flip through the set with buttons, arrow keys or a swipe.

![alt text](<image.png>)


## What it does

- Grid layout that adjusts to the screen size, from one column on a phone to four or more on a wide monitor
- Category filters: All, Nature, City, Animals and Technology, each with a live photo count
- Lightbox (full screen viewer) with a caption and a counter like `3 / 12`
- Next and previous buttons, and they wrap around, so after the last photo you go back to the first
- Next and previous only go through the photos in the category you picked
- Hover effects: the card lifts, the photo zooms in slightly, the border turns yellow and the caption slides up
- Smooth transitions everywhere: cards fade when you filter, the lightbox fades in, and photos fade when you change them
- Dark, high contrast design with a yellow accent
- Works with the mouse, the keyboard and touch


## How it works

Every photo card in `index.html` has a `data-category` attribute, like `data-category="nature"`. The filter buttons have a matching `data-filter` attribute.

`script.js` does the rest:

- `applyFilter()` fades out the cards that don't match, hides them after the fade, and updates the "Showing N photos" line.
- `visibleCards()` returns only the cards currently shown. The lightbox uses this list, which is why next and previous stay inside the chosen category.
- `show()` swaps the photo, caption and counter, and wraps around at both ends.
- `openLightbox()` and `closeLightbox()` handle opening, closing, scroll locking and focus.

I also used `loading="lazy"` on the photos, and the lightbox preloads the next and previous photo, so flipping through feels instant.

## Task checklist

- [x] Image gallery using an HTML and CSS layout
- [x] JavaScript navigation: next and previous buttons
- [x] Lightbox view
- [x] Hover effects and smooth transitions
- [x] Responsive design for different screen sizes
- [x] Bonus: categories and filters


## Ideas for later

- Masonry layout with photos of different heights
- Zoom and pan inside the lightbox
- A slideshow button that plays through the photos automatically
- A search box on top of the category filters