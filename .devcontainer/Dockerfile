# Use Gitpod's base image or a Debian-based image
FROM gitpod/workspace-full

# Install Java 21
RUN sudo apt-get update && \
    sudo apt-get install -y wget gnupg && \
    wget -O- https://packages.adoptium.net/artifactory/api/gpg/key/public | gpg --dearmor | sudo tee /usr/share/keyrings/adoptium-archive-keyring.gpg > /dev/null && \
    echo "deb [signed-by=/usr/share/keyrings/adoptium-archive-keyring.gpg] https://packages.adoptium.net/artifactory/deb bookworm main" | sudo tee /etc/apt/sources.list.d/adoptium.list && \
    sudo apt-get update && \
    sudo apt-get install -y temurin-21-jdk

# Set Java 21 as default
ENV JAVA_HOME=/usr/lib/jvm/temurin-21-jdk
ENV PATH=$JAVA_HOME/bin:$PATH

# Install Gradle (latest stable)
ENV GRADLE_VERSION=8.5
RUN wget https://services.gradle.org/distributions/gradle-${GRADLE_VERSION}-bin.zip -P /tmp && \
    sudo unzip -d /opt/gradle /tmp/gradle-${GRADLE_VERSION}-bin.zip && \
    sudo ln -s /opt/gradle/gradle-${GRADLE_VERSION}/bin/gradle /usr/bin/gradle

# Verify
RUN java -version && gradle --version && git --version
