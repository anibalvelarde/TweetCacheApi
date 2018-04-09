# TweetCacheApi
###### [Formatted with Markdown](https://github.com/adam-p/markdown-here/wiki/Markdown-Here-Cheatsheet)

The basis for this work is 3 fold:
- Learn about cloud technologies (AWS specifically)
- Learn about API creation and reinforce elements learned from [Designing Evolvable APIs with ASP.NET](https://www.amazon.com/gp/product/1449337716/ref=oh_aui_detailpage_o05_s01?ie=UTF8&psc=1)
- Document what I'm learning on this forum 

# What is TweetCacheApi
  
This is an applicaiton that will take avantage of Twitter's Developer API services and perform searches about activities of specific Twitter accounts and display that activity for later reference from a client applicaiton. Since the free Twitter service only goes back 7 days in the past, this API will use cache of up to 21 days in the past.

# Cloud platforms
- Amazon Web Services
- Elastic Container Service (ECS)

# 3rd Party Cloud services
- Twitter API

# Application Architecture
- REST API


# Techniques, Patterns and Principles used
- Separation of Concerns
- Caching

# Technologies used
- VS 2017
- .NET Core
- Web API 2
- ASP.NET Core
- Redis Cache
- C#
- Swagger
- [TweetInvi](https://github.com/linvi/tweetinvi/wiki/Introduction)
- [Spackel](https://github.com/JasonBock/SpackleNet)

# Elastic Container Services

### Define a Task on ECS
First, to run Docker containters you must define a [Task on ECS](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/task_definitions.html).
Tasks are the templates that describe the virtual manchine that you want to stand up as an EC2 instance. This is the
template that is followed when yout automate the creation of your EC2 instance.

### Selecting the Launch Type
> Decided to use **EC2 Launch Type** because I will be breaking the applicaiton into 3 major parts
> - a front end app
> - a back end REST API (this API)
> - a data store as in memory cache (most likely **Redis Cache**) 

### Create a Cluster
A cluster is the "box" in which your container is going to run. You can have clusters of Linux or Windows containers.
The resources that are created include Cluster, VPC, Subnets and Auto-Scaling groups with Windows AMI.

Regarding **VPC** definiiton, there is some great [info at AWS here](https://docs.aws.amazon.com/AmazonVPC/latest/UserGuide/VPC_Subnets.html).

### Create Ci / Cd Pipelines
After your cluster is defined, you can:
- hook up your project from GitHub. In this case I am using my [Tweet Cache REST API](https://github.com/anibalvelarde/TweetCacheApi) project on GitHub.com.
- define a build operation. You can use a variety of tools from AWS and 3rd Party
- define a release operation. You can use a variety of tools from AWS. 

