# Jlab

A docker image for developing jupyterlab. Both notebook and jupyterlab are installed on dev mode.

## Usage

```shell
docker run --rm -i -t -p 8888:8888 wtzeng/jlab-dev # mount files by "-v", like "docker run --rm -i -t -p 8888:8888 -v $(pwd):/root/data wtzeng/jlab-dev"
jupyter lab
```

Then open `http://localhost:8888` in browser.

## Why build this image?

With this container environment, you can modify the origin notebook or jupyterlab without worry about ruining local notebook or jupyterlab.


## Tools

Developing with VSCode remote would be better.