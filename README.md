# A Developer's Guide to Building Resilient Cloud Applications with Azure

<a href="https://www.packtpub.com/product/a-developers-guide-to-building-resilient-cloud-applications-with-azure/9781804611715"><img src="https://m.media-amazon.com/images/I/51UO3RWHMxL.jpg" alt="Book Name" height="256px" align="right"></a>

This is the code repository for [A Developer's Guide to Building Resilient Cloud Applications with Azure](https://www.packtpub.com/product/a-developers-guide-to-building-resilient-cloud-applications-with-azure/9781804611715), published by Packt.

**Deploy applications on serverless and event-driven architecture using a cloud database**

## What is this book about?
To deliver software at a faster rate and reduced costs, companies with stable legacy systems and growing data volumes are trying to modernize their applications and accelerate innovation, but this is no easy matter. A Developer’s Guide to Building Resilient Cloud Applications with Azure helps you overcome these application modernization challenges to build secure and reliable cloud-based applications on Azure and connect them to databases with the help of easy-to-follow examples.
The book begins with a basic definition of serverless and event-driven architecture and Database-as-a-Service, before moving on to an exploration of the different services in Azure, namely Azure API.

This book covers the following exciting features: 
* Understand the architecture of Azure Functions and Azure Service Fabric
* Explore Platform-as-a-Service options for deploying SQL Server in Azure
* Create and manage Azure Storage and Azure Cosmos DB resources
* Leverage big data storage in Azure services
* Select Azure services to deploy according to a specific scenario
* Set up CI/CD pipelines to deploy container applications on Azure DevOps

If you feel this book is for you, get your [copy](https://www.amazon.com/Developers-Guide-Building-Resilient-Applications-ebook/dp/B0BMVW6LQY) today!

<a href="https://www.packtpub.com/?utm_source=github&utm_medium=banner&utm_campaign=GitHubBanner"><img src="https://raw.githubusercontent.com/PacktPublishing/GitHub/master/GitHub.png" alt="https://www.packtpub.com/" border="5" /></a>

## Instructions and Navigations
All of the code is organized into folders. For example, Chapter10.

The commands will look like the following:
```
$ az group create --name healthcareRG --location eastus
$ az identity create -g healthcareRG -n user1
$ az extension add --name storage-preview
$ az storage account create --name myhealthcarestorage1 \
--resource-group healthcareRG \
--location eastus --sku Standard_LRS \
--kind StorageV2 --hns true
```

**Following is what you need for this book:**
This book is for cloud developers, software architects, system administrators, database administrators, data engineers, developers, and computer science students who want to understand the role of the software architect or developer in the cloud world. Professionals looking to enhance their cloud and cloud-native programming concepts on Azure will also find this book useful. A solid background in C#, ASP.NET Core, and any recent version of Visual Studio and basic knowledge of cloud computing, Microsoft Azure, and databases will be helpful when using this book.

With the following software and hardware list you can run all code files present in the book (Chapter 1-11).

### Software and Hardware List

| Chapter  | Software required                                                                   | OS required                       |
| -------- | ------------------------------------------------------------------------------------| ----------------------------------|
| 1-11     | NET 6 and .NET 7, Docker Desktop, Visual Studio Code, Microsoft Azure, Powershell   | Windows, Mac OS X, and Linux (Any)|
| 1-11     | Visual Studio 2022 (community edition)                                              | Windows or macOS                  |
| 5        | Service Fabric Local Cluster Manager, Service Fabric SDK, WebPlatform Installer     | Windows 10 or 11                  |


We also provide a PDF file that has color images of the screenshots/diagrams used in this book. [Click here to download it](https://packt.link/LyxAd).

### Related products <Other books you may enjoy>
* The Azure Cloud Native Architecture Mapbook [[Packt]](https://www.packtpub.com/product/the-azure-cloud-native-architecture-mapbook/9781800562325) [[Amazon]](https://www.amazon.com/Azure-Cloud-Native-Architecture-Mapbook/dp/1800562322)

* Azure for Developers - Second Edition [[Packt]](https://www.packtpub.com/product/azure-for-developers-second-edition/9781803240091) [[Amazon]](https://www.amazon.com/Azure-Developers-ecosystems-containers-serverless/dp/1803240091)

## Get to Know the Author
**Hamida Rebai Trabelsi**
She has been working in the computing domain for over 12 years. She started her professional career in Tunisia working for MNCs as a software developer, then served as a .NET consultant at CGI, Canada and currently she is a Senior Advisor, Information and Solution Integration Architect at Revenu Québec, Canada. She has been awarded with Most Valuable Professional in Developer Technologies and Microsoft DevHeros by Microsoft and holds several Azure certifications. Besides being a Microsoft Certified Trainer and a member of dotnetfoundation, Hamida is a blogger, an international speaker, and one of the finalists in the Women in IT Award Canada 2019.
