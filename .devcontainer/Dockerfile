FROM ubuntu:latest
RUN apt-get update
RUN apt-get -y upgrade

RUN apt-get install python3 python3-pip python3-venv sudo git -y

RUN update-alternatives --install /usr/bin/python python /usr/bin/python3 10

# install Jupyter via apt if available, otherwise use pip in venv
# RUN apt-get install jupyter-notebook -y

# create a user for development
RUN useradd -ms /bin/bash devlh \
    && echo "devlh:testtest" | chpasswd \
    && adduser devlh sudo

USER devlh
WORKDIR /home/devlh
ENV PATH="/home/devlh/.local/bin:${PATH}"

# create and activate a virtual environment, then install packages
RUN python3 -m venv ~/.venv \
    && ~/.venv/bin/pip install --upgrade pip \
    && ~/.venv/bin/pip install jupyter pandas scipy seaborn numpy matplotlib openpyxl sympy ipympl

ENV PATH="/home/devlh/.venv/bin:${PATH}"

# configure git
RUN git config --global --add safe.directory /home/devlh/workspaces/docu \
  && git config --global user.email "lucianhanga@gmx.net" \
  && git config --global user.name "Lucian Hanga"

  
