# gks-starter-repo (REMOVE THIS SECTION AFTER CUSTOMIZING)
This is a template github repository for others to copy and use as a starter to develop 
and share their own extensions and profiles from the GA4GH Genomic Knowledge Standards (GKS).

The instructions below are for copying this repo to make it your own. Once you have done that
you should replace this top-level heading in this README.md file with information about your
specific schema and project.

You will want to replace all the YOUR_GITHUB_ID and YOUR_PROJECT tags below with your github project id and github project or repo name.

You will also want to go through the schema folder and change all the references to `my-project` in folder names, file names and file content to YOUR_PROJECT.

This starter GA4GH GKS repo is set up to refere va-spec and all the submodules nested within it. If you wish to only use a subset of the GKS projects starting at cat-vrs and lower you may want to change the submodule configuration. But it is not necessary.


<--- Remove this line and all the above from the README.md before saving your copy and sharing.
# YOUR_PROJECT 
<add a description of your specific project here and remove everthing above this header to initialize>


## Using the schema

The schema is available in the [schema/](./schema/) directory, in both yaml and json versions. 
It conforms to JSON Schema Draft 2020-12. For a list of
libraries that support JSON schema, see
[JSONSchema>Tools](https://json-schema.org/tools).

## Installing for development

Fork the repo at <https://github.com/YOUR_GITHUB_ID/YOUR_PROJECT>.

    git clone --recurse-submodules git@github.com:YOUR_GITHUB_ID/YOUR_PROJECT.git
    cd YOUR_PROJECT
    make devready
    source venv/3.12/bin/activate
    pre-commit install

If you already cloned the repo, but forgot to include `--recurse-submodules` you can run:

    git submodule update --init --recursive

## Contributing to the schema

YOUR_PROJECT uses [YOUR_PROJECT-source.yaml](./schema/YOUR_PROJECT/YOUR_PROJECT-source.yaml) as the source document for JSON Schema.

To create the corresponding def and json files after making changes to the source document, from the root directory:

    cd schema
    make all

> *Note: We have a custom pre-commit hook to run these commands after you stage a source
> document*

## Contributing to the docs

The YOUR_PROJECT specification documentation is written in reStructuredText and located in [docs/source](docs/source/). Commits to this repo are built automatically at <https://YOUR_RTD_URL>.

To build documentation locally, you must install [entr](https://eradman.com/entrproject/):

    brew install entr

Then from the root directory:

    cd docs
    make clean watch &

Then, open [docs/build/html/index.html](./docs/build/html/index.html). The above make
command should build docs when source changes. (Some types of changes require recleaning and building.)

## Testing

The VRS repo contains two kinds of tests. Basic smoke tests in [tests/](./tests/) ensure that the
schema is parsable and works with certain tools. These tests provide a basic sanity
check during development.

Validation tests (in [validation/](./validation/)) provide language-neutral tests for those
implementing tools with YOUR_PROJECT.

To run the smoke tests:

    make test