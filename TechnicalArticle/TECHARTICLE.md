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
| | | | | |
|:-------:|:-------:|:-------:|:-------:|:-------:|
|VS 2017|.NET Core|Web API 2|ASP.NET Core|Redis Cache|
|C#|Swagger|[TweetInvi](https://github.com/linvi/tweetinvi/wiki/Introduction)|[Spackle](https://github.com/JasonBock/SpackleNet)|[Autofac for ASP.NET Core](http://autofac.readthedocs.io/en/latest/integration/aspnetcore.html)|

# Amazon's Elastic Container Services (ECS)



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

# Ci / Cd Pipeline
After your cluster is defined, you can:
- hook up your project from GitHub. In this case I am using my [Tweet Cache REST API](https://github.com/anibalvelarde/TweetCacheApi) project on GitHub.com.
- define a build operation. You can use a variety of tools from AWS and 3rd Party
- define a release operation. You can use a variety of tools from AWS. 

**UPDATE:**
After further investigation, I realized that there is an easier way to do this with a new AWS feature called [AWS CodeStar](https://console.aws.amazon.com/codestar/home?region=us-east-1#/). With this tool you can (from a single pane of glass):
- Create new applications (with a variety of tech stacks)
- Work across your team securely
- Manage software delivery

### CodeStar Useful Links:
- [Getting Started](https://docs.aws.amazon.com/codestar/latest/userguide/getting-started.html?icmpid=docs_acs_console_mk)
- [Documentation](https://docs.aws.amazon.com/codestar/latest/userguide/welcome.html?icmpid=docs_acs_console_mk)
- [Forums](https://forums.aws.amazon.com/forum.jspa?forumID=248)



# Instructions from Amazon Web Services
- [REST API How-To](https://aws.amazon.com/getting-started/serverless-web-app/module-4/?sc_channel=sm&sc_publisher=TWITTER&sc_geo=GLOBAL&sc_outcome=AWS%20Support&trk=_TWITTER&linkId=50200643)
- [General AWS Help Directory](https://aws.amazon.com/premiumsupport/knowledge-center/get-aws-help/)

# Instructions from other Cloud Providers
The [Cloud Trials](https://twitter.com/CloudTrials) Twitter account [tweeted out a request](https://twitter.com/CloudTrials/status/983122616197304320) to other cloud providers (Azure, Google Cloud, Heroku) to see if they could share any `help` or `how-to-type` of documentation about building / deploying a REST API on their corresponding platforms. I'll draw on any info that comes from that resource to see how this same REST API can be built in other cloud services.

