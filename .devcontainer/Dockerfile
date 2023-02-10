FROM ubuntu:latest
RUN apt-get update && apt-get -y upgrade

# install the python3 and co.
RUN apt-get install python3 python3-pip python3-dev -y
RUN update-alternatives --install /usr/bin/python python /usr/bin/python3 10

# add the sudo
RUN apt-get install sudo -y

# install the Jupiter
RUN pip3 install --upgrade pip
RUN pip3 install jupyter

#
# install the data science tools and libraries
#
# pandas - needed for the data manipulation - web: https://pandas.pydata.org/
RUN pip3 install pandas 
# scipy - algorithms and mathematical functions: optimization, linear algebra, statistics, etc. web: https://www.scipy.org/
RUN pip3 install scipy
# seaborn - statistical data visualization web: https://seaborn.pydata.org/
RUN pip3 install seaborn
# numpy - needed for the numerical manipulation - web: https://numpy.org/
RUN pip3 install numpy
# matplotlib - needed for the ploting - web: https://matplotlib.org/
RUN pip3 install matplotlib
# openpyxl - needed for the excel manipulation - web: https://openpyxl.readthedocs.io/en/stable/
RUN pip3 install openpyxl
# install sympy - needed for the symbolic manipulation - web: https://www.sympy.org/en/index.html
RUN pip3 install sympy

# change the root password
RUN echo 'root:toor' | chpasswd

# create a user used for development
RUN useradd -ms /bin/bash devlh
# change the user password
RUN echo "devlh:testtest" | chpasswd
RUN adduser devlh sudo

# change the user
USER devlh
# change the workdir
WORKDIR /home/devlh
ENV PATH "/home/devlh/.local/bin:${PATH}"

# configure the git
RUN  git config --global --add safe.directory /home/devlh/workspaces/docu \
  && git config --global user.email "lucianhanga@gmx.net" \
  && git config --global user.name "Lucian Hanga"

