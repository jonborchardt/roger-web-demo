Drop exported Roger A/B "swipe" SVG files here (from Roger Studio's SVG export).
Then add one <div class="compare"> block per file in ../comparisons.html.

IMPORTANT: embed each SVG with <object type="image/svg+xml" data="svg/NAME.svg">,
NOT <img> — an <img>-referenced SVG is script-sandboxed and the swipe will not
animate or respond to interaction. GitHub Pages serves .svg with the correct
MIME type, so <object> works with no extra config.
