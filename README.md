# Documentation of the Common–EGSE

This repo contains written and generated documentation for the PLATO Common–EGSE project. 

UPDATE: use the update_docs command to generate the HTML and PDF files. Make sure you are in the virtual environment.

```
$ source venv/bin/activate
$ ./update_docs.py
```
---

The website is created from the asciidoc files in the `hugo` folder using the [HUGO](https://gohugo.io) static site generator. Make sure HUGO is installed on your system to generate the HTML code. In a terminal go into the `hugo` folder of the project and type
```
$ hugo
```
This will generated the full documentation site in the `docs` folder of the project.

Before committing and pushing the code, you should generate the CGSE manuals. The source for these manuals is located in the `src` folder. The manuals are generated using AsciiDoctor. We use the [asciidoctor-tabs](https://github.com/asciidoctor/asciidoctor-tabs) package to add tabbed code blocks in our documentation. Check it's GitHub pages for installation instructions.

To create a PDF file for e.g. the developer manual, go into the `src/develop` folder and run the following command:
```
$ asciidoctor-pdf -o ../../docs/pdfs/developer-manual.pdf developer-manual.adoc
```
To create the HTML file for this manual use:
```
$ asciidoctor -r asciidoctor-tabs -o ../../docs/asciidocs/developer-manual.html developer-manual.adoc
```
Other manuals are created with the same commands.

Now move the HTML files for each of the manuals to the `docs/asciidocs` folder so they become part of the GitHub pages.

The site also provides the API documentation of the Common-EGSE. This documentation shall be generated in the `plato-common-egse` repository. Go into the root folder of the project and run the following command:
```
$ pdoc3 --html --output-dir api egse --force
```
or
```
$ pdoc3 --html --output-dir ~/Documents/PyCharmProjects/plato-cgse-doc/docs/api egse --force
```
The move the `api` folder from the `plato-common-egse` repo into the `docs` folder of this repo.

If you need to exclude certain modules from the API documentation, create the `__pdoc__` variable in the __init__.py of that module. As an example, exclude the `eksma` module from the `egse.filterwheel`, add the following lines in the `__init__.py` of the `egse.filterwheel` module.

```
__pdoc__ = {
    'eksma': False
}
```

You are now ready to commit and push the updated documentation or to make a pull request. The site will automatically be uploaded to the GitHub pages and be available at [github.io](https://ivs-kuleuven.github.io/plato-cgse-doc/).

If you are using PyCharm, updating this documentation is easiest if you install the `Asciidoc` plugin in PyCharm. That will allow you to generate the HTML and PDF documents with just one click.

##  Updating versions

Where do we need to update versions before pushing changes:
* In each of the main files: icd.adoc, installation-manual.adoc, developer-manual.adoc, and user-manual.adoc
* In the `changelog.adoc` file for each of the manuals
* In the HUGO content `posts` and /or `docs` for those manuals that were updated. 

## Installation of AsciiDoctor on macOS

Make sure you have the `ruby` command from brew in your path instead of the system provided version.

See https://docs.asciidoctor.org/asciidoctor/latest/install/
```
$ brew install asciidoctor
```

Then, install asciidoctor-pdf, see https://github.com/asciidoctor/asciidoctor-pdf
```
$ gem install asciidoctor-pdf
```

Then, install asciidoctor-tabs, see https://github.com/asciidoctor/asciidoctor-tabs
```
gem install [--prerelease] asciidoctor-tabs
```

Install HUGO:
```
$ brew install hugo 
```
