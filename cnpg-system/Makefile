NAME="cnpg-system"
CTX="kind-dev"

upgrade:
	helm dependency update .
	helm upgrade \
		--install \
		$(NAME) \
		. \
		--namespace $(NAME) \
		--create-namespace \
		--kube-context $(CTX)

uninstall:
	helm uninstall $(NAME) --namespace $(NAME) --kube-context $(CTX)
	kubectl delete namespace $(NAME) --context $(CTX)