NAME="dbcluster"
CTX="kind-dev"
DB_SVC="$(NAME)"

helm-upgrade:
	helm upgrade \
		$(NAME) \
		. \
		--install \
		--namespace $(NAME) \
		--create-namespace \
		--kube-context $(CTX)

helm-uninstall:
	helm uninstall $(NAME) --namespace $(NAME) --kube-context $(CTX)
	kubectl delete namespace $(NAME) --context $(CTX)

db-forward:
	@until kubectl port-forward -n $(NAME) svc/$(NAME)-rw 5432:5432; do \
		echo "Tunnel crashed with exit code $$?. Respawning in 2 seconds..."; \
		sleep 2; \
	done