# Build project 2 image
FROM eecs485/ag_base:latest

USER autograder:autograder

COPY requirements.txt .
RUN $PYTHON -m venv env-p2
RUN env-p2/bin/pip install -r requirements.txt
RUN rm requirements.txt

USER root:root
