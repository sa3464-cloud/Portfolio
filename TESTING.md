# Portfolio Site Test Plan and Results

## Scope

The site is a single page: `https://sa3464-cloud.github.io/Portfolio/`. Its in-page destinations are `#home`, `#about`, `#project`, `#skills`, and `#contact`. Run the viewport and keyboard checks at 390 x 844 (phone) and 1366 x 768 (laptop).

Results below were collected on 2026-10-29. Live response and asset checks used the published GitHub Pages URLs. `Blocked` means the browser interaction or Lighthouse check could not be executed in this environment; it does not indicate a site failure. No forms exist on the site, so form validation is not applicable.

## Test cases

| Test ID | What you are testing | Steps to run the test | Expected result | Actual result |
| --- | --- | --- | --- | --- |
| T1 | Live page availability | Request the live site URL. | The page responds with HTTP 200 and the portfolio title. | Pass - HTTP 200; title is Seth Abram Engineering Portfolio. |
| T2 | Navigation destinations | Read every in-page navigation href and compare it with an element ID in the live HTML. | Every navigation target exists on the page. | Pass on live rerun - all 5 unique destinations (`#home`, `#about`, `#project`, `#skills`, `#contact`) have matching IDs. |
| T3 | Desktop navigation interaction | At 1366 x 768, click About, Projects, Skills, and Contact. | Each link moves to its matching section. | Blocked - browser interaction runtime unavailable. |
| T4 | Phone navigation interaction | At 390 x 844, open Menu and select each navigation item. | Each item reaches its section and closes the menu. | Blocked - browser interaction runtime unavailable. |
| T5 | Phone layout | Open the live page at 390 x 844 and inspect header, hero, About, Projects, Skills, and Contact. | Content fits the screen width, stacks cleanly, and has no horizontal overflow. | Blocked - viewport rendering could not be inspected. The live CSS contains a 720px responsive breakpoint. |
| T6 | Laptop layout | Open the live page at 1366 x 768 and inspect all sections. | Content uses the available width cleanly and remains readable without overlap. | Blocked - viewport rendering could not be inspected. |
| T7 | Mobile menu JavaScript | At phone width, open and close the menu; also press Escape while it is open. | Menu visibility, label, and `aria-expanded` update correctly; Escape closes it. | Blocked - JavaScript interaction could not be executed. |
| T8 | Theme JavaScript and persistence | Toggle dark theme, reload, then toggle back to light theme. | Theme, label, `aria-pressed`, and stored preference update correctly. | Blocked - JavaScript interaction could not be executed. |
| T9 | Dynamic footer year | Load the live page and inspect the footer year. | The year is set to the current year by JavaScript. | Blocked - JavaScript execution could not be inspected in a browser. |
| T10 | Form validation | Look for forms and, if present, submit valid and invalid values. | Any form accepts valid input and gives useful errors for invalid input. | N/A - this site has no forms. |
| T11 | Keyboard navigation | At phone and laptop widths, use Tab, Shift+Tab, and Enter through navigation and all interactive links and buttons. | Every control is reachable, focus is visible, Enter activates links and buttons, and focus order is logical. | Blocked - keyboard interaction could not be executed. The served CSS defines `:focus-visible` outlines. |
| T12 | Lighthouse Accessibility score | Run Lighthouse Accessibility on the live page at phone and laptop sizes. Record each score and fix reported issues. | A Lighthouse Accessibility score is recorded for both viewport modes; no score is assumed. | Blocked - mobile audit retry returned HTTP 429 because the API project's daily quota is zero; neither viewport produced a Lighthouse score. |
| T13 | Live stylesheet and project image | Request `styles.css` and `assets/sparks-in-our-interest.jpg` from the live site. | Both assets load successfully. | Pass - stylesheet HTTP 200 (6,605 bytes); image HTTP 200 (314,869 bytes). |
| T14 | Garbled-character regression | Inspect the live HTML footer and project tags for garbled copyright and separator characters. | Copyright and separators render correctly without mojibake. | Pass on retest - no garbled characters found. Initial result before the fix: Fail. |

## Execution notes

- The page source has menu and theme event handlers, but their runtime behavior still needs the browser checks above.
- The previous encoding failure was fixed in commit `6af48f9`; T14 records the failed baseline and passing live retest.
- Latest live rerun on 2026-10-29: page, stylesheet, and project image returned HTTP 200; all 5 unique in-page destinations match live element IDs; no garbled characters were found. No failure was found in the checks that could execute.
- Browser-based tests could not be completed because the browser automation runtime did not start. The Lighthouse check could not be completed because the PageSpeed Insights API returned a quota error. Rerun T3-T12 when browser automation and Lighthouse are available, then replace each Blocked result with the observed result and record any fixes and retests.
