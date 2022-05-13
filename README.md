# kdave

The [kdave](https://github.com/wayfair-incubator/kdave) (Kubernetes Depredated API Versions Exporter) checks for any deprecated or removed apiVersions in the cluster and exports them in a Prometheus metrics format. You can integrate it with Prometheus and Alertmanager to receive notifications before upgrading the cluster and break the current workload. It exports detailed metrics such as whether the used apiVersion is deprecated, removed, removed_in_next_release, removed_in_next_2_releases, replacement_api, etc.

## Configuration

The following tables lists the configurable parameters of the kdave chart and their default values.

| Parameter                 | Description                                                                                          | Default                                                           |
| ------------------------- | ---------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------- |
| `replicaCount`            | Number of replicas to run                                                                            | `1`                                                               |
| `name`                    | How to name resources created by this chart                                                          | `kdave`                                                           |
| `debug.enable`            | Do you want to start the application in debug mode                                                   | `false`                                                           |
| `interval`                | Interval between helm check releases jobs in days.                                                   | `1`                                                               |
| `threads`                 | Number of threads to handle helm check releases                                                      | `10`                                                              |
| `max`                     | Maximum number of releases to fetch at once                                                          | `256`                                                             |
| `dataFile`                | The database file location                                                                           | `/app/data/data.json`                                             |
| `helmBinary`              | The helm binary to be used for running helm commands. Default is helm v2.                            | `helm`                                                            |
| `address`                 | The IP address for the Flask server to serve on                                                      | `0.0.0.0`                                                         |
| `port`                    | The Port for the Flask server to serve on                                                            | `8000`                                                            |
| `image.repository`        | The kdave server container image repository                                                          | `aelbakry/kdave-server`                                           |
| `image.tag`               | The kdave server container image tag                                                                 | `1.0.1`                                                           |
| `image.pullPolicy`        | The application container image pull policy                                                          | `IfNotPresent`                                                    |
| `nodeSelector`            | Node labels for the application pod assignment                                                       | `{}`                                                              |
| `priorityClassName`       | Priority class name                                                                                  | `wf-cluster-critical`                                             |
| `tolerations`             | The application pod toleration for taints                                                            | `[]`                                                              |
| `affinity`                | The application pod affinity                                                                         | `{}`                                                              |
| `annotations`             | Annotations to be added to the application pod                                                       | `{}`                                                              |
| `podLabels`               | Labels to be added to the application pod                                                            | `{}`                                                              |
| `resources`               | The application pod resource requests & limits                                                       | `{}`                                                              |
| `securityContext`         | SecurityContext to apply to the the application pod                                                  | `{}`                                                              |
| `rbac.create`             | If true, create & use RBAC resources                                                                 | `true`                                                            |
| `rbac.pspEnabled`         | PodSecuritypolicy                                                                                    | `true`                                                            |
| `rbac.serviceAccountName` | ServiceAccount the application will use (ignored if rbac.create=true)                                | `default`                                                         |
| `extraArgs`               | Add extra args to docker command                                                                     | `[]`                                                              |

Specify each parameter using the --set key=value[,key=value] argument to helm install or provide a YAML file containing the values for the above parameters.
