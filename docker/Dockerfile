FROM python:3.9.1-slim-buster
RUN apt-get update -qq && apt-get install -yqq wget curl awscli jq
RUN wget https://awssecret2env.s3.amazonaws.com/latest/awssecret2env-linux64 \
    && chmod +x awssecret2env-linux64 \
    && mv awssecret2env-linux64 /usr/local/bin/awssecret2env
ENV APP_HOME=/app
ENV APP_USER=appuser
WORKDIR $APP_HOME
RUN groupadd -r ${APP_USER} && useradd --no-log-init -r -g ${APP_USER} ${APP_USER}
ADD ./requirements.txt /app/requirements.txt
RUN pip install --no-cache-dir -r /app/requirements.txt
ADD . /app/
RUN chmod +x /app/scripts/get_secrets.sh
RUN chown -R $APP_USER:$APP_USER $APP_HOME
USER $APP_USER