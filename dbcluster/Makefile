NAME="dbcluster"

helm-upgrade:
	helm upgrade \
		$(NAME) \
		. \
		--install \
		--namespace $(NAME) \
		--create-namespace \
		--kube-context kind-dev

helm-uninstall:
	helm uninstall $(NAME) --namespace $(NAME)
	helm delete ns $(NAME)