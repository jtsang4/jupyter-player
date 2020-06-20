FROM continuumio/miniconda3

WORKDIR /root
EXPOSE 8888

ADD jupyter_notebook_config.py /root

# Basic environment
RUN apt-get update && \
    apt-get install curl vim -y

# Conda and nodejs environment
RUN conda update -n base -c defaults conda
RUN conda install -c conda-forge -y nodejs
RUN npm install -g yarn

# Notebook
RUN git clone https://github.com/jupyter/notebook && \
    cd notebook && pip install -e .
RUN jupyter notebook --generate-config && \
    mv jupyter_notebook_config.py /root/.jupyter/jupyter_notebook_config.py

# Jupyterlab
RUN git clone https://github.com/jupyterlab/jupyterlab.git && \
    cd jupyterlab && \
    pip install -e . && \
    jlpm install && \
    jlpm run build && \
    jlpm run build:core && \
    jupyter lab build

CMD [ "/bin/bash" ]
