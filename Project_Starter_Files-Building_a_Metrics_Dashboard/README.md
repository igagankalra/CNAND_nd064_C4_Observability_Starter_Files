**Note:** For the screenshots, you can store all of your answer images in the `answer-img` directory.

## Verify the monitoring installation

*TODO:* run `kubectl` command to show the running pods and services for all components. Take a screenshot of the output and include it here to verify the installation

1. [pod](answer-img/pod_0.PNG)
2. [service](answer-img/services_1.PNG)

## Setup the Jaeger and Prometheus source
*TODO:* Expose Grafana to the internet and then setup Prometheus as a data source. Provide a screenshot of the home page after logging into Grafana.
3. [grafana](answer-img/grafana_3.PNG)

## Create a Basic Dashboard
*TODO:* Create a dashboard in Grafana that shows Prometheus as a source. Take a screenshot and include it here.
4. [Grafana Custom Dashboard](answer-img/custom_grafana_dashboard.PNG)
## Describe SLO/SLI
*TODO:* Describe, in your own words, what the SLIs are, based on an SLO of *monthly uptime* and *request response time*.

A Service-Level Indicator (SLI) is a specific metric used to measure the performance of a service if it met its objective.

For SLO (service Level Object) of monthly uptime of 99.9% every month. As for request response time, the average response time of a web request would take less than 1second to complete.

## Creating SLI metrics.
*TODO:* It is important to know why we want to measure certain metrics for our customer. Describe in detail 5 metrics to measure these SLIs. 

6. Metrics to measure SLIs defined:

   * The time in ms to reply to a request
   * The number of requests received per second
   * The number of failed requests (40x and 50x responses)
   * The percentage of CPU used
   * The application uptime (both front-end and back-end applications)

## Create a Dashboard to measure our SLIs
*TODO:* Create a dashboard to measure the uptime of the frontend and backend services We will also want to measure to measure 40x and 50x errors. Create a dashboard that show these values over a 24 hour period and take a screenshot.
7. [Dashboard 1](answer-img/dashboard_1.png)
8. [Dashboard 2](answer-img/dashboard_2.png)

## Tracing our Flask App
*TODO:*  We will create a Jaeger span to measure the processes on the backend. Once you fill in the span, provide a screenshot of it here. Also provide a (screenshot) sample Python file containing a trace and span code used to perform Jaeger traces on the backend service.
9. [Flask Trace](answer-img/flask_trace.png)


## Jaeger in Dashboards
*TODO:* Now that the trace is running, let's add the metric to our current Grafana dashboard. Once this is completed, provide a screenshot of it here.
10. [Flask Trace](answer-img/jaeger_backemnd_grafana.png)


## Report Error
*TODO:* Using the template below, write a trouble ticket for the developers, to explain the errors that you are seeing (400, 500, latency) and to let them know the file that is causing the issue also include a screenshot of the tracer span to demonstrate how we can user a tracer to locate errors easily.

TROUBLE TICKET
```
Name: Multiple requests returns HTTP 405 i.e. Method Not Allowed response

Date: 2021-12-04

Subject: Multiple requests returns HTTP 405 i.e. Method Not Allowed response

Affected Area: Back-end application

Severity: High

Description: After code update, we have seen multiple requests are being sent to /star method and the backend application returns HTTP 405 Method Not Allowed response. This seems to be related to mongodb setup.
```

## Creating SLIs and SLOs
*TODO:* We want to create an SLO guaranteeing that our application has a 99.95% uptime per month. Name four SLIs that you would use to measure the success of this SLO.

* Error rate
* Uptime
* Response rate & time
* CPU usage

## Building KPIs for our plan
*TODO*: Now that we have our SLIs and SLOs, create a list of 2-3 KPIs to accurately measure these metrics as well as a description of why those KPIs were chosen. We will make a dashboard for this, but first write them down here.

Error rate:

* Number of 4xx and 5xx HTTP request responses
   - Number of requests on average Those KPIs are chosen to see all types of responses and to check if there is a correlation between average response time and response status code.

* Uptime:

   - Uptime of front-end application pods
   - Uptime of back-end application pods Seeing an indicator whether a pod is up or not. Used both for back-end and front-end applications.

* Response rate & time:

   - Average response time of requests
   - Percentage of requests that returned responses under 250ms, these metrics are chosen to check if the load of requests correlate to the response time.

* Resources:

   - Memory(RAM) usage for application pods
   - CPU usage for application pods.
   - These affect client services indirectly.

## Final Dashboard
*TODO*: Create a Dashboard containing graphs that capture all the metrics of your KPIs and adequately representing your SLIs and SLOs. Include a screenshot of the dashboard here, and write a text description of what graphs are represented in the dashboard.  


- Application stats  - It shows information about application services.
- Successful requests - It shows the total number of successful requests.
- Error requests - It shows the total number of 40x and 50x error requests.
- Average response time - It shows the average response time of successful requests (status 200).
- Average memory used - It shows the average memory.
- Average CPU used - It shows the average CPU used.
- Network I/O Pressure - It shows the amount of I/O operations in the node.

11. [Flask Trace](answer-img/final_dashboard_grafana.png)
