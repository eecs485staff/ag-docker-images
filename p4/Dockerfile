# Build project 4 image
FROM eecs485/ag_base:latest

RUN apt-get install -y netcat
USER autograder:autograder
COPY requirements.txt .
RUN $PYTHON -m venv env-p4
RUN env-p4/bin/pip install -r requirements.txt
USER root:root

RUN rm requirements.txt
