The source code of Tech SHEssions. This project contains the source code of a website based on [hugo](https://github.com/gohugoio) and [node-sass](https://github.com/sass/node-sass). 

```bash
# Install hugo
snap install hugo
# do not use apt-get - it has an old version of hugo

# Install node depenedencies
npm i

# Run the server. This does not write the hugo output to disk. 
npm run watch

# Launch the tests (build, run server and search for broken links)
npm run test

# Build the documentation and save the generated HTML and CSS into /_build
npm run build
```

To deploy, we use the contents located on `/_build`

```bash
# Deploy on GitHub Pages
bin/deploy
```

## Things you should know

- Internationalization (i18n) is located in the [i18n](i18n) directory. Usually, most of the texts only need to be updated in this files.

- Next edition. In [config.toml](config.toml) we have two params:

  - RegistrationLink: the link to the page where someone can register for the next edition.

  - ShowNextEdition: When this param has a value (true, for example), we show the `NextEdition` entry (inside i18n files) as a message in several places of the web, linking to the `RegistrationLink` page. Use blank string ('') to hide this message.

- Mentors and mentees are inside [data/members.yaml](data/members.yaml). The avatar should be a filename located at [static/img/members/original](static/img/members/original), but we show a default avatar if we do not find the image. Images must be squared and have min 200px. Tiwtter account is not required.

- Collaborators. Same as mentors/mentees, but the info file is [data/collaborators.yaml](data/collaborators.yaml) and images should be located at [static/img/collaborators/original](static/img/collaborators/original).

- Menu: Links are extracted from [data/menu.yaml](data.yaml). Additionally, we will always add a language link.

- Footer ([data/footer.yaml](data/footer.yaml)): Here we specify the first footer links. If one link name should not be translated, you must specify a `i18n: false` entry in the item. Usually, links will just work (I mean, it doesn't matter if it is a relative link or an absolute link). If an external link does not work (for example, "mailto" links), add an `absolute: true` entry.

- Stats are extracted from [data/members.yaml](data/members.yaml) info.

- Womens in tech. In the [404 page](layouts/404.html) we show a random entry of the [data/womensintech.json](data/womensintech.json) file. Maybe you want to add more womens entries. We assume the info is from Wikipedia. If it is not the case, please ping me to support the use case.
