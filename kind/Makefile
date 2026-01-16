
create-cluster:
	kind create cluster --name dev

install-cnpg:
	helm repo add cnpg https://cloudnative-pg.github.io/charts
	helm repo update
	helm upgrade \
		--install \
		cnpg-operator \
		cnpg/cloudnative-pg \
		--namespace cnpg-system \
		--create-namespace \
		--kube-context kind-dev
