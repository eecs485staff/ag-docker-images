# Build project 5 image
FROM eecs485/ag_base:latest

USER autograder:autograder
COPY requirements.txt .
RUN $PYTHON -m venv env-p5
RUN env-p5/bin/pip install -r requirements.txt
USER root:root

RUN rm requirements.txt
