FROM apache/airflow:2.1.0

ENV DEBIAN_FRONTEND=noninteractive

ARG FILE_CHANGED

USER root

RUN apt-get update && apt-get install -y wget && apt-get install -y awscli && apt-get install -y unzip

USER airflow

RUN echo "Copy requirements file"
COPY required_packages.txt .

RUN echo "install your pip packages"
RUN /usr/local/bin/python -m pip install --upgrade pip
RUN pip3 cache dir && pip3 cache info
RUN pip3 cache list
RUN pip3 install --no-cache-dir --user -r required_packages.txt

USER root

WORKDIR /opt    

RUN apt-get update
