---
authors:
- email: test@test.com
  image: 
  name: Test Test
blog/category:
- Research
blog/tag:
- aws
- ecs
- containers
- docker
date: 2021-01-29
description: Our new research shows Amazon's ECS steadily gaining steam
draft: false
image: ecs-monitoring.png
meta_title: 3 clear trends in ECS adoption
preview_image: ecs-monitoring.png
slug: 3-clear-trends-in-ecs-adoption
sub_featured: false
technology: aws ecs
title: 3 clear trends in ECS adoption
tcp:
- title: "Research Study: 8 Emerging Trends in Container Orchestration"
  desc: "Gain new insights into ECS, Kubernetes, Docker orchestration trends.  "
  cta: "Download to learn more  "
  link: "https://www.datadoghq.com/resources/8-emerging-trends-in-container-orchestration/?utm_source=Content&utm_medium=whitepaper&utm_campaign=BlogCTA-OrchestrationTrends"
  img: Thumbnail-ContainerOrchestrationDec2018.png 

---

Last year, we published [a study of Docker usage][docker-adopt] across our broad customer base. The data, which we then updated in June 2016, shows that the excitement around Docker is not just hype. Docker is being used at a large and ever-increasing number of organizations, and the companies that try Docker tend to stick with it.

As this young technology finds increasing use in production environments, we decided to take a deeper look at how organizations are managing their containerized application infrastructure. At Datadog, we have seen a tremendous amount of interest in container orchestration tools such as [Kubernetes][k8s-guide] and [Amazon ECS][ecs-dd], but we wanted to see if our anecdotal observations were backed up by actual usage data.  

