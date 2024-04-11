ARG BUILD_FROM
FROM $BUILD_FROM

RUN apk add --no-cache \
    nodejs \
    npm \
    git

WORKDIR /proxy
RUN git clone https://github.com/PinoutLTD/libp2p-ws-proxy
RUN cd libp2p-ws-proxy
RUN git checkout hass-addon
COPY . .
RUN touch /proxy/peerIdJson.json
RUN npm ci --only=production


# Copy data for add-on
COPY run.sh /
RUN chmod a+x /run.sh

CMD [ "/run.sh" ]