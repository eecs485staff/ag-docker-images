# Build project 4 image
FROM eecs485/ag_base:latest

# Install netcat (required for mapreduce scripts)
RUN apt-get install -y netcat

USER autograder:autograder

COPY requirements.txt .
RUN $PYTHON -m venv env-p4
RUN env-p4/bin/pip install --upgrade pip setuptools wheel
RUN env-p4/bin/pip install -r requirements.txt
RUN rm requirements.txt

USER root:root
