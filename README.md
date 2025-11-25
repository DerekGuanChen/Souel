# Souel

This is a tiny single-file React/Tailwind prototype shipped as a static page.

Automatic deployment
- The repository is configured with a GitHub Actions workflow (.github/workflows/deploy-pages.yml) that automatically builds and deploys the repo contents to GitHub Pages on every push to `main`.
- Live preview: https://derekguanchen.github.io/Souel/

Local preview
- For quick local testing, run:

```bash
python3 -m http.server 8000
# open http://localhost:8000
```