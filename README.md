# Documentation of the Common–EGSE

This repo contains written and generated documentation for the PLATO Common–EGSE project. 


The website is created from the asciidoc files in the `hugo` folder using the [HUGO](https://gohugo.io) static site generator. Make sure HUGO is installed on your system to generate the HTML code. In a terminal go into the `hugo` folder of the project and type
```
$ hugo
```
This will generated the full documentation site in the `docs` folder of the project.

Before committing and pushing the code, you should generate the CGSE manuals. The source for these manuals is located in the `src` folder. The manuals are generated using AsciiDoctor. To create a PDF file for e.g. the developer manual, go into the `src/develop` folder and run the following command:
```
$ asciidoctor-pdf developer-manual.adoc
```
To create the HTML file for this manual use:
```
$ asciidoctor developer-manual.adoc
```
Other manuals are created with the same commands.

Now move the HTML files for each of the manuals to the `docs/asciidocs` folder so they become part of the GitHub pages.

The site also provides the API documentation of the Common-EGSE. This documentation shall be generated in the `plato-common-egse` repository. Go into the `MKDOCS` folder and run the following command:
```
$ pdoc3 --html --output-dir api egse --force
```
The move the `api` folder from the `plato-common-egse` repo into the `docs` folder of this repo.

You are now ready to commit and push the updated documentation or to make a pull request. The site will automatically be uploaded to the GitHub pages and be available at [github.io](https://rhuygen.github.io/plato-cgse-doc/).
