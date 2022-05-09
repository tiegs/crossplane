---
title: Move a claim keeping composite ressource
toc: true
weight: 230
indent: true
---
# Move a claim without re-creating the managed ressources by keeping the composite ressource

There are certain scenarios where it may be advisable to move/rename a claim but leave the managed ressource in place.
If the claim supports the 'crossplane.io/external-name' annotation you can just set the existing managed ressources deletionPolicy to "Orphan", delete the old claim and set up a new one with the old name as external-name.
However not all compositions support the annotation (and this may be a concious decision). 
There are also cases where it is not easily possible to orphan/re-import all managed ressources (e.g. for complex ressources this might be quite tedious).

In these scenarios it may be the easiest to be able to create a new claim in the desired location/with the desired name and just "attach" the existing composite-ressource to the new claim. This guide walks you through the steps to archieve exactly this.

## Preparation

