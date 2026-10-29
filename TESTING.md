# Portfolio Test Cases and Results

## Scope

These test cases cover the single-page portfolio, its navigation and theme source, responsive styles, and optimized project image. Results were collected on 2026-10-29 against the local repository files. The source and asset assertions passed; browser interaction and a fresh Lighthouse run were not part of this execution.

## Test cases

| Test ID | What you are testing | Steps to run the test | Expected result | Actual result |
| --- | --- | --- | --- | --- |
| T1 | HTML doctype and language | Open `index.html`; check the first document declarations. | HTML5 doctype and `lang="en"` are present. | Pass |
| T2 | Responsive viewport metadata | Inspect the viewport meta element in `index.html`. | Width is set to `device-width` and initial scale is `1`. | Pass |
| T3 | Main navigation targets | Compare each in-page link in the main navigation with the page element IDs. | All four navigation links point to existing IDs. | Pass |
| T4 | Required page sections | Check the document for `home`, `about`, `project`, `skills`, and `contact` IDs. | Every expected section ID exists. | Pass |
| T5 | Featured project count | Count the `article.project` elements in `index.html`. | Exactly three project cards are present. | Pass |
| T6 | Safe external links | Inspect links using `target="_blank"`. | Each external link also uses `rel="noopener noreferrer"`. | Pass |
| T7 | Contact link destinations | Inspect the email and phone links in the Contact section. | Email uses `mailto:` and phone uses `tel:` with the expected addresses. | Pass |
| T8 | Optimized project image dimensions | Read the image file dimensions. | The project photo is 600 × 742 pixels. | Pass |
| T9 | Project image file size | Check the byte size of `assets/sparks-in-our-interest.jpg`. | The file is under 80 KB. | Pass |
| T10 | Project image loading markup | Inspect the project photo element in `index.html`. | Width and height match the file; alt text, lazy loading, and async decoding are present. | Pass |
| T11 | Initial mobile menu state | Inspect the header element before the inline script. | The menu enhancement class is in the initial HTML. | Pass |
| T12 | No late menu enhancement class | Search the inline script for code that adds `menu-enhanced`. | The script does not add the class after page layout. | Pass |
| T13 | Menu toggle accessibility state | Inspect the menu click handler. | It toggles the open class, updates `aria-expanded`, and changes the menu label. | Pass |
| T14 | Escape key menu close behavior | Inspect the Escape key handler. | Escape closes the menu, resets `aria-expanded` and label, and returns focus to the toggle. | Pass |
| T15 | Navigation without JavaScript | Inspect the `noscript` mobile style fallback. | Mobile navigation is visible when JavaScript is disabled. | Pass |
| T16 | Theme toggle accessibility state | Inspect the theme setter and theme button handler. | Theme changes update `aria-pressed` and the button's action label. | Pass |
| T17 | Theme preference persistence | Inspect theme storage reads and writes. | The saved theme is restored and storage errors are caught. | Pass |
| T18 | Responsive section grids | Inspect the max-width 720px media query in `styles.css`. | About and project grids become single-column on narrow screens. | Pass |
| T19 | Reduced motion setting | Inspect the reduced-motion media query. | Smooth scrolling is disabled when reduced motion is requested. | Pass |
| T20 | Keyboard focus visibility | Inspect the `:focus-visible` styles for links and buttons. | Both links and buttons receive a visible focus outline. | Pass |
| T21 | External script and font dependencies | Search the HTML for external script sources and CSS for imported fonts. | No external script or web-font dependency is present. | Pass |

## Execution notes

- Results are based on source and asset assertions run against the local working tree. They verify markup, asset properties, and the presence of interaction logic; they do not claim that browser interactions were exercised.
- The most recent Lighthouse report visible in Chrome scored 69 for mobile Performance, with CLS 0.268 and TBT 690 ms. The image was reduced from 314,869 bytes to 66,980 bytes and the mobile menu enhancement was moved into the initial HTML. Lighthouse has not been rerun since those changes.
- Cache lifetime findings depend on response headers. GitHub Pages does not let this repository configure custom cache headers.
