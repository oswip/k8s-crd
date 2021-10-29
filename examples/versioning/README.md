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
[v2](rabbit-crd-v2.yaml) is an augmentation of [v1](rabbit-crd-v1.yaml) (it duplicates the existing fields from v1 and adds one more).

[v3](rabbit-crd-v2.yaml) breaks backward compatibility with v2 (and also with v1).

## CR description
Each CR ([v1](rabbit-cr-v1.yaml), [v2](rabbit-cr-v2.yaml), [v3](rabbit-cr-v3.yaml)) is a straightforward instantiation of its respective crd.

## CRD/CR Support
Since CRD v3 breaks backward compatibility, it only supports v3 CRs.

Oberve this by installing the v3 CRD and then trying to create a v1 or v2 CR; notice that the `spec` of the created object is empty (`{}`).

|| CR v1 | CR v2 | CR v3 |
|---|---|---|---|
| CRD v1 | YES | NO | NO |
| CRD v2 | YES | YES | NO |
| CRD v3 | NO | NO | YES |

## Conclusion
If backward compatibility is maintained (only additive changes are made between versions), a CR (and controller) of any previous version can be created/managed on the cluster.

### With backward compatibility
Backward-compatible updates to CRDs will not break deployed controllers. This allows for easy updates: Deploy CRD v<sub>n+1</sub>, Create CR v<sub>n+1</sub>, Deploy controller v<sub>n+1</sub>. During any phase of the update, the active controller should have what it needs to function.

### Without backward compatibility
Once a breaking change is made however, the need arises for one of:
1. Conversion webhooks
2. Updating all affected K8S CRs and controllers at the same time as the breaking CRD

