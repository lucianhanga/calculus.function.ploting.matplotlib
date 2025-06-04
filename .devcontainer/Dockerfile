FROM ubuntu:latest

# Update and upgrade base packages
RUN apt-get update && apt-get -y upgrade

# Install essential packages
RUN apt-get install -y \
    python3 python3-pip python3-venv \
    sudo git curl build-essential

# Make python3 the default "python"
RUN update-alternatives --install /usr/bin/python python /usr/bin/python3 10

# Create a non-root user
RUN useradd -ms /bin/bash devlh \
    && echo "devlh:testtest" | chpasswd \
    && adduser devlh sudo

USER devlh
WORKDIR /home/devlh

# Set up environment variables
ENV PATH="/home/devlh/.local/bin:${PATH}"

# Create virtual environment and install packages
RUN python -m venv ~/.venv && \
    ~/.venv/bin/pip install --upgrade pip && \
    ~/.venv/bin/pip install \
        jupyter pandas scipy seaborn numpy matplotlib \
        openpyxl sympy ipympl ipykernel

# Make sure kernel is visible in Jupyter interfaces
RUN ~/.venv/bin/python -m ipykernel install --user --name=venv --display-name "Python (venv)"

# Add venv to default path for terminal and notebooks
ENV PATH="/home/devlh/.venv/bin:${PATH}"

# Git configuration
RUN git config --global --add safe.directory /home/devlh/workspaces/docu && \
    git config --global user.email "lucianhanga@gmx.net" && \
    git config --global user.name "Lucian Hanga"

