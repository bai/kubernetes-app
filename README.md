# Grafana App for Kubernetes

[Kubernetes](http://kubernetes.io/) is an open-source system for automating deployment, scaling, and management of containerized applications.

The Grafana Kubernetes App allows you to monitor your Kubernetes cluster's performance. It includes 4 dashboards, Cluster, Node, Pod/Container and Deployment. It allows for the automatic deployment of the required Prometheus exporters and a default scrape config to use with your in cluster Prometheus deployment. The metrics collected are high-level cluster and node stats as well as lower level pod and container stats. Use the high-level metrics to alert on and the low-level metrics to troubleshoot.

![Container Dashboard](https://github.com/grafana/kubernetes-app/blob/master/src/img/cluster-dashboard-screenshot.png?raw=true)

![Container Dashboard](https://github.com/grafana/kubernetes-app/blob/master/src/img/container-dashboard-screenshot.png?raw=true)

![Node Dashboard](https://github.com/grafana/kubernetes-app/blob/master/src/img/node-dashboard-screenshot.png?raw=true)

### Requirements

1. Currently only has support for [**Prometheus**](https://prometheus.io/docs/prometheus/latest/querying/basics/)
2. For automatic deployment of the exporters, then Kubernetes 1.6 or higher is required.
3. Grafana 5.0.0+

### Features

- The app uses Kubernetes tags to allow you to filter pod metrics. Kubernetes clusters tend to have a lot of pods and a lot of pod metrics. The Pod/Container dashboard leverages the pod tags so you can easily find the relevant pod or pods.

- Easy installation of exporters, either a one click deploy from Grafana or detailed instructions to deploy them manually them with kubectl (also quite easy!)

- Cluster level metrics that are not available in Heapster, like CPU Capacity vs CPU Usage.

### Cluster Metrics

- Pod Capacity/Usage
- Memory Capacity/Usage
- CPU Capacity/Usage
- Disk Capacity/Usage
- Overview of Nodes, Pods and Containers

### Node Metrics

- CPU
- Memory Available
- Load per CPU
- Read IOPS
- Write IOPS
- %Util
- Network Traffic/second
- Network Packets/second
- Network Errors/second

### Pod/Container Metrics

- Memory Usage
- Network Traffic
- CPU Usage
- Read IOPS
- Write IOPS

### Connect your cluster

1. Install the plugin per the [Installation instructions](https://grafana.com/grafana/plugins/grafana-kubernetes-app/installation).

1. Go to the Cluster List page via the Kubernetes app menu.

    ![Cluster List in main menu](https://github.com/grafana/kubernetes-app/blob/master/src/img/app-menu-screenshot.png?raw=true)

1. Click the `New Cluster` button.

1. Fill in the Auth details for your cluster.

     TLS certs/keys must be provided in plaintext, not base64 encoded form. For example:
     ```
     -----BEGIN CERTIFICATE-----
    MIQWQtAEFeqqfAFeAEGEQWIGNwEQNFGQ4AEFN35AKWadgAENGqiEGNIWm1QETDGF
     ...
     -----END CERTIFICATE-----
     ```

1. Choose the Prometheus datasource that will be used for reading data in the dashboards.

1. Click `Deploy`. This will deploy a Node Exporter DaemonSet, to collect health metrics for every node, and a Deployment that collects cluster metrics.

### Feedback and Questions

Please submit any issues with the app on [Github](https://github.com/grafana/kubernetes-app/issues).
