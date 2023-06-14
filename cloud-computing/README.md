- [🚧 Work In Progress (14JUN2023)](#-work-in-progress-14jun2023)
- [Cloud Computing](#cloud-computing)
- [Links](#links)
- [Cloud Services](#cloud-services)
  - [IaaS: Infrastructure as a Service](#iaas-infrastructure-as-a-service)
  - [PaaS: Platform as a Service](#paas-platform-as-a-service)
  - [SaaS: Software as a Service](#saas-software-as-a-service)
  - [Serverless](#serverless)
- [My Devops Stack](#my-devops-stack)
  - [How did it come to this?](#how-did-it-come-to-this)
  - [Dokku](#dokku)

# 🚧 Work In Progress (14JUN2023)

# Cloud Computing

There is no cloud. It's just someone else's computer. What is the cloud? It's the internet.

Specifically, "the cloud" is a marketing phrase implying access to vast datacenter resources around the globe, scaling your code based on physical location and demand.

# Links

| Page Title                                                                                    | Author      | Description                                                        |
| --------------------------------------------------------------------------------------------- | ----------- | ------------------------------------------------------------------ |
| [Deploy React and Express to Heroku](https://daveceddia.com/deploy-react-express-app-heroku/) | Dave Ceddia | `backend API` _and_ `frontend client` on Heroku (the "simple" way) |

# Cloud Services

There are four types of cloud services:

## IaaS: Infrastructure as a Service

Infrastructure: Usually has to do with replacing physical hardware.

- [Infrastructure as a Service (IaaS)](./IaaS.md)
  - Caching
  - Legacy
  - File
  - Networking
  - Technical
  - Security
  - System Management

## PaaS: Platform as a Service

> ⓘ This is the cloud service that is required by _The Odin Project_

Platform: A service Used to build applications. (Development / Web development)

- [Platform as a Service (PaaS)](./PaaS.md)
  - Application Development
  - Decision Support
  - Web
  - Streaming

## SaaS: Software as a Service

Software: This service is what you use probably everyday. For example Google Mail, Dropbox, Office 365. Nothing can be changed with this service , the users receive access to the software, and that’s it. Also, there is usually a “subscription fee” to use this type of service.

- [Software as a Service (SaaS)](./SaaS.md)
  - Email
  - Customer Relationship Management (CRM)
  - Collaborative / Team
  - Enterprise Resource Planning (ERP)

## Serverless

- [Serverless](./Serverless.md)

# My Devops Stack

- esxi
  - pfsense
    - dns resolving: primary for local domain
  - pihole
    - dns resolving: secondary for blocking
  - dokku

## How did it come to this?

At the time of this writing, June 9, 2003, The Odin Project is recommending that students use Heroku. I'm fine paying for that service. That service would cost me less than the electricity it costs me to run my own servers.

_But_ there are a few things that _made_ me uncomfortable with that:

1. Vendor Lock-in
2. Not knowing what is going on behind the scenes
3. Writing someone (basically) a blank check

Without having used them, it seems that Heroku is a great service.

Vendor lock-in seems non-existent, other than configuration.

I understand a whole lot better after spending some time with docker, docker compose, and dokku.

## Dokku

Dokku is an open-source self-hosted version of the PaaS, Heroku. I really like the idea of pushing my project (git) to my dokku server, having the dokku server rebuilt everything, shut down old docker containers, and deploy the new ones.
