FROM python:3.10-slim-buster

WORKDIR /development

RUN apt-get update && \
    apt-get install -y git

COPY requirements.txt requirements.txt

RUN python -m pip install --upgrade pip && \
    python -m pip install -r requirements.txt
