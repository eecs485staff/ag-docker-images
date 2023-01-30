# Build project 3 image
FROM eecs485/ag_base:latest

# Install Cypress dependencies
RUN apt-get install -y libgtk2.0-0 libgtk-3-0 libgbm-dev libnotify-dev libgconf-2-4 libnss3 libxss1 libasound2 libxtst6 xauth xvfb

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
RUN env-p3/bin/pip install --upgrade pip setuptools wheel
RUN env-p3/bin/pip install -r requirements.txt

# We enter the container as root, but Cypress is installed as autograder.
# Setting this environment variable tells Cypress to look for the cache in /home/autograder
# regardless of which user we are.
ENV CYPRESS_CACHE_FOLDER=/home/autograder/.cache/Cypress

# Install NodeJS packages
COPY package.json .
COPY package-lock.json .

RUN npm ci .

# Install chromedriver (same major version as Google Chrome)
# Since internet access is disabled on the autograder, we need to copy
# the downloaded chromedriver executable to our environment's PATH.
RUN npm install chromedriver --detect_chromedriver_version --no-save; cp node_modules/chromedriver/lib/chromedriver/chromedriver env-p3/bin/chromedriver

RUN rm linux_signing_key.pub requirements.txt

USER root:root
