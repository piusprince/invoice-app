ARG NODE_VERSION=16-alpine3.12

FROM node:${NODE_VERSION} AS base

ENV NODE_ENV=development

ARG APP_HOME = /app

WORKDIR ${APP_HOME}

RUN addgroup -S appgroup && adduser -S appuser -G appgroup

COPY package.json ./

RUN npm install

COPY --chown=appuser:appgroup . ${APP_HOME}

RUN chown appuser:appgroup ${APP_HOME}

USER appuser

CMD ["npm", "run", "dev"]
