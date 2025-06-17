# Python Pip Preinstall Buildpack

A Cloud Native Buildpack that preinstalls Python libraries during the build phase to improve application startup times.

Requires Python layer to be already installed. You can use the following buildpacks:

- [Python Buildpack](https://github.com/paketo-buildpacks/python)
- [Pip Buildpack](https://github.com/paketo-buildpacks/pip)
- [Pip-Install Buildpack](https://github.com/paketo-buildpacks/pip-install)



## Usage

Set the `BP_PREINSTALL_PYTHON_LIBS` environment variable to specify which Python packages to preinstall:

```bash
pack build myapp --env BP_PREINSTALL_PYTHON_LIBS="requests numpy pandas"
```

## Configuration

| Environment Variable | Description | Default |
|---------------------|-------------|---------|
| `BP_PREINSTALL_PYTHON_LIBS` | Space-separated list of Python packages to preinstall | (required) |

## How it works

1. The buildpack detects if `BP_PREINSTALL_PYTHON_LIBS` is set
2. Creates a cached layer with the specified Python packages
3. Sets up the `PYTHONPATH` to include the preinstalled packages
4. Uses intelligent caching to avoid reinstalling packages when the library list hasn't changed

## Supported Stacks

- Universal (`*`)

## License

This buildpack follows standard Cloud Native Buildpack conventions and APIs.