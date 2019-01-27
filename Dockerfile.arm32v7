FROM arm32v7/ubuntu

ARG APP_HASH
ARG BUILD_DATE

LABEL org.label-schema.vcs-ref=$APP_HASH \
      org.label-schema.vcs-url="https://github.com/domoticz/domoticz" \
      org.label-schema.url="https://domoticz.com/" \
      org.label-schema.name="Domoticz" \
      org.label-schema.license="GPLv3" \
      org.label-schema.build-date=$BUILD_DATE

COPY qemu-arm-static /usr/bin

RUN apt-get update && \
    apt-get install -y unzip \
        libudev-dev libusb-0.1-4 \
        curl libcurl4 libcurl4-gnutls-dev \
        libpython3.7-dev

COPY domoticz/ /opt/domoticz/
WORKDIR /opt/domoticz

RUN chmod +x ./domoticz

VOLUME /config

EXPOSE 8080

ENTRYPOINT ["/opt/domoticz/domoticz", "-dbase", "/config/domoticz.db", "-log", "/config/domoticz.log"]
CMD ["-www", "8080"]