FROM python:3.8-bullseye

# set work directory

WORKDIR /usr/src/app/CS_CityScopePy-3.2
RUN apt update && apt install -y libgl1

# install pip
RUN pip install --upgrade pip && pip install wheel && pip install numpy && pip install opencv-python && pip install requests

# install dependencies
RUN 


# copy entrypoint.sh
#COPY ./entrypoint.sh /usr/src/app/entrypoint.sh

# copy project
COPY . /usr/src/app/CS_CityScopePy-3.2

# run entrypoint.sh
#ENTRYPOINT ["sh", "/usr/src/app/entrypoint.sh"]

