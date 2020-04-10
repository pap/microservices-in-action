FROM python:3.8-slim

ARG filename

COPY config.yml requirements.txt setup.cfg setup.py $filename /app/

WORKDIR /app
RUN pip install -r requirements.txt

EXPOSE 8000