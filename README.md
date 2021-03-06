## Website for curiosityhacked.org

This repository represents the website running at curiosityhacked.org.
Curiosity Hacked is a non profit that focuses on STEAM (science, technology,
engineering, art, and math) education.

### Basic layout

The website is implmented as a [Jekyll](http://jekyllrb.com/) project. Jekyll
is a static site generator that is used to power
[Github Pages](https://pages.github.com/) amongst other things. The basic
layout of this site is several pages (about.html, staff.html, locations.html,
etc) that have a very similar page structure and share a layout
(`_layouts/default.html`). Note that the index.html page has a different
structure and does _not_ share the deault layout. The default layout includes a
header and a footer from the _includes/ directory using the
`{% include header.html %}` Jekyll syntax. Otherwise, these pages are normal
HTML pages. They include "YAML front matter" that declares which layout they use
(none, in the case of index.html), that is delineated by "---" in the top of
each file. This front matter is necessary so that the pages get processed by
Jekyll: otherwise they would be passed through untouched to the final site.

The content of the js/ css/ and images/ directory are copied verbatim to the final site and are available for use in the pages.

### Installing

Jekyll is a Ruby program. Because the site lives on and is served by Github
Pages, the flavor of Jekyll used in the project is based on the 'github-pages'
gem. This gem should be installed using [Bundler](http://bundler.io/). For this
reason, a Gemfile is provided in the repository.

We also recommend the use of [rvm (Ruby Version Manager)](https://rvm.io/) to
manage ruby installations and gemsets. The project includes .ruby-gemset and
.ruby-version files to automatically switch to the proper gemset and Ruby
version when entering the project directory.

What follows are full bootstrap directions. If you already have RVM installed
and running, you can skip them.

First, install RVM by running the script provided on the rvm homepage:
```
$ \curl -sSL https://get.rvm.io | bash -s stable
```

RVM will give you a command to run to initialize it, or you can just reload your
shell.

Next, install Ruby version 2.0.0 with RVM. This might prompt you for a sudoer
password in order to install system dependencies.
```
$ rvm install 2.0.0
```

At this point, if you cd into the directory of this repository, RVM should
automatically create a *gemset* for you. The gemset is a set of gems that are
separate from all other gemsets and Ruby installs in the system. Think of it as
the personal set of libraries and dependencies for this project.
```
$ cd ch-jekyll/
ruby-2.0.0-p481 - #gemset created /home/tmoney/.rvm/gems/ruby-2.0.0-p481@ch-jekyll
ruby-2.0.0-p481 - #generating ch-jekyll wrappers...........
```

Finally, to install Jekyll and the github pages dependencies, run:
```
$ bundle install
```

### Running the site in development mode

To launch a development server that automatically refreshes when the files
are updated, use the following command:

```
$ bundle exec jekyll serve -w
```

This runs the _jekyll_ command with the dependencies installed via Bundler,
using the current directory as the input directory and watching for chnages to
dependent files. Jekyll will immediately build a _site directory, which contains the complete, static site output. This file is already added to .gitignore.

Jekyll also prints out the IP and port that it is listening on:

```
    Server address: http://0.0.0.0:4000
```

You can then visit the site at http://localhost:4000. At this point you can
develop using your favorite text editor, and Jekyll will regenerate the site
incrementally as necessary. To view your changes, simply refresh your browser.


### Deploying the site

Whenever a new revision is pushed to the `gh-pages` branch of this repository,
which is its default branch, the site is automatically rendered using Jekyll by
Github Pages and made available at http://curiosityhacked.github.io/curiosityhacked.org/. This path is aliased from the Curiosity Hacked DNS hosts as 
http://curiosityhacked.org. As well, there is a `CNAME` file in this repository 
which enables the mapping on the Github side.

More information on Github Pages:

* Homepage: https://pages.github.com/
* Guides: https://help.github.com/categories/20/articles
* Custom domains: https://help.github.com/articles/setting-up-a-custom-domain-with-github-pages