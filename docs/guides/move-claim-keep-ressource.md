---
title: Move a claim keeping composite ressource
toc: true
weight: 230
indent: true
---
# Move a claim without re-creating the managed ressources by keeping the composite ressource

There are certain scenarios where it may be advisable to move/rename a claim but leave the managed ressource in place.
If the claim supports the 'crossplane.io/external-name' annotation you can just set the existing managed ressources deletionPolicy to "Orphan", delete the old claim and set up a new one with the old name as external-name.
However not all compositions support the annotation (and this may be a concious decision). There are also cases where it is not easily possible to keep/re-import all managed ressources (e.g. in complex claims this might be quite tedious).


For example you want to move the claim for an EKS Cluster with a lot of additional ressources already created but do not want all users to have to update their kubeconfig and re-setting up all managed ressources would be a tedious task.
Therefore it would be easiest and quickest to be able to create a new claim in the desired location/with the desired name and just "attach" the existing composite-ressource to the new claim.

This guide walks you through the process of moving/renaming a claim without re-creating the composite ressource.
