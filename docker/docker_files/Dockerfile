FROM python:3.10

ENV PYTHONUNBUFFERED 1
ENV PYTHONDONTWRITEBYTECODE 1

# Update and install necessary packages
RUN set -e; \
    apt-get update && \
    apt-get -y install netcat-traditional && \
    apt-get -y install gettext

# Set up the working directory and install requirements
RUN mkdir /code
COPY . /code/
WORKDIR /code

RUN set -e; \
    python -m pip install --upgrade pip && \
    python -m pip install -r /code/requirements.txt && \
    chmod +x /code/docker/entrypoints/entrypoint.sh

# Expose the port
EXPOSE 8000
ENTRYPOINT ["/code/docker/entrypoints/entrypoint.sh"]
