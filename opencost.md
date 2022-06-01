<!-- Output copied to clipboard! -->

<!-----

You have some errors, warnings, or alerts. If you are using reckless mode, turn it off to see inline alerts.
* ERRORs: 0
* WARNINGs: 0
* ALERTS: 3

Conversion time: 1.087 seconds.


Using this Markdown file:

1. Paste this output into your source file.
2. See the notes and action items below regarding this conversion run.
3. Check the rendered output (headings, lists, code blocks, tables) for proper
   formatting and use a linkchecker before you publish this page.

Conversion notes:

* Docs to Markdown version 1.0β33
* Wed Jun 01 2022 14:25:48 GMT-0700 (PDT)
* Source doc: Untitled document
* This is a partial selection. Check to make sure intra-doc links work.
* Tables are currently converted to HTML tables.
* This document has images: check for >>>>>  gd2md-html alert:  inline image link in generated source and store images to your server. NOTE: Images in exported zip file from Google Docs may not appear in  the same order as they do in your doc. Please check the images!

----->


<p style="color: red; font-weight: bold">>>>>>  gd2md-html alert:  ERRORs: 0; WARNINGs: 0; ALERTS: 3.</p>
<ul style="color: red; font-weight: bold"><li>See top comment block for details on ERRORs and WARNINGs. <li>In the converted Markdown or HTML, search for inline alerts that start with >>>>>  gd2md-html alert:  for specific instances that need correction.</ul>

<p style="color: red; font-weight: bold">Links to alert messages:</p><a href="#gdcalert1">alert1</a>
<a href="#gdcalert2">alert2</a>
<a href="#gdcalert3">alert3</a>

<p style="color: red; font-weight: bold">>>>>> PLEASE check and correct alert issues and delete this message and the inline alerts.<hr></p>


The OpenCost Spec is a vendor-neutral specification for measuring and allocating infrastructure and container costs in Kubernetes environments. 


