# Hanze openEHR workshop

[![Jupyter Book Badge](https://jupyterbook.org/badge.svg)](https://github.com/sophiedkk/openEHR-Hanze)

Source for the documentation (under workshop) and slides (under slides) for the Hanze openEHR workshop.

The goal of this workshop is to get familiar with the base concepts of openEHR and how to interact
with openEHR based systems.

## Build

The documentation was built with Jupyter book. To create your own build first clone the project:

```shell
git clone <this repo>
```

Ensure you have [uv](https://docs.astral.sh/uv/) installed on your system. Then run the Jupyter book build command with uv:
```shell
uv run jupyter-book build workshop/
```

You can find the generated html under `workshop/build/html`. The `index.html` file is the entrypoint
to your book.
