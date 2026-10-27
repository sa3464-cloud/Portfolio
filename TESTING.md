# Portfolio Site Test Plan

This plan covers the single-page portfolio in `index.html` and its styles in `styles.css`. The current results below are based on source inspection. Browser-only behavior should be rerun manually in a browser at desktop and mobile widths before release.

## Test cases

| Test ID | What you are testing | Steps to run the test | Expected result | Actual result (Pass or Fail) |
| --- | --- | --- | --- | --- |
| T1 | Page title and document language | Open `index.html` and inspect the document `<html>` and `<title>` elements. | The page language is English and the title identifies Seth Abram's engineering portfolio. | Pass |
| T2 | Responsive viewport setup | Inspect the page `<head>` for the viewport meta tag. | The viewport width follows the device width and uses an initial scale of 1. | Pass |
| T3 | Main navigation targets | Click About, Projects, Skills, and Contact in the navigation. | Each link scrolls to a section with the matching `id`. | Pass |
| T4 | Hero project call to action | Click "See my projects." | The browser navigates to the Projects section. | Pass |
| T5 | About content | Scroll to About and review its cards. | Background, education, and interests are present with headings and readable descriptions. | Pass |
| T6 | Project cards and external links | Scroll to Projects and inspect all cards and their links. | Three project cards are present, each with a title, description, and relevant project link. | Pass |
| T7 | Project image accessibility | Inspect the project visuals with a screen reader or DOM inspector. | The SVG visuals have accessible titles, and the project photograph has descriptive alternative text. | Pass |
| T8 | Skills section | Navigate to Skills and review the list. | The technical skills and experience appear in a semantic list. | Pass |
| T9 | Contact actions | Navigate to Contact and inspect the email, phone, and LinkedIn links. | Email uses `mailto:`, phone uses `tel:`, and LinkedIn opens an external destination safely. | Pass |
| T10 | Mobile navigation menu | At a viewport of 720px or narrower, activate Menu, choose a navigation link, then reopen the menu and press Escape. | The menu opens and closes, `aria-expanded` stays in sync, and Escape closes the open menu. | Pass |
| T11 | Theme toggle and saved preference | Activate "Use dark theme," reload the page, then activate "Use light theme." | The theme changes, the pressed state and button label update, and the selected theme is saved in local storage. | Pass |
| T12 | Keyboard focus visibility | Use Tab and Shift+Tab to move through links and buttons. | Focus is visible on interactive controls with a clear outline. | Pass |
| T13 | Reduced motion preference | Enable reduced motion in the operating system or browser, then navigate using an in-page link. | In-page scrolling does not use smooth animation. | Pass |
| T14 | Footer character encoding | Open the page and inspect the footer copyright text and separators. | Copyright and separator characters render cleanly without replacement or mojibake characters. | Fail |

## Notes

- T14 fails source inspection: the footer and project tags contain mojibake where copyright and middle-dot separators should appear. Correct the text or encoding, then rerun this test.
- The Pass results indicate that the relevant structure or interaction logic is present in the source; they are not a record of cross-browser or assistive-technology execution. Follow the steps above in a browser to validate the rendered site.
