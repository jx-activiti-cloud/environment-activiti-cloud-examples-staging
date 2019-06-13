CHART_REPOSITORY := https://activiti.github.io/activiti-cloud-helm-charts/
# http://jenkins-x-chartmuseum:8080
CHART_REPO :=https://activiti.github.io/activiti-cloud-helm-charts/
DIR := "env"
NAMESPACE := "jx-staging"
OS := $(shell uname)

build: clean
	rm -rf requirements.lock
	helm version
	helm init
	helm repo add releases ${CHART_REPO}
	helm repo add jenkins-x http://chartmuseum.jenkins-x.io
	helm dependency build ${DIR}
	helm lint ${DIR}

install: 

	helm upgrade --install  staging-full-chart .   --namespace ${NAMESPACE}   --debug


delete:
	helm delete --purge --no-hooks  --namespace ${NAMESPACE} --name staging-full-chart

clean:


