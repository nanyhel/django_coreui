FROM python:3.9 as build-back

RUN apt-get update

WORKDIR /usr/src/

RUN mkdir -p /usr/src/static

RUN pip3 install -U pip setuptools uwsgi django

RUN django-admin startproject app

WORKDIR /usr/src/app

RUN sed -i 's#/static/#/back/static/#g' app/settings.py

RUN echo "STATIC_ROOT = '/usr/src/static'" >> app/settings.py

RUN python3 manage.py collectstatic

# Stage 2, based on node

FROM node:10 as build-front

WORKDIR /app

COPY package*.json /app/

RUN npm install

COPY . /app/

ARG FRONTEND_ENV=production

# Comment out the next line to disable tests
# RUN npm run test

RUN npm run build

# Stage 3, based on Nginx, to have only the compiled app, ready for production with Nginx

FROM nginx:latest

ENV TZ=America/Lima

COPY --from=build-back /usr/src/static/ /usr/share/static

COPY --from=build-front /app/build/ /usr/share/nginx/html

COPY ./deploy/app/default.conf /etc/nginx/conf.d/default.conf

COPY ./deploy/app/nginx-backend-not-found.conf /etc/nginx/extra-conf.d/backend-not-found.conf
