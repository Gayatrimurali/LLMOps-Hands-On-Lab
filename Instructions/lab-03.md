# Lab 03: Evaluating and Deploying LLMs

### Estimated Duration: 60 minutes

## Overview

Participants will assess the performance and reliability of their chat flows and then deploy and manage the Retrieval-Augmented Generation (RAG) flow in a live online environment.

## Lab Objectives

After completing this lab, you will be able to complete the following tasks:

- Task 01: Evaluate Chat Flow Performance and Robustness
- Task 02: Deploy and Manage RAG Flow to an Online Endpoint

## Task 01: Evaluate Chat Flow Performance and Robustness

1. Navigate to your **Multi-Round Q&A on Your Data** prompt flow from the **Tools > Prompt flow** section in your Azure AI Studio.

1. Create a new output named **documents (1)** in the **Outputs** node. This output will represent the documents that were retrieved in the **lookup** node and subsequently formatted in the **generate_prompt_context.output** node. Assign the output of the **generate_prompt_context.output (2)** node to the output of the document.

   ![](media/multi-rag-flow.png)

1. Create a new output named **documents** in the Outputs node. This output will represent the documents that were retrieved in the **lookup** node and subsequently formatted in the **generate_prompt_context** node. Assign the output of the generate_prompt_context node to the output of the document.

   ![](media/new-output-documents.png)

1. Click **Save** before moving on to the next steps.

   ![](media/multi-round-save.png)

1. In Azure AI Studio, navigate to **Tools > Prompt flow** and click on **+ Create**.

   ![](media/+create-prompt-flow.png)

1. Select the **Evaluation Flow** filter and click on the **Clone** option on the **QnA Groundedness Evaluation** card.

   >**Note:** Click on **View more samples** on the top right of the **Create a new flow** window to get more sample evaluation flows.

   ![](media/groundedness-evaluation.png)

1. In the **Clone flow** window, accept the default folder name value and click on **Clone**.

   ![](media/groundedness-evaluation-clone.png)

1. An **Evaluation flow** will be created with the following structure:

   ![](media/groundedness-flow.png)

1. Update the **Connection** field to point to a **gpt-4** deployment in the **groundedness_score** node. After updating the connection information, click on **Save** in the **evaluation flow**.

   ![](media/groundedness-score-save.png)

1. Now, repeat the same steps to create two additional evaluation flows: one **QnA Relevance Evaluation** and another **QnA GPT Similarity Evaluation**.

   >**Note:** Note that the LLM nodes, where you will set the Azure OpenAI connection for each flow, have slightly different names: **relevance_score** and **similarity_score**, respectively.

   - QnA Relevance Evaluation

   ![](media/relevance-evaluation.png)

   ![](media/relevance-score.png)
   
   - QnA GPT Similarity Evaluation

   ![](media/similarity-evaluation.png)

   ![](media/similarity-score.png)

1. In the **Flow** section of **Prompt Flow**, open the **Multi-Round Q&A on Your Data** flow that you created. This will be the flow we use for evaluation.

1. Start the compute session if it has not started already.

1. On your **Multi-Round Q&A on Your Data** flow, select **Custom Evaluation** from the **Evaluate** dropdown.

   ![](media/custom-evaluation-dropdown.png)

1. Click on **Run Anyway** when prompted.
   
1. On the **Batch run and Evaluate** window, in the **Basic settings**, for the **Promt_variants** option, select at least two variants to avoid reaching your GPT-4 model quota limit and click on **Next**.

   ![](media/custom-evaluation-basic-settings.png)

1. On the **Batch run settings**, click on **+ Add new data**.

   ![](media/custom-evaluation-add-new-data.png)

1. On the **Add new data** pane, enter a name for your data, click on **Browse** to choose a file, and upload the **data.csv** file from the **C:\LabFiles** folder and click on **Add**.

   ![](media/custom-evaluation-add-new-data-01.png)

1. After uploading your file, configure the **chat_input** as **$(data.question)** and click on **Next**.

   ![](media/custom-evaluation-basic-settings-next.png)

1. On the **Evaluation settings > Select evaluation**, select the three evaluation flows you created earlier and click on **Next**.

   ![](media/custom-evaluation-select-three.png)

1. On the **Evaluation settings > Configure evaluation** to set up the **question**, **context**, **ground_truth** and **answer** fields for each evaluation flow.

   >**Note:** Please take a moment to ensure you've selected the correct value. It's crucial for accurate metric calculation. Notice that the default values initially presented in the wizard are not the same as those indicated in the following images. 

   - QnA GPT Similarity Evaluation

   ![](media/custom-evaluation-similarity-conifg.png)
  
   - QnA Groundedness Evaluation

   ![](media/custom-evaluation-groundedness-conifg.png)
     
   - QnA Relevance Evaluation
  
   ![](media/custom-evaluation-relevance-conifg.png)

1. Once you have configured all three evaluation settings, click on **Review + submit** and then on the **Submit** option.

1. The evaluation process has started. To view all evaluations (one per variant), navigate to **Tools > Evaluation**.

   >**Note:** Wait for the evaluation status to be shown as **Completed**.

   ![](media/evaluation-status-complete.png)

1. Upon selecting specific evaluation results, you will have the ability to view their detailed information.

1. You can also select **Switch to dashboard view** to access a dashboard that provides a tabular and visual comparison between the rounds of different variations.

   ![](media/evaluation-switch-dashboard.png)

   - Table Comparison

   ![](media/table-comparison.png)
   
   - Chart comparison

   ![](media/chart-comparison.png)

## Task 02: Deploy and Manage RAG Flow to an Online Endpoint

1. In Azure AI Studio, navigate to **Tools > Prompt flow** and select the **Multi-Round Q&A on Your Data** chat flow.

1. Select **Deploy** in the flow editor.

   ![](media/multi-flow-deploy.png)

1. On the **Basic settings** tab, configure the basic settings to deploy the endpoint in the deployment wizard, and click on **Review + create**.

   - Endpoint: **New** 
   - Endpoint Name: **odl-user-<inject key="Deployment-ID" enableCopy="false"/>-xxxx-xxxx**
   - Deployment name: **odl-user-<inject key="Deployment-ID" enableCopy="false"/>-xxxx-xxxx**
   - Virtual Machine: **Standard_E2s_v3** or select any other size.
   - Instance count: **1**

   ![](media/multi-flow-deploy-basic-settings.png)

1. On the **Review** tab, click on **Create** to deploy the prompt flow.

1. To view the status of your deployment, select **Deployments** from the left navigation. Once the deployment is created successfully, you can select the deployment to view the details.

   >**Note:** This might take a while for the deployment to succeed. Wait for the deployment status to appear as **Succeed**.

   ![](media/llm17.png)

1. Select the **Consume** tab to see code samples that can be used to consume the deployed model in your application.

   ![](media/endpoint-deployment-consume.png)

1. You can use the **REST endpoint** directly or get started with one of the samples.

   ![](media/endpoint-deployment-samples.png)

#### Validation
 
<validation step="69c0b1c3-345d-49aa-9e22-e70838c77609" />
   
> **Congratulations** on completing the task! Now, it's time to validate it. Here are the steps:
> - Click on the **Validate** button for the corresponding task. If you receive a success message, you can proceed to the next task. 
> - If not, carefully read the error message and retry the step, following the instructions in the lab guide.
> - If you need any assistance, please contact us at **labs-support@spektrasystems.com**. We are available 24/7 to help you out.

## Summary

In this lab, you have performed  the following tasks:

- Evaluated chat flow performance and robustness.
- Deployed and managed RAG flow to an online endpoint.

### You have successfully completed the lab.





