ARG NODE_VERSION

FROM node:${NODE_VERSION}-alpine
# Install dependencies required for aws-lambda-ric
RUN apk add --no-cache --update --repository=https://dl-cdn.alpinelinux.org/alpine/v3.16/main/ libexecinfo-dev && \
    apk add --no-cache --update autoconf automake build-base cmake libtool libgsasl python3 && \
    # Install the AWS Lambda Runtime Interface Client.
    npm i -g aws-lambda-ric
# The entrypoint is a small wrapper around aws-lambda-ric.
COPY docker/base/entrypoint.sh /entrypoint.sh
ENTRYPOINT ["/entrypoint.sh"]
WORKDIR /lambda
CMD ["dist/index.handler"]
