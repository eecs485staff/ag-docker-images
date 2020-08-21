# Build base image for all EECS 485 projects
FROM eecsautograder/ubuntu18:latest

# Install and configure build tools
RUN apt-get update && apt-get install -y software-properties-common sqlite3

# Install and configure Python
RUN add-apt-repository ppa:deadsnakes/ppa && apt-get update
ENV PYTHON python3.8
RUN apt-get install -y $PYTHON $PYTHON-venv

# Install and configure Java (required by html5validator)
RUN apt-get install -y openjdk-8-jre
