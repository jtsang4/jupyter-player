# Jlab

A docker image for developing jupyterlab. Both notebook and jupyterlab are installed on dev mode.

## Usage

```shell
docker run -i -t wtzeng/jlab-dev -p 8888:8888 # mount files by '-v "$HOST_PATH":/root'
jupyter lab
```

Then open `http://localhost:8888` in browser.

## Why build this image?

With this container environment, you can modify the origin notebook or jupyterlab without worry about ruining local notebook or jupyterlab.


## Tools

Developing with VSCode remote would be better.