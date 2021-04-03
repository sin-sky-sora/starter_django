FROM python:slim

WORKDIR /django

COPY dp/requirements.txt /django/

ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1

RUN apt-get update && apt-get install gcc libpcre3 libpcre3-dev -y

RUN python -m pip install --upgrade pip \
    && pip install -r requirements.txt

RUN mkdir -p /var/run/gunicorn

CMD ["gunicorn","dp.wsgi","--bind=unix:/var/run/gunicorn/gunicorn.sock"]
