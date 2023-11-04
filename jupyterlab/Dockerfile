#FROM python:3.8.16-bullseye
FROM python:3.11.2-buster
ARG DEBIAN_FRONTEND=noninteractive

# Adding packages and set time zone
RUN apt update && apt install -y \
    tzdata \
    build-essential \
    git \
    curl \
&&  ln -sf /usr/share/zoneinfo/Asia/Tokyo /etc/localtime \
&&  apt clean \
&&  rm -rf /var/lib/apt/lists/*
ENV TZ=Asia/Tokyo


# Install Java RE
RUN apt-get update && apt-get install -y default-jre

# Install dependencies for camelot-py
RUN apt install -y ghostscript python3-tk


# Install nodejs
# https://github.com/nodesource/distributions
RUN curl -fsSL https://deb.nodesource.com/setup_19.x | bash - &&\
apt install -y nodejs


# Regarding Jupyterlab extensions
RUN python3 -m pip install --upgrade pip \
&&  pip3 install --no-cache-dir \
    black \
    jupyterlab \
    jupyterlab_code_formatter \
    jupyterlab-git \
    lckr-jupyterlab-variableinspector \
    jupyterlab_widgets \
    ipywidgets \
    import-ipynb \
    jupyter-resource-usage \
    theme-darcula
#    jupyterlab-topbar \
#    jupyterlab-topbar-text \
#    jupyterlab-system-monitor \
#    jupyterlab_tabnine

# Default pip libraries you need
RUN pip install --no-cache-dir \
    numpy \
    pandas \
    pendulum \
    polars \
    scikit-learn \
    scipy \
    duckdb \
    matplotlib \
    seaborn \
    plotly \
    requests \
    httpx \
    selectolax \
    selenium \
    lxml \
    mitosheet \
    bokeh \
    beautifulsoup4 \
    PyMySQL \
    SQLAlchemy \
    tqdm \
    tornado \
    Pillow \
    sqlmodel \
    tabula-py \
    opencv-python \
    torch \
    fastai \
    transformers \
    diffusers \
    accelerate \
    safetensors \
    omegaconf \
    tensorflow \
    openai \
    pyarrow \
    sentencepiece
#    camelot-py \
#    pycaret \

# Furthermore dependencies
COPY ./requirements.txt /requirements.txt
RUN pip install -r /requirements.txt

# Install Mitosheet to Jupyter \
RUN python -m jupyter nbextension install --py --user mitosheet
RUN python -m jupyter nbextension enable --py --user mitosheet


#RUN jupyter labextension install \
#    @jupyterlab/toc \
#    && jupyter lab build -y \
#    && jupyter lab clean -y
