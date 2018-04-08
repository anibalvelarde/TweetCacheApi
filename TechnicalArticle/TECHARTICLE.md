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

# Elastic Container Services

- You must first define a [Task on ECS](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/task_definitions.html)