Because we have thousands of customers running Docker, we can see usage and adoption trends emerging in real-time. In this article we'll examine how organizations are using ECS specifically, although we plan to study container orchestration more broadly in the future. We've chosen to focus on ECS initially because [Datadog's integration with ECS][ecs-dd] has been generally available for well over a year, giving our customers plenty of time to start using it.

## Background: How ECS works 

Amazon's [EC2 Container Service (ECS)][ecs] is a hosted service for managing and orchestrating [Docker containers][docker-prob] in the AWS cloud. As the name suggests, ECS allows you to run Docker containers on a cluster of EC2 instances. ECS handles the scheduling and placement of containers across your cluster, balances load across containerized services, and can be configured to automatically scale your container infrastructure based on demand. And of course ECS integrates neatly with other AWS services, such as CloudWatch, ELB (Elastic Load Balancing) and Auto Scaling. 

## Trend 1: ECS is quietly, steadily gaining steam

ECS does not have the buzz or community that buoys the open source competitor Kubernetes, but our data shows that ECS is getting plenty of real-world use. In the year-plus since Datadog's ECS integration was first released, ECS adoption has climbed steadily from zero to 15 percent of Docker organizations using Datadog. (And [more than 10 percent][docker-1] of all Datadog customers are now using Docker.)

{{< img src="ecs-monitoring-01.png" alt="ECS monitoring - adoption among Docker users" popup="true" >}}

> ECS is steadily gaining steam for Docker orchestration.

<div class="text-center">

<a href="https://twitter.com/intent/tweet?text=Amazon%20ECS%20is%20steadily%20gaining%20steam%20for%20%23Docker%20orchestration%2C%20%40datadoghq%20research%20shows%20http%3A%2F%2Fdtdg.co%2Fecs-research%20https%3A%2F%2Ftwitter.com%2Fdd_docker%2Fstatus%2F803703172304773120%2Fphoto%2F1" target="_blank" class="button-tweet button-light-blue"><i class="icon icon-twitter"></i>TWEET</a>

</div>

The graph of ECS adoption as a share of Docker users shows a slight flattening in recent months, but it's important to note that this analysis may underestimate the share of Docker users in Datadog's customer base who run ECS.[^fn-mktshare]

## Trend 2: More containers, more problems

As you might expect, orchestration is more prevalent in organizations with more Docker. After all, manually shepherding your containers is fine for small projects, but can become untenable as the number of hosts and containers grows.

Among Datadog users, we see very limited usage of ECS in organizations where fewer than five unique hosts report Docker metrics over the course of a month.[^fn-october] But as the Docker infrastructure grows, so does the likelihood that a given organization will orchestrate its containers using ECS. Nearly 40 percent of organizations monitoring large Docker installations of more than 100 hosts are also monitoring ECS. 

{{< img src="ecs-monitoring-docker-hosts-01.png" alt="ECS monitoring - adoption as a function of Docker infrastructure size" popup="true" >}}

> ECS usage correlates with larger, more complex Docker infrastructure.

<div class="text-center">

<a href="https://twitter.com/intent/tweet?text=AWS%20ECS%20usage%20correlates%20with%20larger%2C%20more%20complex%20%23Docker%20infrastructure%20http%3A%2F%2Fdtdg.co%2Fecs-research%20via%20%40datadoghq%20https%3A%2F%2Ftwitter.com%2Fdd_docker%2Fstatus%2F803703302131064832%2Fphoto%2F1" target="_blank" class="button-tweet button-light-blue"><i class="icon icon-twitter"></i>TWEET</a>

</div>

Bucketing organizations by the number of unique Docker _images_ in use, rather than unique hosts, reveals a similar pattern: The more images an organization uses, the higher the rate of ECS use.

{{< img src="ecs-monitoring-docker-images-01.png" alt="ECS monitoring - adoption as a function of Docker infrastructure complexity" popup="true" >}}

## Trend 3: Orchestration accompanies growth

Whether increasingly complex infrastructure demands orchestration, or orchestration opens the door to more complex container infrastructure, one thing is clear: the typical organization's container infrastructure grows significantly right around the time that they start using ECS.

The graphs below track the increase in running containers and Docker hosts associated with a typical organization's adoption of ECS (as inferred from the first arrival of ECS metrics). The counts are normalized per organization so that a value of 1.0 represents the organization's average value across the time window.

We include a 60-day "before" window to show that the baseline prior is fairly steady, then starts to increase around 10 days before ECS adoption. This early ramp-up could be explained by organizations making changes to their infrastructure in preparation for a cutover, or by a lag between the actual *adoption* of ECS and the start of *monitoring* ECS with Datadog.

{{< img src="ecs-monitoring-running-containers-01.png" alt="ECS monitoring - Number of Docker containers before and after ECS" popup="true" >}}

> Companies start using more containers and Docker hosts when they adopt ECS.

<div class="text-center">

<a href="https://twitter.com/intent/tweet?text=Companies%20start%20using%20more%20%23Docker%20containers%20%26%20hosts%20when%20they%20adopt%20AWS%20ECS%20http%3A%2F%2Fdtdg.co%2Fecs-research%20via%20%40datadoghq%20https%3A%2F%2Ftwitter.com%2Fdd_docker%2Fstatus%2F803703424223092736%2Fphoto%2F1" target="_blank" class="button-tweet button-light-blue"><i class="icon icon-twitter"></i>TWEET</a>

</div>

In the 30 days after an organization starts reporting ECS metrics, we see a 35 percent increase in the number of running containers as compared to the 60-day baseline that came before. Using the same parameters, we see a 27 percent increase in the number of running Docker hosts. 

{{< img src="ecs-monitoring-docker-hosts-02.png" alt="ECS monitoring - Number of Docker hosts before and after ECS" popup="true" >}}

## Tuning up the orchestra

Docker is still a young technology, and the tooling around it is younger still. But all indications from our ECS analysis and our larger [Docker adoption study][docker-adopt] are that plenty of organizations are already getting serious about containerization. 

As container orchestration marches closer to the mainstream, we will continue to keep an eye on emerging trends. Look out for new and updated analyses on Docker adoption, ECS usage, and other infrastructure trends in the coming months. 

## Footnotes

[^fn-ecs]: In this analysis, the organizations reporting metrics from EC2 are used as a proxy for all customers monitoring AWS with Datadog.
[^fn-october]: These percentages are calculated from host and image counts during the month of October 2016.
[^fn-mktshare]: The percentages in this graph are calculated by selecting all the organizations that enabled the Docker integration in Datadog, and determining which of those organizations also have ECS enabled in their account. But some organizations may run ECS without native Docker instrumentation, so they are excluded from the calculation. 

[ecs]:           https://aws.amazon.com/ecs/
[docker-prob]:   https://www.datadoghq.com/blog/the-docker-monitoring-problem/
[docker-adopt]:  https://www.datadoghq.com/docker-adoption/
[docker-1]:      https://www.datadoghq.com/docker-adoption/#1
[k8s-guide]:     https://www.datadoghq.com/blog/monitoring-kubernetes-era/
[mesos-dd]:      https://www.datadoghq.com/blog/monitor-mesos-cluster-datadog/
[ecs-dd]:        https://www.datadoghq.com/blog/monitor-docker-on-aws-ecs/

