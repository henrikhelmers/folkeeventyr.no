# Folkeeventyr.no

Norske folkeeventyr med illustrasjoner fra Asbjørnsen og Moe sin tid. Bygget med Jekyll og publisert på <https://folkeeventyr.no>.

## Kom i gang

Krever Ruby 3.3.

```sh
bundle install
bundle exec jekyll serve
```

Slik bygger og sjekker du som CI gjør:

```sh
JEKYLL_ENV=production bundle exec jekyll build --baseurl ""
bundle exec htmlproofer _site --disable-external --allow-missing-href
```

Hver push til `main` bygges, lenkesjekkes og publiseres via GitHub Actions.

## Innhold

- `_posts/`: ett eventyr per fil, `1111-11-11-<slug>.md`.
- `_data/images.yml`: tittel, kunstner og annen info om hvert bilde i `images/`.
- `_data/image_sizes.yml`: bildestørrelser. Generer på nytt med `bin/image-sizes` (krever ImageMagick) når du legger til bilder.
- `<tag>/index.html`: én side per tag, med `layout: tag_index`.
