# Configuring SAP AI Core and SAP AI Launchpad

![rw-book-cover](https://eu-images.contentstack.com/v3/assets/blt4e79a2501da5d16b/bltd2a626e2a2f8c0d6/66868d652deff133695292dd/SAP-Learning-Socials_comprimida.png)

## Metadata
- Author: [[sap.com]]
- Full Title: Configuring SAP AI Core and SAP AI Launchpad
- Category: #articles
- Summary: After completing this lesson, you will be able to:Illustrate the process involved in working with SAP AI Core and SAP AI LaunchpadConnect SAP AI Core and S
- URL: https://learning.sap.com/learning-journeys/learning-how-to-use-the-sap-ai-core-service-on-sap-business-technology-platform/configuring-sap-ai-core-and-sap-ai-launchpad_a51c5214-d9ab-4f22-bc81-b683d09697fc

## Full Document
Objectives

After completing this lesson, you will be able to:

* Illustrate the process involved in working with SAP AI Core and SAP AI Launchpad
* Connect SAP AI Core and SAP AI Launchpad to user's docker and GitHub repositories

#### SAP AI Core

##### What is the added value of SAP AI Core?

Note

This learning journey just focuses on SAP AI core.

Refer to the learning journey [Solving Your Business Problems Using Prompts and LLMs in SAP's Generative AI Hub](https://learning.sap.com/learning-journeys/solving-your-business-problems-using-prompts-and-llms-in-sap-s-generative-ai-hub) to use SAP's generative AI Hub to solve your business problems using LLMs, SAP AI Launchpad, and generative-ai-hub SDK.

You will also be able to apply techniques for refining and evaluating prompts using different large language models in generative AI hub.

* Gain peace of mind with SAP managed deploymentsWith SAP AI Core, customers gain peace of mind as they benefit from a complete service that packages all dependencies and hides the complexity of building your own training and serving productive environment. Instead, SAP AI Core exposes simple API endpoints to embed AI into your business applications.
* Quickly embed AI in SAP applications and business processesCustomers can take advantage of the standardized integration into SAP applications to quickly build and integrate their AI use cases into their business applications.
* Strike the right balance between costs and performanceOn the one hand, customers benefit from accelerated performance with GPU support to run their most resource-hungry use cases at scale. On the other hand, customers run efficiently while keeping control of their costs by leveraging built-in autoscaling and scale-to-zero as well as by choosing from a broad range of storage, CPU, and GPU service plans.

SAP AI Core uses Kubernetes clusters which provide proven features for running container-based applications for training and serving AI models. Such a cluster can provide different resources according to the current requirements. E.g., GPU nodes for heavy duty AI models or running complex ML AI pipelines that require different resources per step. The Kubernetes infrastructure is very fast and flexible (scale up / down the containers which run the AI code).
* Model once and serve multiple customersCustomers benefit from simplified training and inferencing with reusable templates and can deliver model templates for their customers or internal teams, to train the model on their own data.

![Operationalize AI with SAP AI Core i.e., integrate AI into SAP and custom applications using AI API. Data can be extracted from SAP HANA Cloud, External Cloud or On-Premise Storage.](https://learning.sap.com/service/media/topic/eae25e9e-7e02-496b-bde1-42e5127f5067/AICO01_12_en-US_media/AICO01_12_en-US_images/OperationalizeAI.png)
To realize those added values, SAP AI Core and SAP AI Launchpad offer enterprise-grade features to productize and operate your AI models. The main capabilities that SAP AI Core provides are the orchestration of AI workflows, such as model trainings and batch inference, as well as serving model inference, so that models can make predictions.

To ease the shipment of new AI scenarios, the service offers continuous delivery capabilities and ensures tenant isolation with multi-tenancy. To safeguard your costs and to scale on demand, you only pay for the resources you used but can tap into scalability and increased performance powered by GPUs.

All of the functionality comes out of the box and is managed for you while retaining openness to any AI framework so that you can ship your AI scenario easily.

To connect to your business applications as well as to operate your AI scenarios in AI Launchpad, SAP AI Core provides the standardized AI interface, AI API, which provides a common framework for consuming and operating your AI scenarios.

During development your AI scenarios, you are supported with development tooling, such as the SAP AI Core SDK, and full flexibility in the choice of storage for your data and models.

The process of building a new AI scenario on SAP AI Core involves the following steps: an initial configuration, the model training, and the inferencing. Below is the end-to-end ML Workflow in SAP AI Core, which shows the various sub-steps in each of these steps. Later on, we will start with the onboarding and initial configuration of your instance of SAP AI Core and SAP AI Launchpad.

![Description of the end-to-end ML workflow in SAP AI Core: Onboarding, Data Upload, Training, Model Deployment, Model Serving (Inference) via Rest endpoint.](https://learning.sap.com/service/media/topic/eae25e9e-7e02-496b-bde1-42e5127f5067/AICO01_12_en-US_media/AICO01_12_en-US_images/E2E_ML_Workflow.png)
#### SAP AI Launchpad

SAP AI Launchpad is a service on SAP Business Technology Platform (SAP BTP) to transparently manage AI models across the enterprise. Connect to AI API-enabled runtimes, including SAP AI Core, and centralize AI lifecycle management for your AI scenarios with a convenient user interface. The application acts as the single access point for all AI content across your SAP landscape. From an MLOps perspective, SAP AI Launchpad provides customers with the capabilities to capture and analyze metrics that has been created by supported AI runtimes - for example, SAP AI Core.

Users can compare and visualize those metrics. The integration between SAP AI Launchpad and supported AI runtimes is facilitated by a standardized interface called "AI API". Furthermore, the application is focusing on supporting the full lifecycle management and operations of AI processes by providing a holistic view of all metrics, artifacts etc. made available through the integrated AI runtimes and let you analyze and evaluate critical productive AI KPIs. Customers can also productize existing training models of supported AI runtimes or trigger jobs and deploy models directly using SAP AI Launchpad.

![Description of SAP AI Launchpad, which is a web application for operating and monitoring the SAP AI Core platform as well as other Cloud AI platforms.](https://learning.sap.com/service/media/topic/e6bbf682-6591-4438-8000-cda5504c6ebd/AICO01_12_en-US_media/AICO01_12_en-US_images/SAP%20AI%20Launchpad.png)
##### What is the added value of SAP AI Launchpad?

* Centralize AI lifecycle managementWith SAP AI Launchpad, customers can connect to all AI API-enabled services and streamline the AI lifecycle management of their AI scenarios SAP AI Launchpad. Benefit from uniform model status as well as uniform training and deployment, regardless of the underlying technology. As such, SAP AI Launchpad will not only increase transparency but will also enable to drive innovation by re-using AI content.
* Monitor and continuously improve model performanceCustomers benefit from simplified model retraining to continuously improve their model performance. They can also productize existing training models of supported AI runtimes or trigger jobs and deploy models directly using SAP AI Launchpad. The different resource groups (tenant) are displayed in SAP AI Launchpad.

#### AI Core Configuration

Watch the following video to learn about AI Core Configuration.

##### Resource Groups

The SAP tenant concept provides a separation of data and workspaces of customers in an SAP system.

As SAP AI Core is based on a Kubernetes cluster, the technical separation is achieved by using Kubernetes Resource Groups. You can create resource groups to isolate ML workloads, for example, to separate users/ tenants.

There are 2 use cases:

* An SAP LOB provides embedded AI for different customers: The LOB is administrating the BTP tenant for SAP AI Core. In order to make sure that customer data and AI assets like models and trainings workflows are safe/secured, each "subtenant" i.e. customer is managed in AI Core using a separate resource group.
* A customer is using SAP AI Core directly: As the customer is using his own BTP Organisation (i.e. Tenant), data and AI assets are safe and cannot be accessed by other customers. The Customer can still use resource groups to separate data and AI assets for different departments by assigning a resource group for each department of the company.

<https://help.sap.com/docs/AI_CORE/2d6c5984063c40a59eda62f4a9135bee/8aae6cbe2c0e4290954b8f61b4b355b7.html?locale=en-US>

#### Connect Tools and Manage Your Credentials

Creating secrets for your tools means that you can connect external programs and tools without compromising your account. The tools can be used to incorporate version control, cloud storage, and portable containers.

Using SAP AI Core alongside external tools such as GitHub, Docker, and Amazon Web Services S3 storage leverages the benefits of version control, containerization and cloud storage. As a result, your content is made available remotely, where you have a stable internet connection.

This section is a one-time procedure. It is a dev ops based configuration that connects these tools to your SAP AI Core. You may repeat the steps, if necessary - for example, to remove or replace access to an external tool.

##### Prerequisites

##### Steps

1. Manage your Git Repository.

You can use your own Git repository to version control your SAP AI Core templates. The GitOps onboarding to SAP AI Core instances involves setting up your Git repository and synchronizing your content.

	1. [Managing Your Git Repository | SAP Help Portal](https://help.sap.com/docs/AI_CORE/2d6c5984063c40a59eda62f4a9135bee/2cd299632c194b44bf25b4726217fbb9.html)
2. Manage Resource Groups.

A resource group represents a unique workspace environment where users can create or add entities such as configurations, executions, deployments, and artifacts.

	1. [Managing Resource Groups | SAP Help Portal](https://help.sap.com/docs/AI_CORE/2d6c5984063c40a59eda62f4a9135bee/8aae6cbe2c0e4290954b8f61b4b355b7.html)
3. Manage your Object Store Credentials.

Connect SAP AI Core to a cloud object store and manage access using an object store secret. The connected storage is used as storage for your dataset, models, and other cache files of the Metaflow Library for SAP AI Core.

	1. [Managing Your Object Store Credentials | SAP Help Portal](https://help.sap.com/docs/AI_CORE/2d6c5984063c40a59eda62f4a9135bee/f10b532ebd154d87ae706aeb2d9f9d13.html)
4. Manage docker credentials.

Docker facilitates the packaging and running of an application in a remote container. Connect SAP AI Core to a Docker repository and manage access using a Docker registry secret.

	1. [Managing Docker Credentials | SAP Help Portal](https://help.sap.com/docs/AI_CORE/2d6c5984063c40a59eda62f4a9135bee/c5445c4ab4e24d0c854c9b61c1076a51.html)
