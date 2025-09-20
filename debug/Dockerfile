FROM openjdk:17-slim

RUN apt-get update && apt-get install -y \
    unzip \
    git \
    wget \
    && rm -rf /var/lib/apt/lists/*

# Explicitly set JAVA_HOME for Gradle
ENV JAVA_HOME="/usr/local/openjdk-17"
ENV PATH="${JAVA_HOME}/bin:${PATH}"

ENV ANDROID_SDK_ROOT="/usr/local/android-sdk"
ENV PATH="${PATH}:${ANDROID_SDK_ROOT}/cmdline-tools/latest/bin:${ANDROID_SDK_ROOT}/platform-tools"

# Directory for commandline tools
RUN mkdir -p ${ANDROID_SDK_ROOT}/cmdline-tools

# Download command line tools
RUN wget -q https://dl.google.com/android/repository/commandlinetools-linux-13114758_latest.zip -O android-sdk-tools.zip

# Unzip the downloaded file
RUN unzip android-sdk-tools.zip -d ${ANDROID_SDK_ROOT}/cmdline-tools

# Move to sdk root
RUN mv ${ANDROID_SDK_ROOT}/cmdline-tools/cmdline-tools ${ANDROID_SDK_ROOT}/cmdline-tools/latest

# Remove the downloaded file
RUN rm android-sdk-tools.zip

# Accept Android SDK licenses
RUN yes | sdkmanager --licenses

# Install essential Android SDK components
RUN sdkmanager \
    "platform-tools" \
    "platforms;android-34" \
    "build-tools;34.0.0"

WORKDIR /app