# integration-manager-worker-helm-chart

## Introduction

This chart installs a DataConnect Worker pool for Integration Manager for a specific destination

Add the following repository to helm:  
```helm repo add actian-datacloud https://s3.amazonaws.com/actian-datacloud-helm-charts```

To install the chart, first configure a values.yaml file specific for your environment:  
```helm install actian-datacloud/integration-manager-worker -f override-values.yaml```

## Configuration

The following table lists the configurable parameters of the integration-manager-worker chart and their default values.
  
| Paramter | Description | Default|
| -----  | ----- | ------|
| `imagePullSecret` | secret name of holding the docker creds | [] |
| `image` | image to pull | actian/worker-kubernetes:latest |
| `imagePullPolicy` | When to pull image | Always |
| `namespaced` | true / false : whether you want worker to run in its own namespace. If namespaced, namespace = \"\[destinationId\]-\[ReleaseName\]\" | false |
| `existingRabbitSecret` | Name of RabbitMQ secret that already exists | "" |
| `replicaCount` | number of pods to run | 1
| `extraConfig` | additional properties to include in the config map | {} |
| `extraLabels` | additional labels to add | {} |
| `podAnnotations` | pod annotations | {} |
| `resources` | set resource limits | {} |
| `nodeSelector` | set nodeSelctor | {} |
| `extraVolumes` | extra volume for deployment | [] |
| `extraVolumeMounts` | extra volume mounts for deployment | [] |
| `concurrency` | number of jobs worker can run in parallel | 1 |
| `terminationGracePeriodSeconds` | Amount of time to wait for current jobs to finish before forceful shutdown | 172800 |
| `destinationId` | ID of the destination worker is attaching to | "" |
| `fileStorageEndpoint` | cloud file storage endpoint | "" |
| `fileStorageType` | type of cloud file storage | "" |
| `workerType` | type of worker [CLOUD, REMOTE] | CLOUD |
| `pdb` | pod disruption budget | {} |
| `license` | contents of dc11.slc file | "" |
| `amqp.host` | host name of amqp server | |
| `amqp.port` | port of the amqp server | 5672 |
| `amqp.username` | username for amqp authentication | "" | 
| `amqp.password` | password for amqp authenication | ""|
| `amqp.ssl` | use ssl | false |
