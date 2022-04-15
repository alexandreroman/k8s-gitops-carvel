# Copyright 2022 VMware. All Rights Reserved.
# SPDX-License-Identifier: Apache-2.0

REQUIRED_BINARIES := ytt

check-carvel:
	$(foreach exec,$(REQUIRED_BINARIES),\
		$(if $(shell which $(exec)),,$(error "'$(exec)' not found. Carvel toolset is required. See instructions at https://carvel.dev/#install")))

config: check-carvel
	@ytt -f app.yaml -f overlay.yaml

install: check-carvel
	$(MAKE) config | kubectl apply -f -

uninstall: check-carvel
	$(MAKE) config | kubectl delete -f -
