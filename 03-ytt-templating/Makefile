# Copyright 2022 VMware. All Rights Reserved.
# SPDX-License-Identifier: Apache-2.0

REQUIRED_BINARIES := ytt

check-carvel:
	$(foreach exec,$(REQUIRED_BINARIES),\
		$(if $(shell which $(exec)),,$(error "'$(exec)' not found. Carvel toolset is required. See instructions at https://carvel.dev/#install")))

config: check-carvel
	@ytt -f config

config-staging: check-carvel
	@ytt -f config -f config-staging

install: check-carvel
	$(MAKE) config | kubectl apply -f -

install-staging: check-carvel
	$(MAKE) config-staging | kubectl apply -f -

uninstall: check-carvel
	$(MAKE) config | kubectl delete -f -

uninstall-staging: check-carvel
	$(MAKE) config-staging | kubectl delete -f -
