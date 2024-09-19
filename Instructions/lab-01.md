# Lab 01: Introduction to LLMs and Azure AI Services

### Estimated Duration: 60 minutes

## Overview

Participants will set up an AI project and hub, deploy Azure OpenAI models, and integrate content safety services. They will use the Azure AI Studio Playground to test models, work with open-source LLMs, and create and manage prompt flows, ensuring safe and effective AI interactions.

## Lab Objectives

After completing this lab, you will be able to complete the following tasks:

- Task 01: Create an AI Project and AI Hub Resources
- Task 02: Deploy Azure OpenAI Models
- Task 03: Create a Content Safety Service
- Task 04: Add an Azure Content Safety connection
- Task 05: Use Azure AI Studio Playground
- Task 06: Work with an Open Source LLM Model
- Task 07: Test the prompt in Content Safety
- Task 08: Create a Prompt Flow

## Task 01: Create an AI Project and AI Hub Resources

1. Navigate to https://ai.azure.com to create a project in **Azure AI Studio**.

   ![](media/azure-ai-studio.png)

1. Sign in to **Azure AI Studio** using the credentials from the **Environment** tab.

1. Click on **+ New Project** to create a new project and hub.

   ![](media/create-new-project.png)

1. On the **Project details** section, enter a unique **name** for your project and select **Create a new Hub** option from the drop-down menu. Moving on, click on **Next**. 

   ![](media/new-project-name.png)

1. On the **Create a Hub** section, configure the below values.

   - Hub name: **odl_user_<inject key="Deployment-ID" enableCopy="false"/>_ai**
   - Subscription: **Select your Default Subscription**
   - Resource group: **llm-ops-<inject key="Deployment-ID" enableCopy="false"/>**
   - Location: **<inject key="Region" enableCopy="false"/>**
   - Connect Azure AI Service or Azure OpenAI: **(new)ai-odl-user_<inject key="Deployment-ID" enableCopy="false"/>_ai**

      ![](media/llm1.png)

1. Click on **Create new AI Search (1)** for the **Connect Azure AI Search** option. Enter the **name (2)** for your **Azure AI Search** and click on **Create**.

   ![](media/create-new-ai-search.png)

1. On the **Create a Hub** section, click on **Next**.

   ![](media/create-hub-next.png)

1. In the **Review and finish** section, review your Azure AI services, click on **Create a project,** and wait for the deployments to succeed.

   ![](media/review-create-project.png)

1. You can also navigate to your **Resource groups** section in the Azure portal to verify the resources deployed.

   ![](media/azure-portal-resources.png)

1. Within the selected **resource group**, in the left-hand menu, click on **Access control (IAM)**.

1. In the **Access Control (IAM)** pane, click on the **+ Add** button at the top.

   ![](media/1iam.png)

1. Select **Add role assignment** from the drop-down.

1. In the **Add role assignment** pane, you'll see a drop-down labeled **Role**.

1. Click on the **drop-down**, select **Reader** and click on **Next**. This role allows the user or entity to view all resources in the **resource group** but not make any changes.

1. Under the **Assign access to** section, select **Managed identity (2)**.

1. Click on **+ Select members (3)**.

1. Select your **subscription (4)** under **Subscription** and select **Azure AI project (1) (5)** under **Managed identity**.

1. In the **Select** pane, search for and select the **specific project ID** or **managed identity associated with the AI project** you are working on **(6)**.

1. Once selected, click on **Select (7)** to confirm your choice.

1. Click on **Review + assign (8)** within the **Members** tab, and then click **Review + assign** again to complete the process.

   ![](media/IAM.png)

1. A notification will appear confirming that the role assignment has been successfully added.

#### Validation
 
<validation step="ee969cae-cf3c-46aa-b0fe-5bb362b64bef" />

