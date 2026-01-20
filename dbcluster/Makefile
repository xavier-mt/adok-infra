NAME="dbcluster"
CTX="kind-dev"
DB_SVC="$(NAME)"

psql-super:
	psql "postgresql://superuser:alpha@127.0.0.1:5432/super"

psql-adok:
	psql "postgresql://adokuser:adokpw@127.0.0.1:5432/adok"

upgrade:
	helm upgrade \
		$(NAME) \
		. \
		--install \
		--namespace $(NAME) \
		--create-namespace \
		--kube-context $(CTX)

uninstall:
	helm uninstall $(NAME) --namespace $(NAME) --kube-context $(CTX)
	kubectl delete namespace $(NAME) --context $(CTX)

pf:
	@until kubectl port-forward -n $(NAME) svc/$(NAME)-rw 5432:5432; do \
		echo "Tunnel crashed with exit code $$?. Respawning in 2 seconds..."; \
		sleep 2; \
	done