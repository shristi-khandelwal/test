FROM apache/airflow:2.1.0

ENV DEBIAN_FRONTEND=noninteractive

USER root

RUN apt-get update -y && apt-get install -y unzip zip awscli

USER airflow

RUN echo "Copy requirements file"
COPY required_packages.txt .

RUN sha1sum required_packages.txt

RUN echo "install your pip packages"
RUN /usr/local/bin/python -m pip install --upgrade pip

RUN pip3 install --no-cache-dir --user -r required_packages.txt >> output.txt

RUN cat output.txt

USER root

WORKDIR /opt

RUN apt-get update
