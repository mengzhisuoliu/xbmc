include ../../Makefile.include PYTHONMODULE-SETUPTOOLS-VERSION
PLATFORM=$(NATIVEPLATFORM)
DEPS= ../../Makefile.include Makefile PYTHONMODULE-SETUPTOOLS-VERSION \
                             01-distutils-flag.patch

export PIP_CACHE_DIR=$(TARBALLS_LOCATION)/pip-cache

all: .installed-$(PLATFORM)

.installed-$(PLATFORM):
	PYTHONPATH="$(NATIVEPREFIX)/lib/python${NATIVE_PYTHON_VERSION}/site-packages" $(NATIVEPREFIX)/bin/python3 -m pip install setuptools==$(VERSION)
	cd $(NATIVEPREFIX)/lib/python${NATIVE_PYTHON_VERSION}/site-packages; patch -p1 -i $(abs_top_srcdir)/native/pythonmodule-setuptools/01-distutils-flag.patch
	touch $@

clean:
	rm -rf .installed-$(PLATFORM)

distclean::
	rm -rf .installed-$(PLATFORM)
	cd $(NATIVEPREFIX)/lib/python${NATIVE_PYTHON_VERSION}/site-packages; rm -rf *distutils* pkg_resources setuptools*
