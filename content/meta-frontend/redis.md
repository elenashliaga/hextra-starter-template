---
title: Redis
type: docs
weight: 8
---

export KUBECONFIG=~/Desktop/Inv/ranch-meta-gpu.yaml
kubectl -n dtw-meta-dev port-forward svc/meta-frontend-redis 6379:6379
REDIS_URL="redis://127.0.0.1:6379" node server.js 
