# Basic shell image
FROM codenvy/shellinabox

# Download and extract Java 8u51 to opt
RUN wget \
    --no-cookies \
    --no-check-certificate \
    --header "Cookie: oraclelicense=accept-securebackup-cookie" \
    -qO- \
    "http://download.oracle.com/otn-pub/java/jdk/8u51-b16/jdk-8u51-linux-x64.tar.gz" | sudo tar -zx -C /opt/

# Set JAVA_HOME and add to PATH    
ENV JAVA_HOME /opt/jdk1.8.0_51
RUN echo "export JAVA_HOME=$JAVA_HOME" >> /home/user/.bashrc
ENV PATH $JAVA_HOME/bin:$PATH
RUN echo "export PATH=$PATH" >> /home/user/.bashrc

# Create app directory and extract build
RUN mkdir /home/user/app
WORKDIR /home/user/app
ADD $app$ /home/user/$app$
RUN unzip -q /home/user/$app$ -d /home/user/app && rm /home/user/$app$
  
# Create bin directory for sbt files, and move them from app directory
# Add sbt to PATH
RUN mkdir /home/user/bin
RUN cp /home/user/app/sbt/* /home/user/bin
RUN rm -rf /home/user/app/sbt
RUN chmod u+x /home/user/bin/sbt
ENV PATH /home/user/bin:$PATH
RUN echo "export PATH=$PATH" >> /home/user/.bashrc

# Execute SBT build
WORKDIR /home/user/app
RUN sbt clean compile run