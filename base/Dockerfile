# Build base image
FROM eecsautograder/ubuntu18:latest

# Install and configure build tools, sqlite, tzdata. Non-interactive frontend
# prevents interactive prompt during tzdata installation (required for python 3.9+).
RUN apt-get update && DEBIAN_FRONTEND="noninteractive" apt-get install -y software-properties-common sqlite3 tzdata

# Install and configure Python and Java (required by html5validator)
RUN add-apt-repository ppa:deadsnakes/ppa && apt-get update
ENV PYTHON python3.9
RUN apt-get install -y $PYTHON $PYTHON-venv openjdk-8-jre
