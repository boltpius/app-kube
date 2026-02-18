<<<<<<< Updated upstream
FROM tomcat:10-jdk21
LABEL "Project"="Vprofile"
LABEL "Author"="Imran"

RUN rm -rf /usr/local/tomcat/webapps/*
COPY target/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war

EXPOSE 8080
CMD ["catalina.sh", "run"]
WORKDIR /usr/local/tomcat/
VOLUME /usr/local/tomcat/webapps
=======
# Stage 1: Build the artifact
FROM maven:3.9.9-eclipse-temurin-21-jammy AS BUILD_IMAGE
LABEL "Author"="Pius"

# Set a working directory so paths are predictable
WORKDIR /app

RUN git clone https://github.com/hkhcoder/vprofile-project.git .
RUN git checkout containers && mvn install 

# Stage 2: Deploy to Tomcat
FROM tomcat:10-jdk21 

# Remove default Tomcat apps
RUN rm -rf /usr/local/tomcat/webapps/* # Copy the war file from the build stage
# Note: Since we used WORKDIR /app, the path is now /app/target/...
COPY --from=BUILD_IMAGE /app/target/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war 

EXPOSE 8080 
CMD ["catalina.sh", "run"]
>>>>>>> Stashed changes
