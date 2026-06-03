# Home Assistant add-on build.
# BUILD_FROM is the HA arch-specific Alpine base (see build.json).
# The application code is pulled from the main repo at a pinned tag, so this
# add-on repo stays thin and tracks releases of ProtossBlaster/leapmotor-mate.
ARG BUILD_FROM
FROM ${BUILD_FROM}

# Version of leapmotor-mate to install (git tag in the main repo).
ARG MATE_REF=v1.1.1

ENV PYTHONUNBUFFERED=1 \
    CERT_DIR=/app/certs \
    DB_PATH=/data/leapmotor_mate.db

WORKDIR /app

# bash is needed by run.sh; build-deps are only needed to compile any wheel that
# lacks a musl build, and are removed in the same layer to keep the image small.
RUN apk add --no-cache bash \
    && apk add --no-cache --virtual .build-deps git build-base libffi-dev openssl-dev \
    && git clone --depth 1 --branch "${MATE_REF}" \
       https://github.com/ProtossBlaster/leapmotor-mate.git /src \
    && pip install --no-cache-dir \
       -r /src/poller/requirements.txt \
       -r /src/web/requirements.txt \
    && cp -r /src/poller /src/web /src/certs /app/ \
    && cp /src/run.sh /run.sh && chmod a+x /run.sh \
    && rm -rf /src \
    && apk del .build-deps

CMD ["/run.sh"]
