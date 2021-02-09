# Build project 3 image
FROM eecs485/ag_base:latest

# Install NodeJS LTS
RUN apt-get install -y curl
RUN curl -sL https://deb.nodesource.com/setup_lts.x | bash - && apt-get install -y nodejs
RUN apt-get remove -y curl

# Install Google Chrome
ADD https://dl-ssl.google.com/linux/linux_signing_key.pub .
RUN apt-key add linux_signing_key.pub
RUN sh -c 'echo "deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main" >> /etc/apt/sources.list.d/google-chrome.list'
RUN apt-get update && apt-get install -y google-chrome-stable

USER autograder:autograder

# Configure Python virtual environment and install Python packages
COPY requirements.txt .
RUN $PYTHON -m venv env-p3
RUN env-p3/bin/pip install -r requirements.txt

# Install NodeJS packages
COPY package.json .
COPY package-lock.json .
RUN npm install .

# Install chromedriver (same major version as Google Chrome)
RUN npm install chromedriver --detect_chromedriver_version --no-save

RUN rm linux_signing_key.pub requirements.txt

USER root:root
