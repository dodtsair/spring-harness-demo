# build-image/Dockerfile
FROM cgr.dev/chainguard/wolfi-base:latest

# Copy the APK files
COPY aarch64/*.apk* /tmp/aarch64/
COPY x86_64/*.apk* /tmp/x86_64/
COPY melange.rsa.pub /etc/apk/keys/

RUN apk update
# Install the APK
RUN apk add --no-cache /tmp/aarch64/*.apk /tmp/x86_64/*.apk

RUN rm -rf /var/cache/apk/*; \
    rm -f /tmp/melange.rsa.pub; \
    rm -rf /tmp/*.apk
