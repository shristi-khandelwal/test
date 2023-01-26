FROM apache/airflow:2.1.0

ENV DEBIAN_FRONTEND=noninteractive

USER root

RUN apt-get update && apt-get install -y wget && apt-get install -y awscli && apt-get install -y unzip

USER airflow

RUN echo "Copy requirements file"
COPY required_packages.txt .

RUN echo "install your pip packages"
RUN /usr/local/bin/python -m pip install --upgrade pip

RUN echo "Existing Cache"
RUN pip3 cache list

RUN echo "Installing Libraries"
RUN pip3 install --user -r required_packages.txt

RUN echo "Updated Cache"
RUN pip3 cache list
RUN ls /home/airflow/.cache/pip/wheels -ltr

USER root

WORKDIR /opt    

RUN apt-get update
