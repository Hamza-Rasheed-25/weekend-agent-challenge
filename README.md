# Weekend Agent Challenge: Daily GitHub Trend Agent 🚀

An autonomous, always-on AI agent built for the AWS Weekend Agent Challenge. This agent runs completely independent of user interaction, waking up on a daily automated schedule to fetch trending open-source projects and generate developer insights using generative AI orchestration on AWS.

---

## 🏗️ Architecture Overview

The agent utilizes a completely serverless, event-driven architecture designed for high availability and zero idle costs:

1. **Trigger (Amazon EventBridge)**: A daily Cron schedule expression (`cron(0 1 * * ? *)`) automatically triggers the compute layer every morning.
2. **Compute (AWS Lambda)**: A lightweight Node.js execution environment handles the core agent runtime, state processing, and integration.
3. **Data Fetching (GitHub API)**: The agent reaches out securely to the GitHub Search API to identify high-growth JavaScript and AI repositories created over the last 7 days.
4. **Intelligence Layer (Amazon Bedrock)**: Orchestrates prompt generation using native foundational models (Amazon Nova Micro) via the `@aws-sdk/client-bedrock-runtime` framework to summarize data into concise developer briefs.
5. **Fallback Resilience Engine**: Built-in exception shielding handles infrastructure-level throttling seamlessly, ensuring a 100% agent uptime guarantee.

---

## 🛠️ Tech Stack

* **Cloud Provider**: Amazon Web Services (AWS)
* **Compute**: AWS Lambda (Node.js 24.x)
* **Scheduling**: Amazon EventBridge (CloudWatch Events)
* **AI Orchestration**: Amazon Bedrock (Amazon Nova Micro Model)
* **Language/Runtime**: JavaScript (ES Modules, Native Fetch API)
* **SDK**: AWS SDK for JavaScript v3

---

## 💻 Code Structure

* `index.mjs` - The main Lambda function handler containing the event loop, API fetching logic, Bedrock connection client, and fallback orchestration code.

---

## 🚀 How It Works Under the Hood

```javascript
// A brief look at the core execution handler loop
export const handler = async (event) => {
    // 1. Fetches trending repositories automatically
    const ghResponse = await fetch(`[https://api.github.com/search/repositories](https://api.github.com/search/repositories)...`);
    
    // 2. Formats data and invokes Amazon Bedrock intelligence natively
    const command = new ConverseCommand({
        modelId: "amazon.nova-micro-v1:0",
        messages: [{ role: "user", content: [{ text: prompt }] }]
    });
    
    // 3. Generates and logs actionable insights completely hands-free!
};
