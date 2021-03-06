# Fyde Documentation

![Fyde](imgs/fyde-logo.png)

- Website: <https://fyde.com>
- Documentation: <https://fyde.github.io/docs>

## Test locally

This documentation uses [Jekyll](https://jekyllrb.com/) as a static website
generator. Changes to `master` automatically get deployed to github pages.

### Docker

First, build the docker container locally:

```sh
docker build -t fyde-docs .
```

Next, serve the project:

```sh
docker run -v "$PWD:/srv/jekyll" \
  -p 4000:4000 -p 35729:35729 fyde-docs \
  jekyll serve --incremental --livereload
```

Open your browser on <http://localhost:4000/docs/>.

### macOS

First, install the required dependencies.
This installation requires [brew](https://brew.sh/):

```sh
brew install rbenv ruby-build
rbenv install 2.5.1
rbenv local 2.5.1
gem install bundler
bundle install
```

Next, serve the project:

```sh
bundle exec jekyll serve --livereload
```

Open your browser on <http://localhost:4000/docs/>.
