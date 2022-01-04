![Microsoft Cloud Workshops](https://github.com/Microsoft/MCW-Template-Cloud-Workshop/raw/main/Media/ms-cloud-workshop.png 'Microsoft Cloud Workshops')

<div class="MCWHeader1">
Analyzing text with Azure Machine Learning and Cognitive Services
</div>

<div class="MCWHeader2">
Hands-on lab step-by-step
</div>

<div class="MCWHeader3">
November 2021
</div>

Information in this document, including URL and other Internet Web site references, is subject to change without notice. Unless otherwise noted, the example companies, organizations, products, domain names, e-mail addresses, logos, people, places, and events depicted herein are fictitious, and no association with any real company, organization, product, domain name, e-mail address, logo, person, place or event is intended or should be inferred. Complying with all applicable copyright laws is the responsibility of the user. Without limiting the rights under copyright, no part of this document may be reproduced, stored in or introduced into a retrieval system, or transmitted in any form or by any means (electronic, mechanical, photocopying, recording, or otherwise), or for any purpose, without the express written permission of Microsoft Corporation.

Microsoft may have patents, patent applications, trademarks, copyrights, or other intellectual property rights covering subject matter in this document. Except as expressly provided in any written license agreement from Microsoft, the furnishing of this document does not give you any license to these patents, trademarks, copyrights, or other intellectual property.

The names of manufacturers, products, or URLs are provided for informational purposes only, and Microsoft makes no representations and warranties, either expressed, implied, or statutory, regarding these manufacturers or the use of the products with any Microsoft technologies. The inclusion of a manufacturer or product does not imply endorsement of Microsoft of the manufacturer or product. Links may be provided to third-party sites. Such sites are not under the control of Microsoft and Microsoft is not responsible for the contents of any linked site or any link contained in a linked site, or any changes or updates to such sites. Microsoft is not responsible for webcasting or any other form of transmission received from any linked site. Microsoft is providing these links to you only as a convenience, and the inclusion of any link does not imply endorsement of Microsoft of the site or the products contained therein.

© 2021 Microsoft Corporation. All rights reserved.

Microsoft and the trademarks listed at <https://www.microsoft.com/en-us/legal/intellectualproperty/Trademarks/Usage/General.aspx> are trademarks of the Microsoft group of companies. All other trademarks are the property of their respective owners.

**Contents**

- [Analyzing text with Azure Machine Learning and Cognitive Services hands-on lab step-by-step](#analyzing-text-with-azure-machine-learning-and-cognitive-services-hands-on-lab-step-by-step)
  - [Abstract and learning objectives](#abstract-and-learning-objectives)
  - [Overview](#overview)
  - [Solution architecture](#solution-architecture)
  - [Requirements](#requirements)
  - [Exercise 1: Create and deploy a Summarization Service](#exercise-1-create-and-deploy-a-summarization-service)
    - [Task 1: Locate and open the summarization notebook](#task-1-locate-and-open-the-summarization-notebook)
    - [Task 2: Run notebook - 01 Summarize](#task-2-run-notebook---01-summarize)
    - [Task 3: Run notebook - 02 Deploy Summarizer Web Service](#task-3-run-notebook---02-deploy-summarizer-web-service)
  - [Exercise 2: Create and deploy a custom Deep Learning Model using Keras](#exercise-2-create-and-deploy-a-custom-deep-learning-model-using-keras)
    - [Task 1: Run notebook - 03 Claim Classification](#task-1-run-notebook---03-claim-classification)
    - [Task 2: Run notebook - 04 Deploy Classifier Web Service](#task-2-run-notebook---04-deploy-classifier-web-service)
  - [Exercise 3: Text classification with Azure Automated Machine Learning](#exercise-3-text-classification-with-azure-automated-machine-learning)
    - [Task 1: Create new automated ML experiment](#task-1-create-new-automated-ml-experiment)
    - [Task 2: Create a new automated ML run](#task-2-create-a-new-automated-ml-run)
    - [Task 3: Monitor automated ML run](#task-3-monitor-automated-ml-run)
    - [Task 4: Review best model performance](#task-4-review-best-model-performance)
  - [Exercise 4: Completing the solution](#exercise-4-completing-the-solution)
    - [Task 1: Retrieve the Text Analytics API endpoint and key](#task-1-retrieve-the-text-analytics-api-endpoint-and-key)
    - [Task 2: Run notebook - 05 Cognitive Services](#task-2-run-notebook---05-cognitive-services)
  - [After the hands-on lab](#after-the-hands-on-lab)
    - [Task 1: Clean up lab resources](#task-1-clean-up-lab-resources)

# Analyzing text with Azure Machine Learning and Cognitive Services hands-on lab step-by-step

## Abstract and learning objectives

In this hands-on lab, you implement a solution that combines both pre-built artificial intelligence (AI) in the form of various Cognitive Services with custom AI in the form of services built and deployed with Azure Machine Learning service. In the lab, you work with unstructured text and learning how to develop analytics pipelines for various problems such as text summarization, text classification, sentiment analysis, opinion mining, key phrase extraction, and language and PII detection. You learn how to build and train a deep neural net for text classification. You will also learn to build Automated Machine Learning models in Azure Machine Learning studio for the purposes of text classification. Finally, you learn how to deploy multiple kinds of predictive services using Azure Machine Learning and learn to integrate with the Text Analytics API from Cognitive Services.

At the end of this hands-on lab, you will be better able to present solutions leveraging Azure Machine Learning services and Cognitive Services.

## Overview

In this workshop, you help Contoso Ltd. build a proof of concept that shows how they can develop a solution that amplifies their agents' claims processing capabilities.

## Solution architecture

The high-level architecture of the solution is illustrated in the diagram. The lab is performed within the context of a notebook running within Azure Machine Learning compute instance. Various notebooks are built to test the integration with the Cognitive Services listed, train custom ML services, and integrate the results in a simple user interface that shows the effect of processing the claim with all the AI services involved.

![The High-level architectural solution begins with a Claim, which points to Claims submission WebApp. The WebApp then points to Text Analytics, and Containerized Services, which includes a Classification Service and a Summary Service that both processes claim text.](media/new_arch.png "High-level architectural solution")