> **Congratulations** on completing the task! Now, it's time to validate it. Here are the steps:
> - Click on the **Validate** button for the corresponding task. If you receive a success message, you can proceed to the next task. 
> - If not, carefully read the error message and retry the step, following the instructions in the lab guide.
> - If you need any assistance, please contact us at **labs-support@spektrasystems.com**. We are available 24/7 to help you out.

## Task 02: Deploy Azure OpenAI Models

1. Navigate to **Components > Deployments (1)** settings. Click on **Deploy a model (2)** and select **Deploy base model (3)** to create an OpenAI model.
   
   ![](media/llm3.png)

1. Select **gpt-4 (1)** from the list of models and click on **Confirm (2)**.

   ![](media/gpt-4-deployment.png)

1. On the **Deploy model gpt-4** pane, click on **Customize**.

   ![](media/llm4.png)

1. Change the model version to **0125-Preview (1)** and select **Standard (2)** for the deployment type. Click on **Deploy (3)**.

   ![](media/llm5.png)
   
1. Verify that the **gpt-4** model is present in the **Deployments** section.

   ![](media/gpt-4-model-deployments.png)

1. On the **Components > Deployments** settings. Click on **Deploy a model (2)** and select **Deploy base model (3)** to create an OpenAI model.
   
1. Select **text-embedding-ada-002** from the list of models and click on **Confirm**.

   ![](media/text-embedding-model.png)

1. On the **Deploy model text-embedding-ada-002** pane, accept the default settings and click on **Deploy**.

   ![](media/llm11.png)

1. Verify that the **text-embedding-ada-002** model is present in the **Deployments** section.

   ![](media/text-embedding-model-deployments.png)

## Task 03: Create a Content Safety Service

1. Navigate to the **Azure portal** and search for **content safety**.

   ![](media/search-content-safety.png)

1. On the **Azure AI Serices | Content safety** tab, click on **+ Create**.

   ![](media/+create-content-safety.png)

1. On the **Create Content Safety** **Basics** tab, configure the following resources and click on **Next (6)**.

   >**Note:** Create the Content Safety resource in the same region where you have deployed the Azure AI services.

   - Subscription: **Select your Default Subscription (1)**
   - Resource group: **llm-ops-<inject key="Deployment-ID" enableCopy="false"/> (2)**
   - Region: **<inject key="Region" enableCopy="false"/> (3)**
   - Name: **content-safety-<inject key="Deployment-ID" enableCopy="false"/>(4)**
   - Pricing tier: **Standard S0 (5)**

   ![](media/create-content-safety.png)

1. Click on **Next** again.
   
1. On the **Identity** tab, verify that the **System-assigned managed identity Status** is turned **On**. Click on **Review + create** and then on the **Create** option.

   ![](media/create-content-safety-identity.png)

#### Validation
 
<validation step="071312be-06ef-4970-a4c0-5ff6deb9cc40" />

> **Congratulations** on completing the task! Now, it's time to validate it. Here are the steps:
> - Click on the **Validate** button for the corresponding task. If you receive a success message, you can proceed to the next task. 
> - If not, carefully read the error message and retry the step, following the instructions in the lab guide.
> - If you need any assistance, please contact us at **labs-support@spektrasystems.com**. We are available 24/7 to help you out.

## Task 04: Add an Azure Content Safety connection

1. Navigate to your **odl_user_<inject key="Deployment-ID" enableCopy="false"/>-XXXX** project in **Azure AI Studio**.

   ![](media/project-select.png)

1. On the **project overview** page, navigate to the **Settings** tab and click on **+ New connection** under **Connected resources**.

   ![](media/project-new-connection.png)

1. On the **Add a connection to external assets** pane, click on **Azure AI Content Safety**.

   ![](media/select-content-safety-connection.png)

1. On the **Connect an Azure AI Content Safety resource** pane, click on **Add connection** for the existing Content Safety resource that you had created in the previous task.

   ![](media/add-content-safety-connection.png)

1. Once the status shows as **Connected**, click on **Close**.

   ![](media/review-content-safety-connection.png)

