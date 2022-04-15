# Copyright 2022 VMware. All Rights Reserved.
# SPDX-License-Identifier: Apache-2.0

REQUIRED_BINARIES := kapp ytt

check-carvel:
	$(foreach exec,$(REQUIRED_BINARIES),\
		$(if $(shell which $(exec)),,$(error "'$(exec)' not found. Carvel toolset is required. See instructions at https://carvel.dev/#install")))

install: check-carvel
	ytt -f config | kapp deploy -a spring-on-k8s -f - --diff-changes -y

uninstall: check-carvel
	kapp delete -a spring-on-k8s -y
