# build-image/Dockerfile
FROM cgr.dev/chainguard/wolfi-base:latest

# Copy the APK files (paths are relative to build context root)
COPY build/melange/apks/aarch64/*.apk* /tmp/aarch64/
COPY build/melange/apks/x86_64/*.apk* /tmp/x86_64/

# Copy the public signing key into apk keys
COPY build/melange/keys/melange.rsa.pub /etc/apk/keys/

RUN apk update

# Install the APKs
RUN apk add --no-cache /tmp/aarch64/*.apk /tmp/x86_64/*.apk

# Cleanup
RUN rm -rf /var/cache/apk/* && \
    rm -rf /tmp/*.apk

ENV JAVA_HOME=/usr/lib/jvm/java-21-openjdk/
ENV PATH="${JAVA_HOME}/bin:${PATH}"



# Set working directory and entrypoint
# WORKDIR /workspace
# ENTRYPOINT ["/workspace/gradlew"]
# CMD ["classes",  "--no-daemon", "--build-cache", "--project-cache-dir=/output/.gradle", "-Dorg.gradle.project.buildDir=/output/build"]
# CMD ["build",  "--no-daemon",  "-Dorg.gradle.project.buildDir=/output/"]