1. Navigate back to **Settings > Connected resources** to verify the **Azure Content Safety connection**.

   ![](media/confirm-content-safety-connection.png)

## Task 05: Use Azure AI Studio Playground

1. In your **Azure AI Studio**, navigate to the **gpt-4** deployment under the **Deployments** option.

   ![](media/llm14.png)

1. On the **gpt-4** deployment details, click on **Open in playground**.

   ![](media/llm6.png)

1. Let us run an example where the model will help us summarize and extract information from a conversation between a customer and a representative of a telco company.

1. Copy the following prompt into the **System message** field of the **Chat playground** and click on **Apply changes**.

   ```
   You're an AI assistant that helps telco company to extract valuable information from their conversations by creating JSON files for each conversation transcription you receive. You always try to extract and format it as a JSON:
   1. Customer Name [name]
   2. Customer Contact Phone [phone]
   3. Main Topic of the Conversation [topic]
   4. Customer Sentiment (Neutral, Positive, Negative)[sentiment]
   5. How the Agent Handled the Conversation [agent_behavior]
   6. What was the FINAL Outcome of the Conversation [outcome]
   7. A really brief Summary of the Conversation [summary]

   Only extract information that you're sure of. If you're unsure, write "Unknown/Not Found" in the JSON file.
   ```

   ![](media/llm7.png)

   >**Note:** If you receive an **"Update systems message?"** pop-up, enable **Do not show this again,** and click on **Continue**.

   ![](media/update-sys-msg.png)
   
1. Copy the following text in the **chat session** and click on the **send** button.

   ```
   Agent: Hello, welcome to Telco's customer service. My name is Juan, how can I assist you?
   Client: Hello, Juan. I'm calling because I'm having issues with my mobile data plan. It's very slow and I can't browse the internet or use my apps.
   Agent: I'm very sorry for the inconvenience, sir. Could you please tell me your phone number and your full name?
   Client: Yes, sure. My number is 011-4567-8910 and my name is Martín Pérez.
   Agent: Thank you, Mr. Pérez. I'm going to check your plan and your data usage. One moment, please.
   Client: Okay, thank you.
   Agent: Mr. Pérez, I've reviewed your plan and I see that you have contracted the basic plan of 2 GB of data per month. Is that correct?
   Client: Yes, that's correct.
   Agent: Well, I inform you that you have consumed 90% of your data limit and you only have 200 MB available until the end of the month. That's why your browsing speed has been reduced.
   Client: What? How is that possible? I barely use the internet on my cell phone. I only check my email and my social networks from time to time. I don't watch videos or download large files.
   Agent: I understand, Mr. Pérez. But keep in mind that some applications consume data in the background, without you realizing it. For example, automatic updates, backups, GPS, etc.
   Client: Well, but they didn't explain that to me when I contracted the plan. They told me that with 2 GB I would have enough for the whole month. I feel cheated.
   Agent: I apologize, Mr. Pérez. It was not our intention to deceive you. I offer you a solution: if you want, you can change your plan to a higher one, with more GB of data and higher speed. This way you can enjoy a better browsing experience.
   Client: And how much would that cost me?
   Agent: We have a special offer for you. For only 10 pesos more per month, you can access the premium plan of 5 GB of data and 4G speed. Are you interested?
   Client: Mmm, I don't know. Isn't there another option? Can't you give me more speed without charging me more?
   Agent: I'm sorry, Mr. Pérez. That's the only option we have available. If you don't change your plan, you'll have to wait until next month to recover your normal speed. Or you can buy an additional data package, but it would be more expensive than changing plans.
   Client: Well, let me think about it. Can I call later to confirm?
   Agent: Of course, Mr. Pérez. You can call whenever you want. The number is the same one you dialled now. Is there anything else I can help you with?
   Client: No, that's all. Thank you for your attention.
   Agent: Thank you, Mr. Pérez. Have a good day. Goodbye.
   ```

   ![](media/llm8.png)

