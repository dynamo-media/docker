FROM gliderlabs/consul:0.5
ADD ./config /config/
ADD ./check-http /bin/check-http
ADD https://dl.bintray.com/mitchellh/consul/0.5.2_web_ui.zip /tmp/webui.zip
RUN cd /tmp && unzip webui.zip && mv dist /ui && rm webui.zip && apk add --update curl \
	&& rm -rf /var/cache/apk/*
EXPOSE 8300 8301 8301/udp 8302 8302/udp 8400 8500 53 53/udp
VOLUME ["/data"]
ENTRYPOINT ["/bin/consul", "agent", "-server", "-config-dir=/config"]
