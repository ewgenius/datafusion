

# DataFusion Documentation

This folder contains the source content of the [User Guide](./source/user-guide)
and [Contributor Guide](./source/contributor-guide). These are both published to
https://datafusion.apache.org/ as part of the release process.

## Dependencies

It's recommended to install build dependencies and build the documentation
inside a Python virtualenv.

- Python
- `pip install -r requirements.txt`

## Build & Preview

Run the provided script to build the HTML pages.

```bash
./build.sh
```

The HTML will be generated into a `build` directory.

Preview the site on Linux by running this command.

```bash
firefox build/html/index.html
```

## Making Changes

To make changes to the docs, simply make a Pull Request with your
proposed changes as normal. When the PR is merged the docs will be
automatically updated.

## Release Process

This documentation is hosted at https://datafusion.apache.org/

When the PR is merged to the `main` branch of the DataFusion
repository, a [github workflow](https://github.com/apache/datafusion/blob/main/.github/workflows/docs.yaml) which:

1. Builds the html content
2. Pushes the html content to the [`asf-site`](https://github.com/apache/datafusion/tree/asf-site) branch in this repository.

The Apache Software Foundation provides https://datafusion.apache.org/,
which serves content based on the configuration in
[.asf.yaml](https://github.com/apache/datafusion/blob/main/.asf.yaml),
which specifies the target as https://datafusion.apache.org/.
