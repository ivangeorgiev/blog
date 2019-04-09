---
title: "Create Hello World WebApp in Python"
date: 2019-04-09
excerpt_separator: "<!--more-->"
tags: [azure,webapp,python,'hello-world']
categories: [Azure,Python]
typora-copy-images-to: ..\assets\blog
typora-root-url: ..
---

In this post we are going to create a "Hello world" Azure WebApp in Python. We are going to use GitHub for source control.

<!--more-->

## Step 1: Create GitHub Repository for the WebApp

There are multiple ways to get started with your WebApp GitHub repository. For example:

* Fork an existing GitHub repository
* Create an empty GitHub repository

To  make things simple we are going to fork an existing GitHub repository. Open Azure sample's [python-docs-hello-world](https://github.com/Azure-Samples/python-docs-hello-world) repository and click the `Fork` button at the top right. This will create a copy of the current repository into your GitHub account. The new repository has the same name `python-docs-hello-world`.

## Step 2: Create Azure WebApp

Creating a new WebApp is actually very easy operation. It requires just to provide a few pieces of information. Here is how to do it: 

1. Go to Azure Portal and click "Create a resource"
2. In the "New" blade type `web app` to search the Azure Marketplace.
3. From the search results select `Web App` than click `Create`
4. Give your WebApp a name. The name must be globally unique as it will be accessed as `<webapp-name>.azurewebsites.net`. I will name my WebApp **webjade**
5. Select a subscription, e.g. `Free Trial`
6. Select existing resource group or define new to be created. I am creating a new resource group `webjade`
7. Select `Linux` as *OS* and `Code` for *Publish*.
8. You can leave the default Service Plan selection or create a new Service Plan. I am creating a new service plan, as I do not like the default region:
   * Name: `webjade`
   * Location: `West Europe`
   * Pricing tier: `B1`
9. Select `Runtime Stack` to be `Python 3.7`.
10. Click `Create` to create the WebApp.

Clicking the `Create` button will deploy the new Web App. The deployment takes a few seconds. Once it is complete you will see a notification. You can click `Go to resource`  from the notification, but I prefer that you follow another path.

At the top of Azure Portal there is a search box. Type the name of your WebApp in the search box. The name of my Web App is `webjade`. 

Select the `App Service` result. This will bring you to the new WebApp you created. This will open your Web App resource.

In the Overview section you will find the URL of your web app. You can click it to see the default page for your Web App. When I open `<https://webjade.azurewebsites.net/>` in my web browser, I see following:

![1554815236151]({{ site.baseurl }}/assets/blog/azwebapp-python-default-site.png){: width="700px"}

Congratulations! You already have a Web App created and deployed. 

Now let's connect our web app with GitHub repository so that we can easily deploy changes.

## Step 3: Configure WebApp Deployment from GitHub

1. Open your WebApp resource:
   * In Azure Portal, type the in the search box at the top the name of your WebApp resource
   * Click the `App Service`  result with the name of your WebApp.
2. Go to the `Deployment` section of the WebApp resource and select `Deployment Center`.
3. In the `Deployment Center` select GitHub as source control.
   * If you haven authorized `Azure App Service` before to access your GitHub account, a popup will be shown to confirm authorization
   * Grant permission to your GitHub account
4. Click `Continue` at the bottom.
5. Select a build provider. For this tutorial we are going to use `Kapp Service Kudu build server` and click `Continue`
6. The next step `Configure`:
   1. Select your GitHub profile from the `Organization` drop-down.
   2. Select the `python-docs-hello-world` repository from the `Repository` drop-down.
   3. Select `master` from the `Branch` drop-down.
7. Click `Continue`
8. Review the summary and click `Finish`

The deployment will take place immediately. It might take a minute or two to deploy your Web App. You can see navigate your web browser to your WebApp url. It should look like this:

![1554816362434]({{ site.baseurl }}/assets/blog/azwebapp-python-hello-world.png){: width="400px"}

Great job! Now you have your WebApp set up and running, ready for your new ideas.

Before we continue, one note. We configured the Kapp Service to deploy from the `master` branch of your GitHub repository. This means that each time when your GitHub `master` branch is updated, the application will be automatically updated. This might not be optimal for production purposes. You might use, for example [GitFlow](https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow) (or [this article](https://datasift.github.io/gitflow/IntroducingGitFlow.html)) and connect multiple webapps to various branches so that you have environment for development, testing etc.

## Developing Your Python WebApp

Now I will show you how you can develop your WebApp.

1. Open the GitHub repository you created for the WebApp. When you open the WebApp it says `Hello World!`. We are going to change it so that it says `Hello Ivan!`.

2. Select the `application.py` file. It is very simple and has just a few lines:

   ```python
   from flask import Flask
   app = Flask(__name__)
   
   @app.route("/")
   def hello():
       return "Hello World!"
   ```

3. Click `Edit File` and modify the last line so that it looks like:

   ```python
   return "Hello Ivan!"
   ```

4. Commit the changes directly to `master` (leaving all to defaults).

This will trigger deployment of the application. Once the deployment is complete, you could see the result in your browser:

![1554816362434]({{ site.baseurl }}/assets/blog/azwebapp-python-hello-ivan.png){: width="400px"}

In this tutorial I showed you:

* how to create Python WebApp, running on Linux, using Azure Portal
* connect your WebApp deployment to GitHub
* develop your WebApp by modifying code in GitHub

The development approach I showed you is just for demo purposes. I would not suggest you modifying files directly in GitHub and committing to `master` branch directly. The process of developing WebApp (the Software Development Lifecyle - SDLC) is a very broad and interesting topic on itself and goes far beyond the goal of this tutorial.

## Resources

* [Create a Python app in Azure App Service on Linux](https://docs.microsoft.com/en-us/azure/app-service/containers/quickstart-python)
  Official Azure tutorial on creating Python app in Azure, using Azure CLI
* [Gitflow Workflow](https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow) Tutorial from Atlassian
* [Introducing GitFlow](https://datasift.github.io/gitflow/IntroducingGitFlow.html)

