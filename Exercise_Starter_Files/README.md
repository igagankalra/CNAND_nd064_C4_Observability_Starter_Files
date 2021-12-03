**Note:** For the screenshots, you can store all of your answer images in the `answer-img` directory.

## Install  HELM 

```Shell
localhost:/home/vagrant # curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/master/scripts/get-helm-3
localhost:/home/vagrant # ls
bin  get_helm.sh
localhost:/home/vagrant # chmod +x get_helm.sh 
localhost:/home/vagrant # ./get_helm.sh 
Downloading https://get.helm.sh/helm-v3.7.1-linux-amd64.tar.gz
Verifying checksum... Done.
Preparing to install helm into /usr/local/bin
helm installed into /usr/local/bin/helm
localhost:/home/vagrant # helm version
W1202 14:41:43.042635    9586 loader.go:221] Config not found: descriptor/k3
version.BuildInfo{Version:"v3.7.1", GitCommit:"1d11fcb5d3f3bf00dbe6fe31b8412.9"}

master:/home/vagrant # helm install prometheus prometheus-community/kube-prometheus-stack --namespace monitoring --kubeconfig /etc/rancher/k3s/k3s.yaml
W1202 19:43:25.739091   12605 warnings.go:70] policy/v1beta1 PodSecurityPolicy is deprecated in v1.21+, 
unavailable in v1.25+
W1202 19:43:25.746758   12605 warnings.go:70] policy/v1beta1 PodSecurityPolicy is deprecated in v1.21+, 
unavailable in v1.25+
W1202 19:43:25.751327   12605 warnings.go:70] policy/v1beta1 PodSecurityPolicy is deprecated in v1.21+, 
unavailable in v1.25+
W1202 19:43:25.755134   12605 warnings.go:70] policy/v1beta1 PodSecurityPolicy is deprecated in v1.21+, 
unavailable in v1.25+
W1202 19:43:25.759686   12605 warnings.go:70] policy/v1beta1 PodSecurityPolicy is deprecated in v1.21+, 
unavailable in v1.25+
W1202 19:43:25.763827   12605 warnings.go:70] policy/v1beta1 PodSecurityPolicy is deprecated in v1.21+, 
unavailable in v1.25+
W1202 19:43:25.767921   12605 warnings.go:70] policy/v1beta1 PodSecurityPolicy is deprecated in v1.21+, 
unavailable in v1.25+
W1202 19:43:26.944415   12605 warnings.go:70] policy/v1beta1 PodSecurityPolicy is deprecated in v1.21+, 
unavailable in v1.25+
W1202 19:43:27.668987   12605 warnings.go:70] policy/v1beta1 PodSecurityPolicy is deprecated in v1.21+, 
unavailable in v1.25+
W1202 19:43:58.061889   12605 warnings.go:70] policy/v1beta1 PodSecurityPolicy is deprecated in v1.21+, 
unavailable in v1.25+
W1202 19:43:58.288597   12605 warnings.go:70] policy/v1beta1 PodSecurityPolicy is deprecated in v1.21+, 
unavailable in v1.25+
W1202 19:43:58.355299   12605 warnings.go:70] policy/v1beta1 PodSecurityPolicy is deprecated in v1.21+, 
unavailable in v1.25+
W1202 19:43:58.392474   12605 warnings.go:70] policy/v1beta1 PodSecurityPolicy is deprecated in v1.21+, 
unavailable in v1.25+
W1202 19:43:58.399293   12605 warnings.go:70] policy/v1beta1 PodSecurityPolicy is deprecated in v1.21+, 
unavailable in v1.25+
W1202 19:43:58.404249   12605 warnings.go:70] policy/v1beta1 PodSecurityPolicy is deprecated in v1.21+, 
unavailable in v1.25+
W1202 19:43:58.405859   12605 warnings.go:70] policy/v1beta1 PodSecurityPolicy is deprecated in v1.21+, 
unavailable in v1.25+
W1202 19:43:58.418004   12605 warnings.go:70] policy/v1beta1 PodSecurityPolicy is deprecated in v1.21+, 
unavailable in v1.25+
W1202 19:44:02.875624   12605 warnings.go:70] policy/v1beta1 PodSecurityPolicy is deprecated in v1.21+, 
unavailable in v1.25+
W1202 19:44:03.760917   12605 warnings.go:70] policy/v1beta1 PodSecurityPolicy is deprecated in v1.21+, 
unavailable in v1.25+
W1202 19:44:20.024203   12605 warnings.go:70] policy/v1beta1 PodSecurityPolicy is deprecated in v1.21+, unavailable in v1.25+
NAME: prometheus
LAST DEPLOYED: Thu Dec  2 19:43:23 2021
NAMESPACE: monitoring
STATUS: deployed
REVISION: 1
NOTES:
kube-prometheus-stack has been installed. Check its status by running:
  kubectl --namespace monitoring get pods -l "release=prometheus"

Visit https://github.com/prometheus-operator/kube-prometheus for instructions on how to create & configure Alertmanager and Prometheus instances using the Operator.
master:/home/vagrant # kubectl --namespace monitoring get pods -l "release=prometheus"
NAME                                                   READY   STATUS    RESTARTS   AGE
prometheus-prometheus-node-exporter-2twjn              1/1     Running   0          2m10s
prometheus-kube-prometheus-operator-6457c7d44c-5wzsm   1/1     Running   0          2m10s
master:/home/vagrant # kubectl get all -n monitoring
NAME                                                         READY   STATUS    RESTARTS   AGE
pod/prometheus-prometheus-node-exporter-2twjn                1/1     Running   0          3m2s
pod/prometheus-kube-prometheus-operator-6457c7d44c-5wzsm     1/1     Running   0          3m2s
pod/prometheus-kube-state-metrics-58c5cd6ddb-m9qtl           1/1     Running   0          3m2s
pod/alertmanager-prometheus-kube-prometheus-alertmanager-0   2/2     Running   0          2m33s
pod/prometheus-prometheus-kube-prometheus-prometheus-0       2/2     Running   0          2m32s
pod/prometheus-grafana-55464db9f4-km864                      2/2     Running   0          3m2s

NAME                                              TYPE        CLUSTER-IP      EXTERNAL-IP   PORT(S)                      AGE
service/prometheus-kube-prometheus-operator       ClusterIP   10.43.47.115    <none>        443/TCP                      3m2s
service/prometheus-kube-prometheus-alertmanager   ClusterIP   10.43.59.141    <none>        9093/TCP                     3m2s
service/prometheus-prometheus-node-exporter       ClusterIP   10.43.2.28      <none>        9100/TCP                     3m2s
service/prometheus-grafana                        ClusterIP   10.43.168.230   <none>        80/TCP                       3m2s
service/prometheus-kube-prometheus-prometheus     ClusterIP   10.43.62.159    <none>        9090/TCP                     3m2s
service/prometheus-kube-state-metrics             ClusterIP   10.43.237.101   <none>        8080/TCP                     3m2s
service/alertmanager-operated                     ClusterIP   None            <none>        9093/TCP,9094/TCP,9094/UDP   2m33s
service/prometheus-operated                       ClusterIP   None            <none>        9090/TCP                     2m32s

NAME                                                 DESIRED   CURRENT   READY   UP-TO-DATE   AVAILABLE   NODE SELECTOR   AGE
daemonset.apps/prometheus-prometheus-node-exporter   1         1         1       1            1           <none>          3m2s

NAME                                                  READY   UP-TO-DATE   AVAILABLE   AGE
deployment.apps/prometheus-kube-prometheus-operator   1/1     1            1           3m2s
deployment.apps/prometheus-kube-state-metrics         1/1     1            1           3m2s
deployment.apps/prometheus-grafana                    1/1     1            1           3m2s

NAME                                                             DESIRED   CURRENT   READY   AGE
replicaset.apps/prometheus-kube-prometheus-operator-6457c7d44c   1         1         1       3m2s
replicaset.apps/prometheus-kube-state-metrics-58c5cd6ddb         1         1         1       3m2s
replicaset.apps/prometheus-grafana-55464db9f4                    1         1         1       3m2s

NAME                                                                    READY   AGE
statefulset.apps/alertmanager-prometheus-kube-prometheus-alertmanager   1/1     2m33s
statefulset.apps/prometheus-prometheus-kube-prometheus-prometheus       1/1     2m32s
master:/home/vagrant # 
```

