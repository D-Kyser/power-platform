---
title: "Overview of Power Platform Pipelines (preview)"
description: "Overview of Power Platform Pipelines."
author: caburk
ms.subservice: alm
ms.author: matp
ms.custom: ""
ms.date: 11/02/2022
ms.reviewer: "matp"
ms.topic: "overview"
search.audienceType: 
  - maker
search.app: 
  - PowerApps
  - D365CE
---

# Overview of Power Platform pipelines (preview)

[!INCLUDE [cc-beta-prerelease-disclaimer](../includes/cc-beta-prerelease-disclaimer.md)]

Pipelines aim to democratize application lifecycle management (ALM) for Power Platform and Dynamics 365 customers by bringing ALM automation and CI/CD capabilities into the service in a manner that's more approachable for all makers, admins, and developers.

:::image type="content" source="media/deployment-pipelines.png" alt-text="Example of the deployment Pipelines feature":::

> [!IMPORTANT]
> - This is a preview feature. More information: [Model-driven apps and app management](/power-apps/maker/powerapps-preview-program#model-driven-apps-and-app-management)
> - [!INCLUDE [cc-preview-features-definition](../includes/cc-preview-features-definition.md)]
> - This feature is being gradually rolled out across regions and might not be available yet in your region.

Pipelines significantly reduce the effort and domain knowledge previously required to realize the ROI from adopting healthy, automated ALM processes within your team or organization.

1. Admins easily configure automated deployment pipelines in minutes rather than days or weeks.
1. Makers have an intuitive user experience for easily deploying their solutions.
1. Professional developers can (optionally) run pipelines using their preferred tools such as the Power Platform command line interface (CLI).

## Admins centrally manage and govern pipelines

Pipelines enable admins to centrally govern citizen-led and pro-dev-led projects at scale with less effort. Admins set up the appropriate safeguards that govern and facilitate solution development, testing, and delivery across the organization. Other admin benefits include:

- Lower total cost of ownership:
  - Pipelines significantly improve maker, developer, and admin productivity. Pipelines enable your business solutions to come to market faster, with higher quality, through a safe and governed process.
  - Minimal effort to implement custom-tailored change management processes across your organization or team.
- Save time and money:
  - The system handles the heavy lifting and ongoing maintenance so you don't have to.
- Scale ALM at your own pace:
  - Regardless of where you're at in your ALM journey, you can extend Power Platform pipelines to accommodate your evolving business needs. We aim for this upward transition to be as seamless and effortless as possible. More information: [Microsoft Power Platform CLI](../developer/cli/introduction.md)
- Achieve compliance, safety, monitoring, and automation goals with:
  - Customizations and audit logs saved automatically and are easily accessible.
  - Out of the box analytics provides better visibility within a central location.
  - The ability to create your own reports from within the pipelines app. More information: [Reporting overview for model-driven apps](/power-apps/maker/model-driven-apps/reporting-overview)

## Makers run pre-configured pipelines

Once pipelines are in place, makers can initiate in-product deployments with a few clicks.  They do so directly within their development environments. Other benefits to makers include:

- No prior knowledge of ALM processes or systems required. Citizen developers often view pipelines as a guided change management process.
- Solution deployments are pre-validated against the target environment to prevent mistakes and improve success rates. For example, missing dependencies and other issues are detected before deployment and makers are immediately guided to take the appropriate action.
- Connections and environment variables are provided upfront and validated before the deployment begins.
  - This helps ensure applications and automation are deployed without needing manual post-processing steps, and are connected to the appropriate data sources within each environment.
  - Admins can even pre-configure certain connections that will be used.

## Developers can use the same pipelines

Professional developers are more productive with pipelines now handling the complex background operations. Developers can tell the system what they want to accomplish instead of executing the various underlying tasks necessary to accomplish the same goal. Using the Power Platform CLI, developers can:

- List pipelines to view pertinent details such as which stages and environments are ready to deploy their solutions to.
- Deploy a solution with a single command:
  - With pipelines, developers simply provide the required parameters and the system orchestrates all the end-to-end deployment operations in compliance with the organizational policies.
  - No need to connect to multiple environments, export solutions, download solution files, manually create connections and populate deployment settings files, import solutions, or handle various other tasks that were required previously.

## Frequently asked questions

### Can an environment be associated with multiple hosts?

No. However, one environment can be linked to multiple pipelines within the same host. In order to associate an environment with a different host, you must first navigate to the current host environment and play the Deployment Pipeline Configuration app. Next, remove this environment from any associated pipeline stages, then delete the environment record (just the entry in the app, not the actual environment). Now you can associate this environment with a different host.

### Can I customize or extend the first party deployment pipeline app and tables?

Not currently. For now, don't attempt to customize the app or register plugins on deployment pipeline tables.

### Where can I view and run pipelines?

Currently only within development environments associated with a pipeline. Pipelines can't be viewed or run from within target environments. Notice you may also run pipelines from the Power Platform CLI.

### Can I deploy across regions?

Not currently. The host and all environments associated with pipelines in a host must be located within the same geographic location (as specified when creating environments). For example, a pipeline can't deploy from Germany to Canada. And a host in Germany shouldn't manage environments in Canada. Instead, separate hosts should be used for Germany and Canada.

### Should I deploy the same solution using different pipelines?

Yes, this is possible. Although we recommend starting with the same pipeline for a given solution. This helps avoid confusion and inadvertent mistakes. Pipeline run information is displayed in the context of one pipeline and one solution (within the solution experience). Therefore other pipelines may not show the latest deployed solution version or other important run information associated with different pipelines. Notice the Deployment Pipeline Configuration app shows run information across all pipelines and all solutions for the current host.

### Can the host environment also be used as a development or target environment?

This isn't recommended.

### What do pipelines deploy?

Pipelines deploy solutions as well as configuration for the target environment such as connections, connection references, and environment variables. Any Power Platform customization contained in your solution can be deployed using Pipelines. Pipelines, or solutions in general, don't contain data stored within Dataverse tables. 

### Can I use pipelines in the default environment?

Not currently.

### Should my host environment be the same as where I installed the COE toolkit?

This is possible, but we don't recommend you combine preview features with production workloads.

### Can I deploy unmanaged solutions?

No. We recommend that you deploy managed solutions to non-development environments.

### Can I deploy multiple solutions at once?

Not currently. You'll need to submit a different deployment for each solution. However, the same pipeline can be used for multiple solutions.

### Do pipelines publish unmanaged customizations before exporting the solution?

Not currently. We recommend you publish individual objects as they're saved. Note that only certain solution objects require publishing.

### Can I specify advanced solution import behaviors such as update vs upgrade?

Not currently. Pipelines default behavior is _Upgrade_ with _Maintain customizations_.

### Can I use pipelines for multi-developer teams working in isolated development environments?

The current implementation uses a single development environment for a given solution.

### Can pipelines deploy to a different tenant?

Not currently. We recommend using Azure DevOps or GitHub for this scenario.

### Can I deploy using my own service principal?

Not currently. Note that deployments are facilitated via a Microsoft provided service principal that impersonates the deploying user. This is secure, compliant, and was designed to accommodate future capabilities.

### How are pipelines different from the ALM Accelerator?

Both offer many valuable capabilities and the owning teams work together closely in developing the pipelines and broader ALM vision for Power Platform. Pipelines are more simplistic in nature and can be set up and managed with less effort. Access to other products and technologies isn't required as everything is managed in-house. The ALM Accelerator, on the other hand, is feature rich and capable of handling more advanced ALM scenarios including source code integration and other areas not currently available in-product.

While there are many additional functional differences, the fundamental difference being that pipelines are an official Microsoft Power Platform product feature - meaning it's designed, architected, engineered, tested, maintained, and supported by Microsoft product engineering. Pipelines are built into the product code and can be accessed within native product experiences.

### When should I use pipelines versus another tool?

We encourage customers to choose the tool that best suits their ALM needs. Power Platform pipelines are currently best suited for customers seeking simplicity, fast set up, and lower cost of ownership. Other tools often provide more advanced functionality and source code management. Notice other tools may also be more complicated and costly to set up, use, and maintain.

### Can pipelines be used with Azure DevOps, GitHub, or the ALM Accelerator?

Not currently. We aim for these to work together more seamlessly in the future.

## Next steps

[Set up Power Platform pipelines (preview)](set-up-pipelines.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
