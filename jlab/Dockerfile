FROM python:buster

WORKDIR /root
EXPOSE 8888
ENV SHELL=/bin/bash
ARG CONDA_INSTALLER_PATH=/root/install-conda.sh
ARG CONDA_PATH=/miniconda

ADD jupyter_notebook_config.py /root

# Basic environment
RUN apt-get update && \
    apt-get install curl vim wget git -y

# Conda and nodejs environment
RUN wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh -O ${CONDA_INSTALLER_PATH} && \
    bash ${CONDA_INSTALLER_PATH} -p ${CONDA_PATH} -b && \
    rm -f ${CONDA_INSTALLER_PATH} && \
    echo "export PATH=${CONDA_PATH}/bin:$PATH" >> ~/.bashrc
ENV PATH=${CONDA_PATH}/bin:${PATH}
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
