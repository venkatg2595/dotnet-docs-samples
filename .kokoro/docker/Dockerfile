# start with a powershell image.
FROM mcr.microsoft.com/powershell:lts-ubuntu-18.04

RUN apt-get update
RUN apt-get install wget

RUN wget https://packages.microsoft.com/config/ubuntu/18.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
RUN dpkg -i packages-microsoft-prod.deb

RUN apt-get update
RUN apt-get install apt-transport-https
RUN apt-get update
RUN apt-get -y install dotnet-sdk-2.1
RUN apt-get -y install dotnet-sdk-2.2
RUN apt-get -y install dotnet-sdk-3.1
RUN apt-get -y install dotnet-sdk-6.0

# install phantomjs
# steps from https://www.vultr.com/docs/how-to-install-phantomjs-on-ubuntu-16-04
RUN apt-get install build-essential chrpath libssl-dev libxft-dev libfreetype6-dev libfreetype6 libfontconfig1-dev libfontconfig1 -y
RUN curl https://bitbucket.org/ariya/phantomjs/downloads/phantomjs-2.1.1-linux-x86_64.tar.bz2 -O -L
RUN ls -lash phantomjs-2.1.1-linux-x86_64.tar.bz2
RUN tar xvjf phantomjs-2.1.1-linux-x86_64.tar.bz2 -C /usr/local/share/
RUN ln -s /usr/local/share/phantomjs-2.1.1-linux-x86_64/bin/phantomjs /usr/local/bin/

# install python (required by casperjs)
RUN apt-get install python -y

# install casperjs
RUN curl https://github.com/n1k0/casperjs/tarball/1.0.3 -o casperjs-1.0.3.tar.gz -L
RUN tar xvf casperjs-1.0.3.tar.gz
ENV PATH "$PATH:/casperjs-casperjs-76fc831/bin"

# install casperjs 1.1
RUN curl https://github.com/casperjs/casperjs/archive/1.1.4-1.tar.gz -o casperjs-1.1.4-1.tar.gz -L
RUN tar xvf casperjs-1.1.4-1.tar.gz
ENV CASPERJS11_BIN /casperjs-1.1.4-1/bin

# Add debugging tools.
RUN apt-get install git vim -y

# install GDI+ API compatible implementation for cross-plaform System.Drawing
RUN apt-get install libgdiplus -y
