ifneq ($(strip $(KERNEL_SRC)$(M)),)
MAKE_OPTION = 1
else
MAKE_OPTION = 0
endif

ifeq ($(strip $(MAKE_OPTION)), 1)
all: modules
modules:
	$(MAKE) -C $(KERNEL_SRC) M=$(M) O=$(O) modules $(KBUILD_OPTIONS)
modules_install:
	$(MAKE) INSTALL_MOD_STRIP=1 -C $(KERNEL_SRC) M=$(M) O=$(O) modules_install
%:
	$(MAKE) -C $(KERNEL_SRC) M=$(M) O=$(O) $@ $(KBUILD_OPTIONS)
clean:
	rm -f *.o *.ko *.mod.c *.mod.o *~ .*.cmd Module.symvers
	rm -rf .tmp_versions
KBUILD_EXTRA_SYMBOLS += $(CURDIR)/$(KBUILD_EXTMOD)/../../../sensors/$(GKI_OBJ_MODULE_DIR)/Module.symvers
else
KERNEL_SRC ?= /lib/modules/$(shell uname -r)/build

all:
	$(MAKE) -C $(KERNEL_SRC) M=$(shell pwd) O=$(O) modules $(KBUILD_OPTIONS)

modules_install:
	$(MAKE) INSTALL_MOD_STRIP=1 -C $(KERNEL_SRC) M=$(shell pwd) O=$(O) modules_install

clean:
	$(MAKE) -C $(KERNEL_SRC) M=$(PWD) O=$(O) clean

endif
