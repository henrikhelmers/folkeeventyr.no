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
bin/check
```

`bin/check` kjører html-proofer og fanger i tillegg filnavn i feil Unicode-form, utdaterte bildestørrelser, tagger som ikke er lister, bildeinkluderinger som ikke viser noe og sider som mangler i sitemapen.

Hver push til `main` bygges, sjekkes og publiseres via GitHub Actions.

## Innhold

- `_posts/`: ett eventyr per fil, `1111-11-11-<slug>.md`.
- `_data/images.yml`: tittel, kunstner og annen info om hvert bilde i `images/`.
- `_data/image_sizes.yml`: bildestørrelser. Generer på nytt med `bin/image-sizes` (krever ImageMagick) når du legger til bilder.
- `<tag>/index.html`: én side per tag, med `layout: tag_index`.
