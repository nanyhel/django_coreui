FROM python:3.9

RUN apt-get update

WORKDIR /usr/src/

RUN mkdir -p /usr/src/static

RUN pip3 install -U pip setuptools uwsgi django

RUN django-admin startproject app

WORKDIR /usr/src/app

RUN sed -i 's#/static/#/back/static/#g' app/settings.py

RUN echo "STATIC_ROOT = '/usr/src/static'" >> app/settings.py

RUN python3 manage.py collectstatic

EXPOSE 8000

ENTRYPOINT ["uwsgi", "--http", ":8000", "--wsgi-file", "app/wsgi.py"]