1. You will see a result generated by the model similar to the one shown in the image below. Notice that the model has correctly followed the instructions indicated in the **System message** field.

   ```
   {
   "name": "Martín Pérez",
   "phone": "011-4567-8910",
   "topic": "Mobile data plan issues",
   "sentiment": "Negative",
   "agent_behavior": "Polite and helpful, offered solutions",
   "outcome": "Client is considering options, will call back later",
   "summary": "Client Martín Pérez called to complain about slow mobile data. Agent explained that he had almost reached his data limit for the month, causing the reduced speed. The agent suggested upgrading his plan for better service, but the client was unsure and said he would think about it and call back later."
   }
   ```
   
   ![](media/llm9.png)
   
## Task 06: Work with an Open Source LLM Model

1. Now let's test an **open-source Llama2 model** from Meta. Navigate to **Components > Deployments (1)** settings. Click on **Deploy a model (2)** and select **Deploy base model (3)** to create an OpenAI model.
   
   ![](media/llm3.png)

1. Search for and select **Llama-2-13b-chat** from the list of models, and click on **Confirm**.

   ![](media/llama-chat-model-confirm.png)

1. On the **Deployment options** tab, click on **Serverless API with Azure AI Content Safety**.

   ![](media/llama-serverless-api.png)

1. On the **Serverless API deployment for Llama-2-13b-chat** tab, select your project and click on **Subscribe and Deploy**.

   ![](media/llama-subs-and-deploy.png)

1. Once the **Serverless API deployment for Llama-2-13b-chat** deployment succeeds, click on the **Deploy** option on the **Deploy Llama-2-13b-chat**.

   ![](media/llama-chat-model-deploy.png)

1. Wait for the chat model provisioning state to appear as **Succeeded** before using the deployment.

   ![](media/llama-provisioning-state.png)

1. On the **Llama-2-13b-chat** deployment details, click on **Open in playground** to start using the **Open Source LLM Model**.

   ![](media/llama-open-in-playground.png)

## Task 07: Test the prompt in Content Safety

1. On your **Azure AI Studio,** navigate to **AI Services** and click on the **Content Safety** box to get started with **Content Safety Studio**.

   ![](media/ai-services-content-safety.png)

1. On the **Content Safety** studio, click on the **Moderate text content** option to try out the prompt.

   ![](media/content-safety-studio.png)

1. On the **Moderate text content** window, select the **content safety resource** from the **Azure AI services resources** dropdown.

   ![](media/content-safety-resource-select.png)

1. In the **Test** section, copy and paste the below text in the text box and click on **Run test**.

   ```
   You're an AI assistant that helps telco company to extract valuable information from their conversations by creating JSON files for each conversation transcription you receive. 

   You always try to extract and format as a JSON, field names between square brackets:

   1. Customer Name [name]
   2. Customer Contact Phone [phone]
   3. Main Topic of the Conversation [topic]
   4. Customer Sentiment (Neutral, Positive, Negative)[sentiment]
   5. How the Agent Handled the Conversation [agent_behavior]
   6. What was the FINAL Outcome of the Conversation [outcome]
   7. A really brief Summary of the Conversation [summary]

   Conversation:

   Agent: Hi Mr. Perez, welcome to Telco's customer service. My name is Juan, how can I assist you?
   Client: Hello, Juan. I am very dissatisfied with your services.
   Agent: ok sir, I am sorry to hear that, how can I help you?
   Client: I hate this company I will kill everyone with a bomb.
   ```

   ![](media/content-safety-run-test.png)

1. In the **View Results** section, notice how the content safety resource blocks the content because the **Violence** filter is triggered with the provided content.

   ![](media/content-safety-view-results.png)

1. You can configure the **Threshold level** for the four categories and test out different prompts.

   ![](media/content-safety-threshold-level.png)

## Task 08: Create a Prompt Flow

1. Navigate to the **gpt-4** deployment under the **Deployments** settings in your **Azure AI Studio**.

   ![](media/gpt-4-model-deployments.png)

