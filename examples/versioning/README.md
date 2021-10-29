# CRD Versioning Experiment

## Makefile
To shorten kubectl commands, there's a [Makefile](Makefile)
- To wipe the CRD and CRs
```
make clean
```

- To install a CRD
```
make crd v=1
```
- To create a CR
```
make cr v=1
```

## CRD description
There are 3 versions of CRD here.
[v2](rabbit-crd-v2.yaml) is an augmentation of v1 (it duplicates the existing fields from v1 and adds one more).
[v3](rabbit-crd-v2.yaml) breaks backward compatibility with v2 (and also with v1).

## CR description
Each CR ([v1](rabbit-cr-v1.yaml), [v2](rabbit-cr-v2.yaml), [v3](rabbit-cr-v3.yaml)) is a straightforward instantiation of its respective crd.




