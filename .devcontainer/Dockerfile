FROM mcr.microsoft.com/vscode/devcontainers/base:ubuntu-20.04

# Install all Python versions supported by EDGAR
RUN apt-get update && apt-get install -y \
    software-properties-common \
    && add-apt-repository ppa:deadsnakes/ppa \
    && apt-get update && apt-get install -y \
    python3.9 python3.9-dev python3.9-venv \
    python3.10 python3.10-dev python3.10-venv \
    python3.11 python3.11-dev python3.11-venv \
    python3.12 python3.12-dev python3.12-venv \
    python3.13 python3.13-dev python3.13-venv \
    curl

# This installs pip for the primary version of Python we'll use
# for development
RUN curl -sS https://bootstrap.pypa.io/get-pip.py | python3.13

# Set default python executable for when users run python or python3
# on the command line
RUN ln -sf /usr/bin/python3.13 /usr/bin/python
RUN ln -sf /usr/bin/python3.13 /usr/bin/python3

# Install pipx, poetry, and tox
RUN python -m pip install --upgrade pip \
    && python -m pip install pipx \
    && python -m pipx ensurepath \
    && pipx install --global poetry tox
