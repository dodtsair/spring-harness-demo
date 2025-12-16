# build-image/Dockerfile
FROM cgr.dev/chainguard/wolfi-base:latest

# Copy the APK files
COPY *.apk* /tmp/
COPY melange-rsa.pub /etc/apk/keys/

RUN apk update
# Install the APK
RUN apk add --no-cache /tmp/*.apk

RUN rm -rf /var/cache/apk/*; \
    rm -f /tmp/melange.rsa.pub; \
    rm -rf /tmp/*.apk
