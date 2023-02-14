FROM ubuntu:latest
RUN apt-get update
RUN apt-get -y upgrade

# install the python3 and co.
RUN apt-get install python3 -y
RUN apt-get install python3-pip -y
RUN update-alternatives --install /usr/bin/python python /usr/bin/python3 10

# add the sudo
RUN apt-get install sudo -y

# install the Jupiter
RUN pip3 install --upgrade pip
RUN pip3 install jupyter

# install the git
RUN apt-get install git -y

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
# ipympl - needed for the interactive ploting - web: 
RUN pip3 install ipympl

# for notebook to pdf printing
# RUN pip3 install notebook-as-pdf
# RUN sudo apt-get install chromium-chromedriver -y
# RUN sudo apt-get install -y gconf-service libasound2 libatk1.0-0 libatk-bridge2.0-0 libc6 libcairo2 libcups2 libdbus-1-3 libexpat1 libfontconfig1 libgcc1 libgconf-2-4 libgdk-pixbuf2.0-0 libglib2.0-0 libgtk-3-0 libnspr4 libpango-1.0-0 libpangocairo-1.0-0 libstdc++6 libx11-6 libx11-xcb1 libxcb1 libxcomposite1 libxcursor1 libxdamage1 libxext6 libxfixes3 libxi6 libxrandr2 libxrender1 libxss1 libxtst6 ca-certificates fonts-liberation libappindicator1 libnss3 lsb-release xdg-utils wget
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

