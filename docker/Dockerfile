FROM multiarch/alpine:armhf-v3.7

LABEL maintainer="Massimo Gaggero <massimo dot gaggero at gmail dot com>"
  
RUN apk add --no-cache git g++ make cmake libusb-dev

RUN mkdir /sources && cd /sources && \
	git clone git://git.osmocom.org/rtl-sdr.git && cd rtl-sdr && \
	mkdir build && cd build && \
	cmake ../ -DINSTALL_UDEV_RULES=ON -DDETACH_KERNEL_DRIVER=ON && \
	make && make install #&& ldconfig

#RUN apk del git g++ make bash

EXPOSE 1234

CMD ["rtl_tcp", "-a", "0.0.0.0"]