## 
**Introduction** {#introduction}


Kubernetes enables complex deployments of containerized workloads, which are often transient and consume variable amounts of cluster resources. While this enables teams to construct powerful solutions to a broad range of technical problems, it also creates complexities when measuring the resource utilization and costs of workloads and their associated infrastructure within the  dynamics of shared Kubernetes environments. 


As Kubernetes adoption increases within an organization, these complexities become a business-critical challenge to solve. In this document, we specify a vendor-agnostic methodology for accurately measuring and allocating the costs of a Kubernetes cluster to its hosted tenants. This community resource is maintained by Kubernetes practitioners and we welcome all contributions. 


## 
**Foundational definitions ** {#foundational-definitions}

**Total Cluster Costs** represent all costs required to operate a Kubernetes cluster. **Cluster Assets Costs** are the portion of these costs that are related to directly observable entities within a cluster; these include expenses from nodes, persistent volumes, attached disks, load balancers, and network ingress/egress costs. From a financial accounting perspective, these are equivalent to the Cost of Goods Sold when measuring product costs. **Cluster Overhead Costs** measure the overhead required to operate all of the Assets of a cluster, e.g. Cluster Management Fees. These are the equivalent to Selling, General and Administrative Expenses (SG&A), or indirect costs, when viewed from a financial accounting perspective.


<table>
  <tr>
   <td><strong>Total Cluster Costs</strong>
   </td>
   <td><strong>=</strong>
   </td>
   <td><strong>Cluster Asset Costs</strong>
   </td>
   <td><strong>+</strong>
   </td>
   <td><strong>Cluster Overhead Costs</strong>
   </td>
  </tr>
</table>


Cluster Asset Costs can be further segmented into **Resource Allocation Costs** and **Resource Usage Costs**. Resource Allocation Costs are expenses that accumulate based on the amount of time provisioned irrespective of usage (e.g. CPU hourly rate) whereas Resource Usage Costs accumulate on a per-unit basis (e.g. cost per byte egressed). Costs for an individual Asset are the summation of it’s Resource Allocation and Usage Costs, e.g. a Node’s cost is equal to CPU cost + GPU cost + RAM cost + Node Network Costs


<table>
  <tr>
   <td><strong>Total Cluster Costs</strong>
   </td>
   <td><strong>=</strong>
   </td>
   <td><strong>Resource Allocation Costs</strong>
<p>
(for all assets)
   </td>
   <td><strong>+</strong>
   </td>
   <td><strong>Resource Usage Costs</strong>
<p>
(for all assets)
   </td>
   <td><strong>+</strong>
   </td>
   <td><strong>Cluster Overhead Costs</strong>
<p>
(for cluster)
   </td>
  </tr>
</table>


The following chart shows these relationships:



<p id="gdcalert1" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image1.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert2">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image1.png "image_tooltip")


While billing models can differ by environment, below are common examples of segmentation by Allocation, Usage and Overhead Costs.



<p id="gdcalert2" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image2.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert3">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image2.png "image_tooltip")


Once calculated, these Asset Costs can then be distributed to the tenants that consume them, where Workload Costs plus Idle Costs equals Asset Costs. **Workload costs** are expenses that can be directly attributed to a set of Kubernetes workloads, e.g. a container, pod, deployment, etc. **Cluster Idle Costs** are the portion of Resource Allocation Costs that are not allocated to any workload[^1].


<table>
  <tr>
   <td><strong>Total Cluster Costs</strong>
   </td>
   <td><strong>=</strong>
   </td>
   <td><strong>Workload Costs</strong>
   </td>
   <td><strong>+</strong>
   </td>
   <td><strong>Cluster Idle Costs</strong>
   </td>
   <td><strong>+</strong>
   </td>
   <td><strong>Cluster Overhead Costs</strong>
   </td>
  </tr>
</table>


The following chart shows these relationships:


## 


<p id="gdcalert3" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image3.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert4">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image3.png "image_tooltip")



## 
**Cluster Asset Costs** {#cluster-asset-costs}

Cluster Assets are observable entities within a Kubernetes cluster that directly incur costs related to their resources. Asset Costs consist of Resource Allocation Costs and Resource Usage Costs. Every Asset conforming to this specification MUST include at least one cost component with Amount, Unit and Rate attributes as well as a TotalCost value. 

Attributes for measured Resource Allocation Costs:



* [float] Amount - the amount of resource reserved by the asset, e.g. 2 CPU cores
* [float] Duration - time between the start and end of the allocation period measured in hours, e.g. 24 hours
* [string] Unit - the amount’s unit of measurement, e.g. CPU cores 
* [float] HourlyRate - cost per one unit hour, e.g. $0.2 per CPU hourly rate
* [float] Total Cost - defined as Amount * Duration * HourlyRate

Attributes for measured Resource Usage Costs:



* [float] Amount - the amount of resource used, e.g. 1GB of internet egress
* [string] Unit - the amount’s unit of measurement, e.g. GB
* [float] UnitRate - cost per unit, e.g $ per GB egressed
* [float] TotalCost - defined as Amount * UnitRate

Below are example inputs when measuring asset costs over a designated time window (e.g. 24 hours) with common billing models:



* **Nodes**
    * CPU allocation costs
        * cores = avg_over_time(cpu) by (node) [cores]
        * duration = end running- start running [hrs]
        * price = provider defined or custom pricing sheet [$/core-hr] (see Appendix A for more details)
        * total cost = cores * duration * price [$]
    * RAM allocation costs
        * ram bytes = avg_over_time(GB) by (node) [ram GBs]
        * duration = end running- start running [hrs]
        * price = provider defined or custom pricing sheet [$/GB-hr] (see Appendix A for more details)
        * total cost = ram bytes * duration * price [$]
* **Persistent Volumes	**
    * Disk Size = avg_over_time(GB) by (pv) [disk GBs]
    * price = price = provider defined or custom pricing sheet [$/GB-hr] (see Appendix A for more details) typically a function of disk class, IOPS, backup size
    * Persistent storage attached to the pod-level
* **Attached disks**
    * Disk Size = avg_over_time(GB) by (pv) [disk GBs]
    * price = price = provider defined or custom pricing sheet [$/GB-hr] (see Appendix A for more details) typically a function of disk class, IOPS, backup size
    * Ephemeral storage used per pod on node
* **Load balancers**
    * Usage costs
        * amount = bytes ingressed
        * price = $ per byte ingressed
    * Allocation costs
        * rules = # of forwarding rules defined
        * price = average $ per forwarding rule
* Overhead Costs
    * **Cluster management** **fees: **provider fees typically charged on an hourly basis
    * **Operator fees: **potential DevOps team costs allocated to cluster operations

## 
**Workload Costs** {#workload-costs}


Workloads** **are defined as entities to which Asset Costs are committed. Some resources solely have Usage Costs, but others have Allocation Costs independent of actual usage. Workload Costs should be understood as _max(request, usage)_ when Assets have Resource Allocation Costs, e.g. CPU or GPU. This formula effectively assigns costs that have been directly reserved or allocated by _kube-scheduler_. Workload Costs should be calculated at the lowest level possible, e.g. _container_ level[^2], and then they can be aggregated by any dimension, e.g. pod, deployment, statefulset, label, annotation, namespace, etc.


<table>
  <tr>
   <td>Resource Type
   </td>
   <td>Measurement
   </td>
  </tr>
  <tr>
   <td>CPU
   </td>
   <td>The greater of <a href="https://kubernetes.io/docs/concepts/configuration/manage-resources-containers/#resource-requests-and-limits-of-pod-and-container">requested</a> and used CPU resources measured in cores or millicores.
   </td>
  </tr>
  <tr>
   <td>Memory
   </td>
   <td>The greater of requested resources and memory in use measured in bytes or gigabytes.
   </td>
  </tr>
  <tr>
   <td>GPU
   </td>
   <td>The greater of requested resources and used resources measured in cores.
   </td>
  </tr>
  <tr>
   <td>Storage Volume
   </td>
   <td>The storage capacity of Persistent Volume Claim (PVC) requests measured in bytes or gigabytes. Attached at the Kubernetes pod-level. 
   </td>
  </tr>
  <tr>
   <td>Network
   </td>
   <td>Amount of ingress or egress across zones, regions, or the wide internet measured in bytes or gigabytes (can vary by provider)
   </td>
  </tr>
  <tr>
   <td>Load Balancer
   </td>
   <td>The number of load balancers used plus the volume of connections and bytes (can vary by provider).
   </td>
  </tr>
</table>



## 
**Shared Costs** {#shared-costs}

Shared Workload Costs, Cluster Idle Costs, and Overhead Costs are common examples of costs that organizations can optionally distribute amongst tenants. A common example would be system workload costs, e.g. kube-system pods, that benefit all tenants. Common methods for distributing these costs include the following:



1. Uniformly across other tenants
2. Proportionate to a tenant's consumption of Cluster Asset costs
3. Custom metric, e.g. bytes of network egress

A full implementation of the spec should support various methods of distributing shared costs. 


## 
**Idle Costs** {#idle-costs}

Idle Costs can be calculated at both the Asset/Resource level as well as the Workload level. Asset Idle Costs represent the cost-weighted difference between Cluster Asset Costs and costs of resources being allocated or consumed. Idle Costs and then Idle Percentage can be calculated as follows:


<table>
  <tr>
   <td><strong>Cluster Idle Cost</strong>
   </td>
   <td><strong>=</strong>
   </td>
   <td><strong>( Cluster Asset Costs</strong>
   </td>
   <td><strong>-</strong>
   </td>
   <td><strong>Workload Costs )</strong>
   </td>
   <td>
   </td>
   <td>
   </td>
  </tr>
</table>



<table>
  <tr>
   <td><strong>Cluster </strong>
<p>
<strong>Idle %</strong>
   </td>
   <td><strong>=</strong>
   </td>
   <td><strong>Idle Cost</strong>
   </td>
   <td><strong>/</strong>
   </td>
   <td><strong>Resource Allocation Costs</strong>
   </td>
  </tr>
</table>



## 
The following chart shows these relationships:    

Asset Idle Cost can be calculated by individual assets, groups of assets, cluster(s), and by individual resources, e.g. CPU. Resources that are strictly billed on usage can be viewed to have 100% efficiency but should not be included when measuring idle percentage of a cluster. 

Workload Idle Costs is a cost-weighted measurement of [requested](https://kubernetes.io/docs/concepts/configuration/manage-resources-containers/#resource-requests-and-limits-of-pod-and-container) resources that are unused. Workload Idle Costs can be calculated on any grouping of Kubernetes workloads, e.g. containers, pods, labels, annotations, namespaces, etc.


## 



## 
**Glossary** {#glossary}


**Cluster Assets** – Observable entities within a Kubernetes cluster that directly incur costs related to their resources. Examples include nodes, persistent volumes, attached disks, load balancers.


**Container** - An instance of a container image. You may have multiple copies of the same image running at the same time. [More info](https://kubernetes.io/docs/concepts/containers/) 


**Image** - A template of a container which contains software (usually microservices) that needs to be run. [More info](https://kubernetes.io/docs/concepts/containers/images/)


**Server / Instance / Node / Node Pool** - A machine (possibly cloud or on-prem, physical or virtual) in this context used by Kubernetes [More info](https://kubernetes.io/docs/concepts/architecture/nodes/)


**Pod** - A Kubernetes specific concept that consists of a group of containers. A pod is treated as a single block of resources that may be scheduled or scaled on a cluster. [More info](https://kubernetes.io/docs/concepts/workloads/pods/)


**Container Orchestration** - Manages the cluster of server instances and maintains the lifecycle of containers and pods. Scheduling is a function of the container orchestrator which schedules pods/containers to run on a server instance. 


**Cluster** - A group of server instances 


**Namespace** - A Kubernetes concept which creates a ‘virtual’ cluster where pods/containers may be deployed and observed discreetly from other namespaces. [More info](https://kubernetes.io/docs/concepts/overview/working-with-objects/namespaces/)


**Pod Labels** - Key / Value pairs which may be used to identify objects that are meaningful to the user. There is no semantic meaning to the core of the system. Labels are typically used where a grouping of multiple namespaces need to be associated with a workload. [More info](https://kubernetes.io/docs/concepts/overview/working-with-objects/labels/)


## 
**Appendix A **

Various cloud providers supply an hourly resource cost directly in their user billing model.The OpenCost model recommends utilizing the fully Amortized Net Cost for each resource as an input when this is the case. When explicit RAM, CPU or GPU prices are not provided by a cloud provider, the OpenCost model needs to derive these values. The recommendation is to use a scalable ratio of CPU, GPU, RAM and other price inputs. These default values should be based on the marginal resource rates of the provider by family.

One approach for calculating is to ensure the sum of each component is equal to the total price of the Asset (e.g. node) based on billing rates from your provider. When the sum of resources (e.g. RAM/CPU/GPU) cost is greater (or less) than the price of the node, then the ratio between the input prices is held constant but the total value is adjusted.

As an example, you have provisioned a node with 1 GPU, 1 CPU and 1 GB of RAM that costs $35/mo. If your base GPU price is $30, base CPU price is $30, and RAM GB price is $10, based on the average marginal costs across instances in this family class, then these inputs will be normalized to $15 for GPU, $15 for CPU and $5 for RAM so that the sum equals the cost of the node. Note that the price of a GPU, as well as the price of a CPU remain 3x the price of a Gb of RAM.


## 



## 
**Appendix B**

Sampling Kubernetes resources is recommended with the following metrics / datasources:



* container_cpu_usage_seconds_total – sample from cAdvisor
* container_memory_working_set_bytes –  sampled from cAdvisor
* gpu_usage – sampled via chipset specific metrics
* cpu_requested – sampled from kube API
* ram_requested – sampled from kube API
* gpu_requested – sampled from kube API

## 
**Appendix C**


Working examples to come! 


<!-- Footnotes themselves at the bottom. -->
## Notes

[^1]:
     Resource **usage** costs cannot be part of idle cost because they are always used, the corresponding resource never "sits idle."

[^2]:
     This is because containers are the smallest identifiable unit of "thing that uses resources." For example, the lowest level of reliable CPU usage information is usually a container.



