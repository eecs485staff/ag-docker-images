# Build base image
FROM eecsautograder/ubuntu22:latest

# Set ARG and ENV variables required for tzdata installation (required for Python 3.9+)
# Source: https://serverfault.com/a/1016972
ARG DEBIAN_FRONTEND=noninteractive
ENV TZ=America/Detroit

# Install common build tools, sqlite, and tzdata
RUN apt-get update && apt-get install -y build-essential software-properties-common sqlite3 tzdata

# Install Python, Java (required by html5validator), and file (used in tests)
RUN add-apt-repository ppa:deadsnakes/ppa && apt-get update
ENV PYTHON python3.10
RUN apt-get install -y $PYTHON $PYTHON-venv openjdk-8-jre file
