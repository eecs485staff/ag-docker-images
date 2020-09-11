# Build project 1 image
FROM eecs485/ag_base:latest

USER autograder:autograder
COPY requirements.txt .
RUN $PYTHON -m venv env-p1
RUN env-p1/bin/pip install -r requirements.txt
USER root:root

RUN rm requirements.txt
