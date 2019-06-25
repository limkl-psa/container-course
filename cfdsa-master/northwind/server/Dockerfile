# base image
FROM node:latest

# environment variables
ENV DB_HOST=northwind-db DB_PORT=3306 \
    DB_USER=root DB_PASSWORD=changeit \
    APP_PORT=3000 APP_DIR=/app

# create WORKDIR and cd inside
WORKDIR ${APP_DIR}

# copy files to APP_DIR
ADD main.js .
ADD package.json .
# directories must have a target name
ADD config config
ADD public public
ADD views views

# install
RUN npm install

EXPOSE ${APP_PORT}

HEALTHCHECK --interval=60s --timeout=5s --retries=3 \
  CMD curl -f -s http://localhost:${APP_PORT}/health || exit 1

# how should the image be executed
ENTRYPOINT [ "node", "main.js" ]

CMD [ "" ]
