# syntax=docker/dockerfile:1
FROM python:3.9.6-alpine

WORKDIR /home/api

# set environment variables
ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1

# install psycopg2 dependencies
RUN apk update \
    && apk add postgresql-dev gcc python3-dev musl-dev

RUN pip install --upgrade pip
RUN pip install flake8==3.9.2
COPY . .
RUN flake8 --ignore=E501,F401 .


COPY ./requirements.txt .
RUN pip install -r requirements.txt

# copy entrypoint.sh
COPY ./entrypoint.sh /home/api/
RUN sed -i 's/\r$//g' /home/api/entrypoint.sh
RUN chmod +x /home/api/entrypoint.sh

COPY . .
ENTRYPOINT ["/home/api/entrypoint.sh"]

