KDIR ?= /lib/modules/`uname -r`/build
PPS_GPIO ?= 483

obj-m := minnow-pps-gpio.o

SRC := $(shell pwd)

all:
	$(MAKE) -C $(KDIR) M=$(SRC) CFLAGS_minnow-pps-gpio.o="-DPPS_GPIO=$(PPS_GPIO)"

modules_install:
	$(MAKE) -C $(KDIR) M=$(SRC) modules_install

clean:
	rm -f *.o *~ core .depend .*.cmd *.ko *.mod.c
	rm -f Module.markers Module.symvers modules.order
	rm -rf .tmp_versions Modules.symvers

dkms_install:
	cp -R . /usr/src/minnow-pps-gpio-20150721 && dkms add -m minnow-pps-gpio -v 20150721
