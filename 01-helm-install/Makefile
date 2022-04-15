# Copyright 2022 VMware. All Rights Reserved.
# SPDX-License-Identifier: Apache-2.0

install:
	kubectl apply -f namespace.yaml -f ingress.yaml && \
	helm upgrade -n hello-kubernetes -f helm-values.yaml -i hello-kubernetes charts/hello-kubernetes

uninstall:
	kubectl delete -f namespace.yaml
