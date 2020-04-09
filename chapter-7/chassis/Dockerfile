FROM python:3.8-slim

COPY . /app

WORKDIR /app

RUN pip install -r requirements.txt

EXPOSE 8000

CMD [ "nameko", "run", "--config", "config.yml", "demo" ]