# Build project 4 image
FROM eecs485/ag_base:latest

USER autograder:autograder

RUN apt-get install -y netcat
COPY requirements.txt .
RUN $PYTHON -m venv env-p4
RUN env-p4/bin/pip install -r requirements.txt
RUN rm requirements.txt

USER root:root
