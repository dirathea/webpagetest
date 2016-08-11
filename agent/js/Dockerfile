FROM robcherry/docker-chromedriver

RUN apt-get update

# WPT Agent dependencies
RUN apt-get install -y libjpeg-dev
RUN apt-get install -y zlib1g-dev
RUN apt-get install -y imagemagick
RUN apt-get install -y python-pip
# RUN echo y | pip install pillow

# Nodejs dependencies
RUN apt-get -qq update
RUN apt-get install -y nodejs npm
# TODO could uninstall some build dependencies

# fucking debian installs `node` as `nodejs`
RUN update-alternatives --install /usr/bin/node node /usr/bin/nodejs 10

ADD . /source
ENV SERVER_URL=localhost:8888
ENV LOCATION=Salestock_Chrome
RUN chmod -r /source

CMD xvfb-run /source/wptdriver.sh -s $SERVER_URL -l $LOCATION
