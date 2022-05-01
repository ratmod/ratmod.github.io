# Readme

Docs for Ratmod

[https://ratmod.github.io](https://ratmod.github.io)

If you have any feedback or an issue, feel free to create an issue in the repository. Please keep it to issues about the documentation, not about any ratmod bugs/etc.

---

## Build

If you are building this documentation it is done with mkdocs. You can install the necessary theme into a python venv:

	mkdir env
	python3 -m venv env
	source env/bin/activate
	pip install mkdocs-bootswatch

Then simply:

	mkdocs build

or:

	mkdocs serve

### Deploy

You must use the master branch for the build as github won't allow using other branches for github pages on the main organization page:

    mkdocs gh-deploy -b master

Use the 'edit' branch for editing/pushing changes etc. The master branch is only for the pushed build.

