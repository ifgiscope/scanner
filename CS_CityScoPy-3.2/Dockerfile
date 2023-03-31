FROM python:3.8-bullseye

# set work directory
WORKDIR /usr/src/app/CS_CityScopePy-3.2

#install dependencies
RUN apt update && \
apt install -y libgl1 && \
pip install --upgrade pip \
&& pip install wheel && \
pip install numpy && \
pip install opencv-python && \
pip install requests && \
adduser cityscopepy && adduser cityscopepy video

USER cityscopepy
# copy project
COPY . /usr/src/app/CS_CityScopePy-3.2


