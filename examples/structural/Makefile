

PRJNAME:=frog
KIND:=Frog
GROUPNAME=amphibians.animals.com

.PHONY: clean crd cr get-crd get-cr

clean:
	kubectl delete crd $(PRJNAME)s.$(GROUPNAME) || true

# must supply version like this `make crd v=1`
crd:
	kubectl apply -f $(PRJNAME)-crd-v$(v).yaml
	kubectl describe crd $(PRJNAME)s.$(GROUPNAME)

# must supply version like this `make cr v=1`
cr:
	kubectl apply -f $(PRJNAME)-cr-v$(v).yaml
	kubectl get $(KIND)/$(PRJNAME)-cr-v$(v) -o yaml
	kubectl get $(PRJNAME) -A

get-crd:
	kubectl describe crd $(PRJNAME)s.$(GROUPNAME)

get-cr:
	kubectl get $(PRJNAME)


# install kind k8s cluster manager
install-kind-linux:
	go install sigs.k8s.io/kind@v0.17.0

