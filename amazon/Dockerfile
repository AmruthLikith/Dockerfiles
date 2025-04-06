# Use Ubuntu as the base image
FROM ubuntu:22.04

# Install Java, wget, and git
RUN apt update && apt install -y openjdk-11-jdk git wget

# Clone your Git repo (replace with your repo URL)
RUN git clone https://github.com/AmruthLikith/Amazon  /myrepo

# Download and extract Tomcat
RUN wget https://archive.apache.org/dist/tomcat/tomcat-10/v10.1.17/bin/apache-tomcat-10.1.17.tar.gz && \
    tar -xvzf apache-tomcat-10.1.17.tar.gz && \
    mv apache-tomcat-10.1.17 /opt/tomcat && \
    rm apache-tomcat-10.1.17.tar.gz

# Copy WAR from cloned repo to Tomcat
RUN cp /myrepo/Amazon/Amazon-Web/target/Amazon.war /opt/tomcat/webapps/

# Set working directory
WORKDIR /opt/tomcat

# Expose Tomcat port
EXPOSE 8080

# Start Tomcat
ENTRYPOINT ["sh", "bin/catalina.sh", "run"]
