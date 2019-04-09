---
title: "Configure Azure Web App for Local Git Repository Deployment"
date: 2019-04-09 15:37:00
excerpt_separator: "<!--more-->"
tags: [azure,webapp,git]
categories: [Azure]
typora-copy-images-to: ..\assets\blog
typora-root-url: ..
---

There are multiple Azure Web App deployment options. I am going to show you how to configure your Web App to use local git repository.

<!--more-->

For this tutorial you need an existing Azure Web App. You can create one, following Step 2 from the [Create Hello World WebApp in Python]({{ site.baseurl }}{% post_url 2019-04-09-create-hello-world-azure-webapp-pyhon %}) tutorial.

## Step 1: (Optional) Disconnect Active Web App Deployment

If you haven't configured deployment for your Web App, skip this step.

1. Open your Web App:
   1. Enter the name of your Web App in the search box at the top of the Azure Portal
   2. Select the App Service result to open your Web App
2. Scroll down to the `Deployment` section and select `Deployment Center`
3. Click `Disconnect`

It takes a minute or two to disconnect your Web App from the deployment. Once it is complete, you can proceed with Step 2. 

## Step 2: Configure Local Git for Web App Deployment

In this step we will configure the Web App to use local Git for deployment.

1. Open your Web App:
   1. Enter the name of your Web App in the search box at the top of the Azure Portal
   2. Select the App Service result to open your Web App
2. Scroll down to the `Deployment` section and select `Deployment Center`
3. Select `Local Git` for source control and click `Continue`
4. Select a build provider. I am going to use `Kapp Service Kudu build server` and click `Continue`
5. Review the deployment definition and click `Finish` to setup the deployment

Once the deployment set up is complete, you can see the `Git Clone Url`  in the `Deployment Center`. To be able to deploy from Git you need to setup deployment credentials.

## Step 3: Setup Deployment Credentials

1. From the `Deployment Center` of your Web App select `Deployment Credentials`
2. Select the `User Credentials` tab.
3. Enter `Username` and `Password`
4. Save the credentials

## Step 4: Clone the Web App Git Repository

1. Go to the `Deployment Center` of your Web App and copy the `Git Clone Url`
   The Url is in format: `https://<web-app-name>.scm.azurewebsites.net:443/<web-app-name>.git`

2. Clone the repository, using the Url you copied:

   ```
   $ git clone https://webjade.scm.azurewebsites.net:443/webjade.git
   ```

3. When asked for credentials, enter the credentials you configured in Step 3.

## Developing Your Web App

You can modify and test your Web App locally. When ready, you can push it to the Azure App Service.

Building on the example from the [Create Hello World WebApp in Python]({{ site.baseurl }}{% post_url 2019-04-09-create-hello-world-azure-webapp-pyhon %}) tutorial, you could modify the `application.py` file:

```python
from flask import Flask
app = Flask(__name__)

@app.route("/")
def hello():
    return "Long time ago in a cloud far, far away..."
```

Once changes are complete and saved, you can push them to the Azure App Service:

``` bash
$ git add .
$ git commit -m "New welcome message"
$ git push -u origin master
```

You might be asked to provide the deployment credentials. After that you will get rather verbose output showing full log on the deployment activities.

```
Username for 'https://webjade.scm.azurewebsites.net:443': <your-deployment-username>
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 8 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 368 bytes | 368.00 KiB/s, done.
Total 3 (delta 1), reused 0 (delta 0)
remote: Deploy Async
remote: Updating branch 'master'.
remote: Updating submodules.
remote: Preparing deployment for commit id 'f73d4c87f7'.
remote: Oryx-Build: Running kudu sync...
remote: Kudu sync from: '/home/site/wwwroot' to: '/home/site/wwwroot'
remote: Running oryx build...
remote: Build Operation ID : |csLOYh6lj1o=.c54b9b69_
remote: Oryx Version       : 0.2.unspecified, Commit: unspecified
remote: Repository Commit  : f73d4c87f7809389d232781c49f62c7dadb1b2f7
remote:
remote:
remote: Source directory     : /home/site/wwwroot
remote: Destination directory: /home/site/wwwroot
remote:
remote: Python Version: /opt/python/3.7.2/bin/python3
remote: Python Virtual Environment: antenv
remote: Creating virtual environment ...
remote: ..
remote: Activating virtual environment ...
remote: ..
remote: Requirement already up-to-date: pip in ./antenv/lib/python3.7/site-packages (19.0.3)
remote: ..
remote: [19:09:47+0000] Requirement already satisfied: click==6.7 in ./antenv/lib/python3.7/site-packages (from -r requirements.txt (line 1)) (6.7)
remote: [19:09:47+0000] Requirement already satisfied: Flask==1.0.2 in ./antenv/lib/python3.7/site-packages (from -r requirements.txt (line 2)) (1.0.2)
remote: [19:09:47+0000] Requirement already satisfied: itsdangerous==0.24 in ./antenv/lib/python3.7/site-packages (from -r requirements.txt (line 3)) (0.24)
remote: [19:09:47+0000] Requirement already satisfied: Jinja2==2.10 in ./antenv/lib/python3.7/site-packages (from -r requirements.txt (line 4)) (2.10)
remote: [19:09:47+0000] Requirement already satisfied: MarkupSafe==1.0 in ./antenv/lib/python3.7/site-packages (from -r requirements.txt (line 5)) (1.0)
remote: [19:09:47+0000] Requirement already satisfied: Werkzeug==0.14.1 in ./antenv/lib/python3.7/site-packages (from -r requirements.txt (line 6)) (0.14.1)
remote: Done running pip install.
remote:
remote:
remote: Done.
remote:
remote: Running post deployment command(s)...
remote: Deployment successful.
remote: App container will begin restart within 10 seconds.
To https://webjade.scm.azurewebsites.net:443/webjade.git
   c91a424..f73d4c8  master -> master
Branch 'master' set up to track remote branch 'master' from 'origin'.

```

## Tips

### Credentials in Windows

If you are using Windows, credentials are stored in `Credential Manager`. If you modify the Deployment Credentials, you will start getting authorization failures. To fix this, open the Windows `Credential Manager` and find the Git credentials in the Windows Credentials tab. Remove or modify the credentials as appropriate.

### Testing Python Flask Web App Locally

You first need to install the requirements.

```bash
$ pip install -r requirements.txt
```

Than you start the flask development server:

```bash
$ export FLASK_APP=application.py
$ flask run
```

```
 * Serving Flask app "application.py"
 * Environment: production
   WARNING: Do not use the development server in a production environment.
   Use a production WSGI server instead.
 * Debug mode: off
 * Running on http://127.0.0.1:5000/ (Press CTRL+C to quit)
```

Open a web browser and navigate to `http://127.0.0.1:5000` where you can see your Web App executed by local Flask server.

To stop the server, hit `Ctrl-C`.

I would suggest that you do not install requirements globally, but use Python virtual environments when developing applications in Python. See [Virtual Environments and Packages](https://docs.python.org/3/tutorial/venv.html) Python documentation for more information. This will also give you the opportunity to keep updated your `requirements.txt` file.

## Resources

* [Create a PHP web app in Azure](https://docs.microsoft.com/en-us/azure/app-service/app-service-web-get-started-php)
  Official Azure tutorial on creating PHP app in Azure, using Azure CLI and local Git
* Python [Virtual Environments and Packages](https://docs.python.org/3/tutorial/venv.html)

