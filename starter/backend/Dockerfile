FROM public.ecr.aws/docker/library/python:3.10-alpine

ENV FLASK_RUN_HOST=0.0.0.0

WORKDIR /

RUN adduser -u 1000 -D app

RUN apk update && \
    apk add \
    pcre \
    pcre-dev \
    build-base \
    gcc \
    linux-headers \
    openssl \
    libffi-dev

RUN pip install --no-cache-dir flask flask-cors gunicorn

RUN mkdir -p /var/www/app

RUN mkdir /backend

COPY . /backend

CMD ["gunicorn", "--bind", "0.0.0.0:5000", "backend:app"]