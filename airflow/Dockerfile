FROM apache/airflow:2.1.0

ENV DEBIAN_FRONTEND=noninteractive

USER root


RUN apt-get update -y && apt-get install -y unzip zip awscli

USER airflow

RUN echo "Copy requirements file"
COPY required_packages.txt .

RUN echo "install your pip packages"
RUN /usr/local/bin/python -m pip install --upgrade pip

RUN pip3 install --no-cache-dir --user -r required_packages.txt

RUN ls /home/airflow/.local/lib/python3.6/site-packages -ltr

RUN zip /home/airflow/.local/lib/python3.6/site-packages {sha1sum required_packages.txt}.zip && ls -al

USER root

WORKDIR /opt

RUN apt-get update
