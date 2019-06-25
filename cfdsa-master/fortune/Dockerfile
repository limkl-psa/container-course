FROM node:latest

# define my environment variables
ENV APP_PORT=3000 APP_DIR=/fortune

# create WORKDIR and cd inside
WORKDIR ${APP_DIR}

# copy files to APP_DIR
ADD main.js .
ADD package.json .
# directories must have a target name
ADD public public
ADD views views

# install
RUN npm install
RUN echo ${APP_PORT}
EXPOSE ${APP_PORT}

HEALTHCHECK --interval=60s --timeout=5s --retries=3 \
  CMD curl -f -s http://localhost:${APP_PORT}/health || exit 1

# how should the image be executed
ENTRYPOINT [ "node", "main.js" ]

#CMD [ "${APP_PORT}" ]
