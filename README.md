
> 💡 **Note:** This repository was created to support the students from the AI classes I teach.

## Objective

```
Run n8n locally in the simplest possible way avoiding as much as possible installing unnecesary things on your Operating System.
```

# Table of Contents

* [Prerequisites](#prerequisites)
* [Runnint (step-by-step)](#running-step-by-step)
    * [Start the application](#start-the-application)
    * [Stop the application](#stop-the-application)
    * [Troubleshooting](#troubleshooting)
    * [Extra](#extra)
    * [Reference](#reference)
* [n8n: Initial Setup](#n8n-initial-setup)
    * [Setup Account](#setup-account)
    * [Questionaire](#questionaire)
    * [Activation Key (Advanced Features)](#activation-key-advanced-features)
* [n8n: First Workflow](#n8n-first-workflow)
    * [Start from Scratch](#start-from-scratch)
    * [Start from a Template](#start-from-a-template)
        * [Choosing the Template](#choosing-the-template)
        * [Loading the Template](#loading-the-template)
        * [Configuring the Workflow](#configuring-the-workflow)
        * [Customizing the Workflow](#customizing-the-workflow)
    * [Run the Workflow](#run-the-workflow)
* [n8n: Troubleshooting](#n8n-troubleshooting)

# Prerequisites

1) Install [Git](https://git-scm.com/downloads)
* Run the instructions on your TERMINAL
* Note on MAC: You might need to install brew first ([instructions](https://brew.sh/))

2) Install [Docker Desktop](https://www.docker.com/)
* Note on Windows: It requires to restart after installing

# Running (Step-by-step)

## Start the application

From your TERMINAL, run the following commands:

1) Download this repositoty
```
git clone https://github.com/rafaelspecta/n8n.git
```
The n8n directory will be created 

2) Enter n8n directory, because every "docker" command must run in that directory
```
cd n8n
```

3) Run the containers (PostgreSQL and n8n appication)
```
docker compose up -d
```

4) Acess n8n on your browser with the following URL
```
http://localhost:5678
```

## Stop the application

When you stop working on it, just stop the containers
```
docker compose stop
```

## Troubleshooting

If you face problems, the logs might be helpful. To check them run
```
docker compose logs -f
```

## Extra

The default name of the database, user and password for PostgreSQL can be changed in the [`.env`](.env) file in the current directory.

## Reference

Based on https://github.com/n8n-io/n8n-hosting/tree/main/docker-compose/withPostgres

# n8n: Initial Setup

## Setup Account

Fill your information for setting up your account

<img src="n8n-screenshots/01-setup-account.png" width="300" />

## Questionaire

You can skip this if you want by leving it blank and clicking on "Get Started". Although this is a useful information that helps the n8n team.

<img src="n8n-screenshots/02-questionaire.png" width="300" />

## Activation Key (Advanced Features)

You can get the activation key for FREE to have access to paid features just by providing you email.

If you filled your email just hit "Send me a free license key".

<img src="n8n-screenshots/03-activation-key.png" width="400" />

# n8n: First Workflow

You can
* Start from Scratch
* Start from a Template

## Start from Scratch

Just hit "Start from scratch" and you will enter a blank canvas

<img src="n8n-screenshots/10-start-from-scratch.png" width="400" />

## Start from a Template

### Choosing the Template

1) Look for the option "Teamplates" on the side menu.

<img src="n8n-screenshots/20-templates-menu-option.png" width="250" />

2) That will take you to page on n8n's website with a huge list of options to choose from

<img src="n8n-screenshots/21-templates-page.png" width="500" />

3) On the search bar you can look for a specific keyword, such as "email"

<img src="n8n-screenshots/22-search-keyword.png" width="500" />

Or you can look for a specific tool, such as "Gmail"

<img src="n8n-screenshots/23-search-tool.png" width="500" />

4) Choose the template you want to use anc click on it. For example bellow I clicked on "Gmail AI Email Manager"

<img src="n8n-screenshots/24-selected-template.png" width="500" />

### Loading the Template

Once you have chosen the template (see [Choosing the Template](#choosing-the-template)) now we want to load it in our n8n.

1) Now click on "Use for free" and the follwing will appear

<img src="n8n-screenshots/25-use-for-free.png" width="500" />


2) Now click on "Copy template to clipboard (JSON)"

That will copy the content workflow description file that has all the information needed for this workflow.

3) Now you have to create local empty file (with the extension ".json") and PASTE this content to it. So create the file, open it and hit "Paste" on the menu, or hit Ctrl+V (Windows) or Cmd+V (Mac)

In this case, to facilitate, I have already created the file "gmail-manager.json" for you under the directory n8n/sample-template/"

4) So now lets load this file into our n8n running locally, but going back to our n8n application
```
http://localhost:5678
```

5) Click on "Start from scratch" to open a new canvas

<img src="n8n-screenshots/10-start-from-scratch.png" width="400" />

6) Now find on the top menu the 3 dots menu option, and click on it

<img src="n8n-screenshots/26-three-dots-menu.png" width="400" />

7) Click on "Import from File..."

<img src="n8n-screenshots/27-import-from-file.png" width="400" />

8) Select the file at `n8n/sample-template/gmail-manager.json`

9) After selecting the file you will see somthing like this:

<img src="n8n-screenshots/28-sample-workflow.png" width="600" />

### Configuring the Workflow

Bassically all templates come with Nodes that require credentials, so you will need to configure it.

You can identify the nodes that require configuring by the following symbol on the node

<img src="n8n-screenshots/30-needs-configurin-symbol.png" width="100" />

I this example we need to configure:
* Gmail Account Credentials
* Anthropic Credentials

<img src="n8n-screenshots/31-needs-configuring.png" width="600" />

To configure double-click on the symbol and you will ths config panel bellow where you need to click on the drop-down arrow in "Credential do connect with", followed by "Create new credential"

<img src="n8n-screenshots/32-configuration-panel.png" width="300" />

Each tool have its own configuration and you will have to click on "Open docs" to learn how to do it

<img src="n8n-screenshots/33-gmail-credentials.png" width="600" />

You will have to follow the same steps for other Nodes that require configuration (in this case Anthropic). For nodes of the same type you can just select the credential you have created in the first one (in this case you need to create Gmail credentials only one and you can reuse it in the other Gmail-related nodes)

### Customizing the Workflow

In the Gmail Manager example you might want to customize it by switching the `Anthropic Chat Model` for `OpenAI Chat Model`.

Click on the `+` button on the top-right part of the canvas and type `OpenAI`. You will see the option `OpenAI Chat Model`

<img src="n8n-screenshots/40-select-openai-chat-model.png" width="300" />

Drag the `OpenAI Chat Model` into your canvas

Now you can select and erase `Anthropic Chat Model` and link the new `OpenAI Chat Model` node to your Agent's `Chat Model` like this:

<img src="n8n-screenshots/41-connect-openai-chat-model.png" width="300" />

> 💡 **Note:** Don't forget to configure `OpenAI Chat Model` with your OpenAI Key

## Run the Workflow

Once there is no more pending configuration you can click on "Execute Workflow"

<img src="n8n-screenshots/50-execute-workflow.png" width="200" />

# n8n: Troubleshooting

If the Workflow is not working as expected you can check the logs.

Click on the arrow bellow that you will find in the bottom-right corner of the screen

<img src="n8n-screenshots/60-acessing-logs.png" width="100" />

It will open the following panel that shows each step executed, where it stopped and what was the error

<img src="n8n-screenshots/61-log-missing-credentials.png" width="800" />

In this case the credentials for Gmail are missing