## Install Jaeger and prometheus
```Shell
master:/home/vagrant # kubectl create namespace observability
namespace/observability created
master:/home/vagrant # kubectl get ns
NAME              STATUS   AGE
default           Active   32m
kube-system       Active   32m
kube-public       Active   32m
kube-node-lease   Active   32m
monitoring        Active   6m27s
observability     Active   6s
master:/home/vagrant # 
```

## Create a Basic Dashboard
*TODO:* Create a dashboard in Grafana that shows Prometheus as a source. Take a screenshot and include it here.

## Describe SLO/SLI
*TODO:* Describe, in your own words, what the SLIs are, based on an SLO of *monthly uptime* and *request response time*.

## Creating SLI metrics.
*TODO:* It is important to know why we want to measure certain metrics for our customer. Describe in detail 5 metrics to measure these SLIs. 

## Create a Dashboard to measure our SLIs
*TODO:* Create a dashboard to measure the uptime of the frontend and backend services We will also want to measure to measure 40x and 50x errors. Create a dashboard that show these values over a 24 hour period and take a screenshot.

## Tracing our Flask App
*TODO:*  We will create a Jaeger span to measure the processes on the backend. Once you fill in the span, provide a screenshot of it here. Also provide a (screenshot) sample Python file containing a trace and span code used to perform Jaeger traces on the backend service.

## Jaeger in Dashboards
*TODO:* Now that the trace is running, let's add the metric to our current Grafana dashboard. Once this is completed, provide a screenshot of it here.

## Report Error
*TODO:* Using the template below, write a trouble ticket for the developers, to explain the errors that you are seeing (400, 500, latency) and to let them know the file that is causing the issue also include a screenshot of the tracer span to demonstrate how we can user a tracer to locate errors easily.

TROUBLE TICKET

Name:

Date:

Subject:

Affected Area:

Severity:

Description:


## Creating SLIs and SLOs
*TODO:* We want to create an SLO guaranteeing that our application has a 99.95% uptime per month. Name four SLIs that you would use to measure the success of this SLO.

## Building KPIs for our plan
*TODO*: Now that we have our SLIs and SLOs, create a list of 2-3 KPIs to accurately measure these metrics as well as a description of why those KPIs were chosen. We will make a dashboard for this, but first write them down here.

## Final Dashboard
*TODO*: Create a Dashboard containing graphs that capture all the metrics of your KPIs and adequately representing your SLIs and SLOs. Include a screenshot of the dashboard here, and write a text description of what graphs are represented in the dashboard.  
