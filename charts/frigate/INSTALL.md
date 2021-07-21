# Frigate - NVR With Realtime Object Detection for IP Cameras

This is a helm chart for [frigate](https://github.com/blakeblackshear/frigate)

## TL;DR;

```shell
$ helm repo add blakeshome https://blakeblackshear.github.io/blakeshome-charts/
$ helm install blakeshome/frigate
```

## Requirements
MQTT server in either thesame namespace or reachable via IP or FQDN

## Installing the Chart

To install the chart with the release name `frigate`:

### Create credentials seceret
```console
kc create secret generic frigate-rstp-credentials --from-literal=FRIGATE_RTSP_USERNAME=<username> --from-literal=FRIGATE_RTSP_PASSWORD=<password> -n <namespace>
```

### Install MQTT is not already available
```console
helm install mosquitto k8s-at-home/mosquitto
```

### Install Frigate
```console
helm install frigate blakeshome/frigate
```

If using the Coral USB TPU module (strongly recommended), you can use `nodeAffinity` rules to designate which node the pod is scheduled to in order to have host-access to the device, for example:

```yaml
affinity:
  nodeAffinity:
    requiredDuringSchedulingIgnoredDuringExecution:
      nodeSelectorTerms:
      - matchExpressions:
        - key: tpu
          operator: In
          values:
          - google-coral
```

... where a node with an attached Coral USB device is labeled with `tpu: google-coral`

## Uninstalling the Chart

To uninstall/delete the `frigate` deployment:

```console
helm delete frigate
```

The command removes all the Kubernetes components associated with the chart and deletes the release.

## Configuration

Read through the [values.yaml](https://github.com/blakeblackshear/blakeshome-charts/blob/master/charts/frigate/values.yaml) file. It has several commented out suggested values.

Also reference https://blakeblackshear.github.io/frigate/configuration/index for detailed frigate configuration settings.

Specify each parameter using the `--set key=value[,key=value]` argument to `helm install`. For example,

```console
helm install frigate \
  --set rtspPassword="someValue" \
    blakeshome/frigate
```

Alternatively, a YAML file that specifies the values for the above parameters can be provided while installing the chart. For example,

```console
helm install --name frigate -f values.yaml blakeshome/frigate
```
