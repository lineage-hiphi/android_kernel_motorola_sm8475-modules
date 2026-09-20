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

KBUILD_EXTRA_SYMBOLS := $(M)/../../sensors/$(GKI_OBJ_MODULE_DIR)/Module.symvers
