# 📧 Scheduled Email Digest and Summarizer

[![n8n Workflow](https://img.shields.io/badge/Made%20with-n8n-ff6347?logo=n8n&logoColor=white)](https://n8n.io)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

## 🌟 Overview

This n8n workflow is designed to **automatically generate a daily or scheduled summary digest of your recent emails**. It connects to your Gmail account, fetches a batch of messages, aggregates their content, uses an AI large language model (LLM) to create a concise summary, and finally sends the summary back to you (or another recipient) as a new email.

Say goodbye to inbox overload—get the key takeaways delivered straight to your inbox!

---

## ✨ Features

* **Scheduled Execution:** Runs automatically at specified intervals (e.g., every morning at 8 AM).
* **Batch Processing:** Fetches a defined number of recent emails (e.g., 13 items as shown in the image).
* **Content Aggregation:** Merges the body of multiple emails into a single block of text for the model.
* **AI-Powered Summarization:** Utilizes an LLM (via the **Message a Model** node) to produce a professional, concise summary.
* **Self-Delivery:** Sends the final digest email directly to a specified recipient.

---

## 🖼️ Workflow Visualization

This diagram illustrates the step-by-step flow of the automation:

(./scheduled_email_digest_workflow.json)

---

## 🛠️ Prerequisites

Before you can run this workflow, you need:

1.  **An n8n Instance:** Self-hosted or using [n8n Cloud](https://n8n.io/cloud).
2.  **Gmail Account:** With **Google API access** configured for n8n (requires **OAuth2 credentials** for the **Gmail API**).
3.  **AI Model API Key:** An API key for your chosen LLM (e.g., OpenAI, Gemini, Claude) to be used with the **Message a Model** node.

---

## 🚀 Workflow Logic Breakdown

| Step | Node | Function | Notes |
| :--- | :--- | :--- | :--- |
| **1** | **Schedule Trigger** | Starts the workflow at a set time. | Configure this to your desired frequency (e.g., daily). |
| **2** | **Get many messages (Gmail)** | Fetches a batch of emails. | You can use a filter (e.g., `is:unread`) and set the limit (e.g., 13 items). |
| **3** | **Aggregate** | Combines the content of all fetched emails. | Essential to pass one large text block to the AI model. |
| **4** | **Message a model (AI)** | Generates the summary. | The prompt should instruct the model to create a digest from the aggregated text. |
| **5** | **Send a message (Gmail)** | Delivers the final summary. | Configured to send the AI's output as the body of a new email. |

---

## 📥 Installation

1.  **Download the JSON:** Download the workflow file named [`scheduled_email_digest_workflow.json`](./scheduled_email_digest_workflow.json) from this repository.
2.  **Import to n8n:** In your n8n editor, click **"New"** then **"Import from JSON"** and upload the downloaded file.
3.  **Configure Credentials:** Select your previously configured **Gmail / Google OAuth2** and **AI Model API** credentials for the relevant nodes.
4.  **Activate:** Save and activate the workflow to begin scheduling your email digests!
