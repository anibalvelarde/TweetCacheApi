# TweetCacheApi
###### [Formatted with Markdown](https://github.com/adam-p/markdown-here/wiki/Markdown-Here-Cheatsheet)

The basis for this work is 3 fold:
- Learn about cloud technologies (AWS specifically)
- Learn about API creation and reinforce elements learned from [Designing Evolvable APIs with ASP.NET](https://www.amazon.com/gp/product/1449337716/ref=oh_aui_detailpage_o05_s01?ie=UTF8&psc=1)
- Document what I'm learning on this forum 

# What is TweetCacheApi
  
This is an applicaiton that will take avantage of Twitter's Developer API services and perform searches about activities of specific Twitter accounts and display that activity for later reference from a client applicaiton. Since the free Twitter service only goes back 7 days in the past, this API will use cache of up to 21 days in the past.

# Cloud platforms
- Azure App Services

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

# Azure App Services

This was relatively easy to setup. All I needed to do was:

### Have my code on [GitHub](https://github.com/anibalvelarde/TweetCacheApi)
Just started a regular repo. Coded a few pieces of functionality and also added the test libraries.

**NOTE:** Make sure that you name the unit test project to contain the word "%Tests%.proj" (plural). If TFS CI/CD pipeline does not find that matching word, it will complain saying that it could not find a testing library.  I am sure this is configurable, but the objective of this exercise was to use the most simple of workflows on the Azure platform.

### Have an Azure account with $$$ to use services
In my case, I am using some of the alloted $150.00 credit that having an MSDN Enterprise Developer's licence could afford me.

### Create an **App Services** entry
This created all the resources that were required automatically:
- App Service Plan group
- App Service itself
- Application Insights (I had to opt in to use this)

# Release notes
| Date    | <------------------ Change Description ------------------> | Interesting Observations|
|:-------:|:-----------------------------------------------------------|:-----------------------:|
|4-9-2018 | Initial push to Azure's App Services                       |  -- none --             |

Completing this does not get you anything working (you have not deployed anything yet).  The next part is very important....

### Continuous Integration (Build) & Continuous Delivery (Release) Pipeline
When you click on your newly defined App Service "holder", you will see a menu with many options. Among them, you will see one called "Continuous Delivery (Preview)" - It has been in "preview" for a while now.

When you choose it, you will get to define your pipeline. It was very simple to follow allong. The experience was very intuitive and did not made me think too much. It seems to me that the guys and gals at Azure have been reading a good reference [book](https://play.google.com/store/books/details?id=e-VIDwAAQBAJ&source=productsearch&utm_source=HA_Desktop_US&utm_medium=SEM&utm_campaign=PLA&pcampaignid=MKTAD0930BO1&gclid=Cj0KCQjwnqzWBRC_ARIsABSMVTP1TTfOxPlob1Ob0gwH5f7vx6K9AQXlJkEYbQTgb2uwgMur9AsiY0EaAnLfEALw_wcB&gclsrc=aw.ds&dclid=CLTcs6fvrtoCFYUcPwodVJ4Ktw) on this topic.

Some things to keep in mind here:
- the name of the test library must contain the word "Tests" in the name of `.proj` file so that the automation software can pick it up.
- I used a template for Web Api for ASP.NET Core.  When I deployed it for the first time, the automation software complained that I attempted to deploy a web app, but that it could not recognize it was a web app because it was missing the Web.Config file.  I'm sure there is a 'trick' to fix this, but then again, the goal of this experience was to see how we can get from source to CI/CD pipeline automation with the most out-of-the-box (little tweaking) as possible.

After those 2 things were corrected (a couple of attempts later), the [endpoint was ready](https://tweetcacheapi.azurewebsites.net/api/twusers).

