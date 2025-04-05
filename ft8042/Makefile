ifneq ($(KERNELRELEASE),)
KERNELDIR ?= /lib/modules/$(KERNELRELEASE)/build
KERNELNAME ?= $(KERNELRELEASE)
else
KERNELDIR ?= /lib/modules/$(shell uname -r)/build
KERNELNAME ?= $(shell uname -r)
endif

PWD :=$(shell pwd)

default:
	$(MAKE) -C $(KERNELDIR)  M=$(PWD)  
clean:
	rm -rf *.mk .tmp_versions Module.symvers *.mod.c *.mod *.o *.ko .*.cmd Module.markers modules.order
load:
	insmod ft8042.ko
unload:
	rmmod ft8042
install: default
	mkdir -p /lib/modules/$(KERNELNAME)/kernel/drivers/misc/
	cp -f ./ft8042.ko /lib/modules/$(KERNELNAME)/kernel/drivers/misc/
	depmod -a
	#echo "ft8042" >> /etc/modules
	cp -rv ft8042.conf /etc/modules-load.d/
uninstall:
	rm -rf /lib/modules/$(KERNELNAME)/kernel/drivers/misc/ft8042.ko
	rm -rf /etc/modules-load.d/ft8042.conf
	depmod -a
