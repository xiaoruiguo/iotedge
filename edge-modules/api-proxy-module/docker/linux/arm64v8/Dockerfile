#-------------------------------------------------------------------------------------------------------------
# Copyright (c) Microsoft Corporation. All rights reserved.
# Licensed under the MIT License. See https://go.microsoft.com/fwlink/?linkid=2090316 for license information.
#-------------------------------------------------------------------------------------------------------------

FROM arm64v8/alpine:3.13.1
WORKDIR /app
COPY ./docker/linux/arm64v8/lib/ /lib
COPY ./docker/linux/arm64v8/api-proxy-module .
COPY ./docker/linux/arm64v8/templates .
RUN	apk update && \
    apk add nginx && \
	mkdir /run/nginx
#expose ports
EXPOSE 443/tcp	
EXPOSE 80/tcp
#used by registry
EXPOSE 5000/tcp
#used by blob storage
EXPOSE 11002/tcp
#use for custom defining ports
EXPOSE 7000-8000/tcp
ENTRYPOINT ["/app/api-proxy-module"]
 