# integration-manager-worker-helm-chart

## Introduction

This chart installs a DataConnect and DataFlow Worker pool for Integration Manager for a specific destination

Add the following repository to helm:  
```helm repo add actian-datacloud https://s3.amazonaws.com/actian-datacloud-helm-charts```

To install the chart, first configure an override-values.yaml file specific for your environment:  
```helm install actian-datacloud/integration-manager-worker -f override-values.yaml```

## Configuration

The following table lists the configurable parameters of the integration-manager-worker chart and their default values.
  
| Parameter | Description | Default|
| -----  | ----- | ------|
| `imagePullSecrets` | name of Secret resource containing private registry credentials | [] |
| `image` | image to pull | actian/datacloud-worker:2.0.5.270 |
| `imagePullPolicy` | When to pull image | IfNotPresent |
| `namespaced` | true / false : whether you want worker to run in its own namespace. If namespaced, namespace = \"\[destinationId\]-\[ReleaseName\]\" | false |
| `existingRabbitSecret` | name of RabbitMQ secret that already exists | nil |
| `replicaCount` | number of pods to run | 1 |
| `extraConfig` | additional properties to include in the config map | {} |
| `extraLabels` | additional labels to add | {} |
| `podAnnotations` | pod annotations | {} |
| `resources` | set resource limits | {} |
| `nodeSelector` | set nodeSelector | {} |
| `extraVolumes` | extra volume for deployment | [] |
| `extraVolumeMounts` | extra volume mounts for deployment | [] |
| `concurrency` | number of jobs worker can run in parallel | 1 |
| `terminationGracePeriodSeconds` | Amount of time to wait for current jobs to finish before forceful shutdown | 172800 |
| `destinationId` | ID of the destination worker is attaching to | nil |
| `pdb` | pod disruption budget | {} |
| `amqp.host` | host name of amqp server | nil |
| `amqp.port` | port of the amqp server | 5672 |
| `amqp.username` | username for amqp authentication | nil | 
| `amqp.password` | password for amqp authentication | nil |
| `amqp.ssl` | use ssl | false |
| `license` | contents of dc11.slc file | nil |
| `dflicense` | contents of df6.slc file | nil |
| `externalSecrets.enabled` | contents of df6.slc file | false |
| `externalSecrets.backendType` | secretsManager, azureKeyVault | nil |
| `externalSecrets.keyVaultName` | required if backendType is azureKeyVault  | nil |
| `externalSecrets.keyName` | name of the secret  | nil |
| `externalSecrets.keyProperty` | property of the secret  | nil |
| `dockerConfiguration` | base64 encoded docker authentication  | nil |