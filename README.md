# A minimal Binder environment for using DataLad

This repository contains the minimal configuration for a [Binder](https://mybinder.org/)
environment that can run [DataLad](https://www.datalad.org/).

This base environment repository is decoupled from content, allowing it to be maintained separately and preventing updates to content
from triggering a rebuild of the Binder environment instance. 

## Usage

### 1. Empty environment

To use this environment *as is*, visit [![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/jsheunis/datalad-binder/HEAD)

From the menu file browser interface, select `New > Terminal` and explore DataLad in the resulting command-line shell.

### 2. Environment with content

To use this environment with content (such as Jupyter notebooks and/or data), first make this content available via a separate repository.

Then construct a URL from the base environment repository URL and the content repository URL, as follows:

```
https://mybinder.org/v2/gh/jsheunis/datalad-binder/HEAD?urlpath=git-pull?repo=<url-of-your-content-repo>
```

This URL, when opened, will use [nbgitpuller](https://github.com/jupyterhub/nbgitpuller) to automatically pull in content from the specified
repository into the base Binder environment.

For an example of using the base environment with seperate content, visit [![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/jsheunis/datalad-binder/HEAD)

## Configuration

The following files allow Binder to configure the base environment:

- `environment.yml` specifies the required tools/packages that will be installed via [conda-forge](https://conda-forge.org/)
- `apt.txt` specifies the required tools/packages that will be installed via APT
- `postBuild` runs the command to enable the `nbgitpuller` extension

These should only be updated if other packages or extensions are required for the base environment
that allows DataLad to be run in Binder.