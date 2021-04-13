# Mkdocs container image

Container image for working with mkdocs sites

## Usage

The image sets up `mkdocs` as the entry point so it can be used as-is as a docker-based cli by passing all the arguments to `mkdocs` on the command-line.
If more customized behavior is required, the image can be extended and the entrypoint replaced with more specific logic.

### Docker-extended CLI

#### Help content

To get started running `mkdocs` through the container image, run the following:

```
docker run quay.io/cloudnativetoolkit/mkdocs --help
```

That will download the container image (if not already available) and run it locally. In this case it will print the help content for `mkdocs`.

#### Dev Server

```
docker run -d -v ${PWD}:/site -p 8000:8000 quay.io/cloudnativetoolkit/mkdocs serve -f /site/mkdocs.yml --livereload -a 0.0.0.0:8000
```

That command will run the container in the background (`-d`), mount the current working directory into the container in the `/site` directory (`-v ${PWD}:/site`), expose the container port `8000` to the host port `8000`, and start the server using the `mkdocs.yml` in the current working directory to configure a live reloading mkdocs server. After the command is run you can access the dev site by openning a browser to `http://localhost:8000`.

## Building the image

To build the container image run the following: `docker build -t mkdocs .`

