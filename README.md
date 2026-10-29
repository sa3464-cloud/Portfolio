# Seth Abram | Engineering Portfolio

A responsive, single-page portfolio for Seth Abram, an Electrical and Computer Engineering student at NJIT. It introduces his background, education, technical skills, selected projects, and contact information.

**Live website:** [sa3464-cloud.github.io/Portfolio](https://sa3464-cloud.github.io/Portfolio/)

## View the website locally

1. Clone this repository:

   ```text
   git clone https://github.com/sa3464-cloud/Portfolio.git
   ```

2. Open the repository folder and open `index.html` in a web browser. The stylesheet and project image use relative paths, so the page works directly from the folder.

There is no build step or framework to install.

## Repository files

- `index.html` contains the portfolio content and interactive controls.
- `styles.css` contains the responsive layout, color themes, and focus styles.
- `assets/` contains the project image.
- [AGENTS.md](AGENTS.md) describes the site's purpose, design, and implementation guidance.
- [TESTING.md](TESTING.md) records test cases and the latest checked results.

## Additional notes

The site uses plain HTML, CSS, and JavaScript. Its project cards link to Onshape, Google Colab, and Google Drive. The mobile Lighthouse report recorded a 99 Performance score before the latest project image optimization; see `TESTING.md` for the run details.
