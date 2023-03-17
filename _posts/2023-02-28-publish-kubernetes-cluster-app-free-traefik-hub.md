---
title: "How to publish a Kubernetes application for free with Traefik Hub"
description: "Learn how to quickly publish your cluster application for free with Traefik Hub"
author: marcia
date: 2023-02-28 17:45:00 +0100
categories: [Tutorial]
tags: [web dev, docker, kubernetes, traefik]
video: 'https://www.youtube.com/embed/toWxWTw2tEY'
video-alt: 'Watch the video walk-through'
---

# How to publish a Kubernetes application for free with Traefik Hub

It can be hard to find a provider to publish Kubernetes applications
to the internet for free without a trial period.

Sometimes you just want to test a new app or just run a personal application
but you can't get them live in a production environment because you can't
find a service to publish them for free.

That's how [Traefik Hub](https://traefik.io/traefik-hub/) can help you, among
with other nice features that come along.

With Traefik Hub:

- You can publish one application for free. No trial. No credit card required.
- It's fast. Run a couple of commands to install an agent in your cluster and you're done.
- You can create an access control policy to grant access to your app only to authorized users.
- You can add your custom domain for your app.
- You get a few metrics to monitor your app.

## Requirements

For this tutorial, we assume you've gone through the process explained on the
previous [video](https://www.youtube.com/watch?v=JaTITCVcUn0) and
[blog post](../traefik-proxy-with-proxy-wizard/). During the described process we:

1. Created a Kubernetes cluster running on Docker.
1. Launched Traefik Proxy on the cluster.
1. Deployed a sample `Hello-world` containerized application to the cluster.

The next step and goal of this post is to publish this application to the internet. To do so,
watch the video on top of this page and/or follow the steps below.

## Create a new Traefik Hub Agent

1. On your computer, open the terminal and the browser side-by-side to make this process easier.
1. On the terminal, go to your cluster's directory and ensure the cluster is up and running.
1. On your browser, sign into your [Traefik Hub](https://hub.traefik.io/) account.
1. To create a new agent, click **Install my first Traefik Hub Agent**.
1. Select the orquestrator (or platform). In our case, it's **Kubernetes**.
1. Copy each command from Traefik Hub and run on your terminal. It uses Helm to install the agent in your cluster.
1. Copy the agent's token and store it somewhere safe. You may need it later and you cannot recover it.
1. Click **Configuration Done** to finish the process.
1. Give a name to your agent, for example, `my-agent-wizard`.

The agent is installed in your cluster and connected to Traefik Hub.

> Note: with the Traefik Hub free account you can create only one agent.
{: .prompt-info }

## Publish your application

To expose your application to the internet:

1. On Traefik Hub, from the left navigation, click **Dashboard**.
1. From the panel **Services**, select the service you'd like to publish. In our example, it's the `Hello-world` app registered with the `my-agent-wizard` agent.
1. Click **Publish**.
1. Select the port you'd like to use. In our example, it's the port 80 (set during the application deployment).
1. Click **Save and Publish**.

Traefik Hub publishes your application. Within a minute or so, the URL to your app is shown.
After a few minutes, you can monitor your application from the same screen.

## Configure access control

If you'd like to restrict access to your application, you can configure
access control.

### Choose the authentication method

Traefik Hub offers three authentication methods:

- Basic Auth: authorize users with usernames and passwords.
- JWT: authenticate users with a JWT token.
- OIDC: uses OpenID authentication (not available for free accounts).

### How to configure access control

1. On Traefik Hub, from the left navigation, click **Access Control**.
1. Click **Create a Policy**.
1. Create a name for the policy.
1. Select the agent.
1. Select the authentication method.
1. Fill in the authentication data according to the method of your choice.

> Note: With the Traefik Hub free account you can create only one policy.
{: .prompt-info }

### Attribute the authentication policy to the published application

The authentication is not attributed to your app automatically, you must do so manually.
To attribute the authentication policy you created to the published application:

1. On Traefik Hub, from the left navigation, click **Services**.
1. Select the service corresponding to your application.
1. Under the **Published Services** tab, you can see the the port you published your app.
1. On the right side of the port, click **Add Access Control**.
1. From the **Select an ACP** dropdown menu, select the name of the policy you created before.

Traefik Hub republishes your app with the corresponding authorization policy.

### Remove access control

If you'd like to drop the access control and make your application publicly available:

1. On Traefik Hub, from the left navigation, click **Services**.
1. Select the service corresponding to your application.
1. From the **Published Services** tab, on the right side of the port, you can see the access control policy attributed to your application in the format **ACP: `policy-name`**.
1. Hover over **ACP: `policy-name`** to reveal a trash can. Click it to remove the policy from the app.

Traefik Hub republishes your app without the authorization policy.
