

PRJNAME:=rabbit
KIND:=Rabbit
GROUPNAME=mammals.animals.com

.PHONY: crd

clean:
	kubectl delete crd $(PRJNAME)s.$(GROUPNAME) || true

# must supply version like this `make cr v=1`
cr:
	kubectl apply -f $(PRJNAME)-cr-v$(v).yaml
	kubectl get $(KIND)/$(PRJNAME)-cr-v$(v) -o yaml
	kubectl get $(PRJNAME) -A

# must supply version like this `make crd v=1`
crd:
	kubectl apply -f $(PRJNAME)-crd-v$(v).yaml
	kubectl describe crd $(PRJNAME)s.$(GROUPNAME)

get-cr:
	kubectl get $(PRJNAME)

get-crd:
	kubectl describe crd $(PRJNAME)s.$(GROUPNAME)

