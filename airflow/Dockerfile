FROM apache/airflow:2.1.0

ENV DEBIAN_FRONTEND=noninteractive

USER root

RUN apt-get update -y && apt-get install -y unzip zip awscli

USER airflow

RUN echo "Copy requirements file"
COPY required_packages.txt .

RUN sha1sum required_packages.txt | awk '{print $1}' >> output.txt

ENV sha=`${cat output.txt}`

RUN echo "install your pip packages"
RUN /usr/local/bin/python -m pip install --upgrade pip

RUN pip3 install --no-cache-dir --user -r required_packages.txt

RUN ls /home/airflow/.local/lib/python3.6/site-packages -ltr

RUN zip "$sha".zip /home/airflow/.local/lib/python3.6/site-packages && ls -al

USER root

WORKDIR /op

RUN apt-get update