1. Perform the same steps that you performed in **Task 05** by adding the same system message, applying the changes, and fetching the response. Once the response is generated, click on **Prompt flow**.

   ![](media/chat-playground-prompt-flow.png)

1. On **"Orchestrate and customize this setup with prompt flow,"** click on **Open**. This will create a new prompt flow.

   ![](media/prompt-flow-open.png)

   >**Note:** If it takes too long, refresh the page and re-enter the details and click on **prompt flow**; the prompt flow should appear right away.

1. Notice how the prompt flow is created with a single node, which represents the step in the flow where the LLM model is configured.

   ![](media/prompt-flow-graph.png)

1. Once the new prompt flow opens, click on **Start compute session** before you start using the chat session.

   ![](media/prompt-flow-start-compute.png)

1. Configure the connection settings with the AI service and the GPT-4 deployment for the **chat** node, and then click on the **Chat** button to test your flow in the **chat window**.

   ![](media/prompt-flow-connection-chat.png)

1. In the **chat window**, copy and paste the below conversation and click on **send** to view the expected response.

   ```
   Agent: Hello, welcome to Telco's customer service. My name is Juan, how can I assist you?
   Client: Hello, Juan. I'm calling because I'm having issues with my mobile data plan. It's very slow and I can't browse the internet or use my apps.
   Agent: I'm very sorry for the inconvenience, sir. Could you please tell me your phone number and your full name?
   Client: Yes, sure. My number is 011-4567-8910 and my name is Martín Pérez.
   Agent: Thank you, Mr. Pérez. I'm going to check your plan and your data usage. One moment, please.
   Client: Okay, thank you.
   Agent: Mr. Pérez, I've reviewed your plan and I see that you have contracted the basic plan of 2 GB of data per month. Is that correct?
   Client: Yes, that's correct.
   Agent: Well, I inform you that you have consumed 90% of your data limit and you only have 200 MB available until the end of the month. That's why your browsing speed has been reduced.
   Client: What? How is that possible? I barely use the internet on my cell phone. I only check my email and my social networks from time to time. I don't watch videos or download large files.
   Agent: I understand, Mr. Pérez. But keep in mind that some applications consume data in the background, without you realizing it. For example, automatic updates, backups, GPS, etc.
   Client: Well, but they didn't explain that to me when I contracted the plan. They told me that with 2 GB I would have enough for the whole month. I feel cheated.
   Agent: I apologize, Mr. Pérez. It was not our intention to deceive you. I offer you a solution: if you want, you can change your plan to a higher one, with more GB of data and higher speed. This way you can enjoy a better browsing experience.
   Client: And how much would that cost me?
   Agent: We have a special offer for you. For only 10 pesos more per month, you can access the premium plan of 5 GB of data and 4G speed. Are you interested?
   Client: Mmm, I don't know. Isn't there another option? Can't you give me more speed without charging me more?
   Agent: I'm sorry, Mr. Pérez. That's the only option we have available. If you don't change your plan, you'll have to wait until next month to recover your normal speed. Or you can buy an additional data package, but it would be more expensive than changing plans.
   Client: Well, let me think about it. Can I call later to confirm?
   Agent: Of course, Mr. Pérez. You can call whenever you want. The number is the same one you dialled now. Is there anything else I can help you with?
   Client: No, that's all. Thank you for your attention.
   Agent: Thank you, Mr. Pérez. Have a good day. Goodbye.
   ```

   ![](media/prompt-flow-chat-response.png)

   >**Note:** Please press Enter if the send icon is not visible.

## Summary

In this lab, you have performed  the following tasks:

- Created an AI project and AI hub resources.
- Deployed Azure OpenAI models.
- Created a content safety service.
- Added an Azure content safety connection.
- Used Azure AI studio playground.
- Worked with an open-source LLM model.
- Tested the prompt in content safety.
- Created a prompt flow.

### You have successfully completed the lab.
