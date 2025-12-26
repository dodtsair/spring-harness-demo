# build-image/Dockerfile
FROM cgr.dev/chainguard/wolfi-base:latest

# Copy the APK files
COPY /apk-files/aarch64/*.apk* /tmp/aarch64/
COPY /apk-files/x86_64/*.apk* /tmp/x86_64/
COPY /apk-files/melange.rsa.pub /etc/apk/keys/



RUN apk update
# Install the APK
RUN apk add --no-cache /tmp/aarch64/*.apk /tmp/x86_64/*.apk

RUN rm -rf /var/cache/apk/*; \
    rm -f /tmp/melange.rsa.pub; \
    rm -rf /tmp/*.apk

ENV JAVA_HOME=/usr/lib/jvm/java-21-openjdk/
ENV PATH="${JAVA_HOME}/bin:${PATH}"


# Set working directory and entrypoint
WORKDIR /workspace
ENTRYPOINT ["/workspace/gradlew"]
# CMD ["classes",  "--no-daemon", "--build-cache", "--project-cache-dir=/output/.gradle", "-Dorg.gradle.project.buildDir=/output/build"]
CMD ["build",  "--no-daemon",  "-Dorg.gradle.project.buildDir=/workspace/build"]