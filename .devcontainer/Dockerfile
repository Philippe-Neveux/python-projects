FROM ubuntu:22.04

RUN apt update && apt-get install -y --no-install-recommends libssl-dev libffi-dev libncurses5-dev zlib1g zlib1g-dev libreadline-dev libbz2-dev libsqlite3-dev make gcc curl wget
RUN mkdir /home/pneveux

ENV HOME="/home/pneveux"
WORKDIR ${HOME}

RUN apt install -y git

# Install Pyenv
RUN curl https://pyenv.run | bash

ENV PYENV_ROOT="${HOME}/.pyenv"
ENV PATH="${PYENV_ROOT}/shims:${PYENV_ROOT}/bin:${PATH}"

ENV PYTHON_VERSION=3.10
RUN pyenv install ${PYTHON_VERSION}
RUN pyenv global ${PYTHON_VERSION}

# Install conda/mamba
RUN wget -O Miniforge3.sh "https://github.com/conda-forge/miniforge/releases/latest/download/Miniforge3-$(uname)-$(uname -m).sh"
RUN bash Miniforge3.sh -b -p "${HOME}/conda"

## Activate conda and mamba command
# RUN echo "${HOME}/conda/etc/profile.d/conda.sh" > .bashrc && echo "${HOME}/conda/etc/profile.d/mamba.sh" >> .bashrc

# Install Poetry
RUN curl -sSL https://install.python-poetry.org | python3 -
ENV PATH="${HOME}/.local/share/pypoetry/venv/bin:${PATH}"
