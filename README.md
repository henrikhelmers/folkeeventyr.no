# Folkeeventyr.no

Norske folkeeventyr med illustrasjoner fra Asbjørnsen og Moe sin tid. Bygget med Jekyll og publisert på <https://folkeeventyr.no>.

## Kom i gang

Oppsettet forutsetter macOS med [Homebrew](https://brew.sh). `bin/image-sizes` bruker blant annet macOS-varianten av `iconv`.

```sh
brew install ruby@3.3 imagemagick
```

Homebrew legger ikke `ruby@3.3` i PATH. Uten neste linje bruker `bundle` systemets gamle Ruby, og bygget feiler. Legg den gjerne i `~/.zshrc`:

```sh
export PATH="$(brew --prefix ruby@3.3)/bin:$PATH"
```

Installer Bundler-versjonen fra `Gemfile.lock`, så gemene. De havner i `vendor/bundle`.

```sh
gem install bundler:4.0.23
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

- `_posts/`: ett eventyr per fil, `1111-11-11-<slug>.md`. En avslutningsformel som «snipp snapp snute» står i eget avsnitt med `{: .slutt}` på linjen under.
- `_data/images.yml`: tittel, kunstner og annen info om hvert bilde i `images/`.
- `_data/image_sizes.yml`: bildestørrelser. Generer på nytt med `bin/image-sizes` (krever ImageMagick) når du legger til bilder.
- `<tag>/index.html`: én side per tag, med `layout: tag_index`.
