# 🧠 README: How to Run the `basic_LinkedIn_Agent_Workflow.json`

## 🚀 Overview

This n8n workflow listens for Slack messages, generates a **LinkedIn post about AI literacy (for PolyLabs)** using GPT-4o, formats the output, sends it to **Google Docs**, and posts it to **LinkedIn** after Slack approval.

---

## ✅ Prerequisites

Before running this workflow, make sure you:

1. **Have these credentials set up in n8n:**

   * `Slack API`
   * `Google Docs OAuth2`
   * `LinkedIn OAuth2`
   * `OpenAI API` (GPT-4o access)
2. **Your Slack App is installed**, added to a public channel, and connected to n8n.
3. You’ve updated:

   * The Google **Folder ID** where the doc is stored.
   * The LinkedIn **person ID** to post from.
   * The Slack **channel ID** that triggers the workflow.

---

## 🧱 Node Breakdown

| Node                     | Purpose                                                    |
| ------------------------ | ---------------------------------------------------------- |
| **Slack Trigger**        | Listens for messages in a Slack channel                    |
| **LinkedIn Post Agent**  | Uses GPT-4o to generate a long-form post in PolyLabs voice |
| **Format Output**        | Cleans and formats the generated text                      |
| **Google Docs (Create)** | Saves the post in a new Google Doc                         |
| **Google Docs (Update)** | Appends the cleaned content to the document                |
| **Slack (Approval)**     | Posts the doc link back to Slack and waits for approval    |
| **IF Node**              | Checks if the Slack user approved the post                 |
| **LinkedIn Post**        | Publishes post to LinkedIn once approved                   |

---

## 🧪 How to Run This

### 🔧 Step 1: Import the Workflow

1. Open n8n
2. Click **“Import workflow”** and select `basic_LinkedIn_Agent_Workflow.json`

---

### 🔗 Step 2: Connect Your Credentials

For each node:

* Click into it and select the appropriate **credential**
* Credentials required:

  * Slack API (with valid token)
  * Google Docs (OAuth2)
  * OpenAI (GPT-4o)
  * LinkedIn (OAuth2, with permissions to post)

---

### 💬 Step 3: Configure Slack Trigger

* Edit the `Slack Trigger` node:

  * Set `Channel ID` to the Slack channel you want to monitor
  * Make sure the Slack app is invited to that channel (`/invite @YourBot`)

---

### 📝 Step 4: Set Google Folder ID (Optional)

* In `Linkedin doc creation1`, change `Folder ID` to a folder you control in Google Drive
* You can get this from the folder URL:
  `https://drive.google.com/drive/folders/XXXX`

---

### 🧑‍💼 Step 5: Set LinkedIn Person ID

* In the `Post on LinkedIn` node, make sure `person` is your actual LinkedIn user ID (starts with `urn:li:person:` or short ID like `PnQwcsps5V`)

---

### ▶️ Step 6: Test the Workflow

1. Activate the workflow
2. Post a message in the Slack channel (e.g. `"Generate new post on AI for PolyLabs"`)
3. n8n will:

   * Generate a post
   * Create + update a Google Doc
   * Post the doc link to Slack
   * Wait for your approval ✅

Once you approve:

* The post is published to LinkedIn.

---

## 🧼 Tips & Notes

* You can **customize the prompt** in `Linkedin post generating agent` to change tone, length, or themes.
* The content always reflects **PolyLabs’ brand voice**.
* Add image generation nodes later if you'd like visual assets for the post.

---

