# Deep Research
#### **Empower Your AI with Real-time Web Intelligence**
The Deep Research Dify Plugin transforms your AI applications into powerful research assistants by integrating seamless, real-time web search capabilities. Leveraging the advanced Tavily API, this tool allows your Large Language Models (LLMs) to go beyond their training data, accessing the latest and most relevant information directly from the internet.

Whether you're building an AI agent for comprehensive market analysis, a content generation system requiring factual validation, or a sophisticated research bot for academic inquiries, the Deep Research plugin provides the critical bridge to external knowledge.


### Description

#### Deep Research: Transform Your Dify AI with Dynamic Web Insights

Unleash the full potential of your Dify applications. The Deep Research plugin empowers your AI to move beyond static data, providing real-time, comprehensive web intelligence directly within your workflows and agents. Seamlessly integrate the power of the Tavily API to ensure your LLMs always have access to the most current and relevant information.

#### Key Capabilities:

Real-time Web Search: Execute precise, on-demand queries to fetch up-to-the-minute information from across the internet.

Intelligent Content Snippets: Automatically extract the most pertinent content excerpts from search results, optimized for immediate LLM comprehension and synthesis.

Configurable Result Depth: Fine-tune your research scope by effortlessly specifying the exact number of search results required, ensuring focused and efficient data retrieval.

Seamless Integration: Designed for intuitive interaction within Dify's orchestration studio, allowing your AI to autonomously leverage web knowledge when it matters most.

Deliver Factual, Up-to-Date Responses: Equip chatbots with live product data, news, or factual answers.

Automate Complex Research: Power agents that can independently gather information for reports, market analysis, or competitive intelligence.

Enhance Decision-Making: Provide LLMs with the freshest data points for more accurate and contextually rich outputs.

Empower your Dify applications to explore, learn, and deliver with unparalleled web intelligence. Integrate Deep Research today!


## 🚀 Prerequisites
Before installing and using the Deep Research plugin, ensure you have the following:

Dify Instance: A running Dify self-hosted instance (v1.4.3 or newer recommended for full compatibility).

Tavily API Key: An API key from Tavily. This is essential for the plugin to perform web searches.


##📦 Installation
The Deep Research plugin can be installed in your Dify instance via a local package file.

### 1. Package the Plugin
cd ~/deepResearch

explore the files, or create ur own improvements
```
.
├── GUIDE.md
├── PRIVACY.md
├── README.md
├── __pycache__/   
├── _assets
│   └── icon.svg
├── main.py
├── manifest.yaml
├── provider
│   ├── __pycache__/ 
│   ├── deep_research.py
│   └── deep_research.yaml
├── requirements.txt
└── tools
    ├── deep_research.py
    └── deep_research.yaml
```
### 2. Upload to Dify
- Access your Dify UI.

- Navigate to the "Plugins" section in the left sidebar.

- Click the "Install" button (or "Add Plugin") in the top right.(or install plugin directly from marketplace(if available ))

- Select "Install via Local File".

- Upload the deep_research_plugin.difypkg file you just created.

## 🔑 Configuration & Credentials
After installing the plugin, you must provide your Tavily API Key:

In the Dify UI, go to the "Plugins" section.

Find and click on your "Deep Research" plugin.

Click the "Authorize" or "Settings" button (usually a key icon or cogwheel).

In the displayed form, enter your Tavily API Key into the designated field.

Click "Save" or "Authorize" to apply the changes.

Connection Requirements:

Your Dify instance must have outbound internet access to reach the Tavily API at api.tavily.com (port 443 for HTTPS).

The Dify plugin_daemon service (or the api service if plugin_daemon is integrated) needs to be running and healthy within your Dify Docker environment.

## 💡 Usage Instructions
Once installed and configured, you can integrate "Deep Research" into your Dify applications.

### 1. Enable Plugin in Your Application
Go to "Studio" (or "Applications") in Dify.

Create a new application (e.g., a "Chatflow" or "Agent") or open an existing one.

On the orchestration canvas, locate the "Tools" section (often on the right sidebar or within the LLM node configuration).

Enable the "Deep Research" plugin by selecting it from the list.

### 2. Prompting Your AI (Chatflow/Agent Applications)
For conversational applications, the LLM will intelligently decide when to use the tool based on your prompt and the user's input. Craft your System Prompt to guide the LLM's usage:

```
You are an intelligent research assistant capable of performing real-time web searches.
You have access to the "Deep Research" tool.
When the user asks a question that requires current, external, or factual information, you MUST use the "Deep Research" tool to find the answer.
You can optionally specify the number of search results to retrieve (e.g., "find 10 results").
```
Example User Prompts:
- "What are the latest advancements in AI ethics?"
- "Research the impact of climate change on ocean ecosystems, providing 7 key findings."
- "Summarize the history of the internet."

The LLM will automatically pass the query and max_results parameters to the tool.

3. Using the Tool Node (Workflow Applications)
For more structured, automated tasks, you can explicitly use a "Tool" node in a Workflow:

On the Dify Workflow orchestration canvas, click "+" to add a new node.

Select the "Tool" node.

In the Tool node's configuration panel:

Choose "Deep Research" from the "Tool" dropdown.

Map Inputs:

query: Connect this to a variable containing your search query (e.g., {{#start.query}} from a "Start" node, or a variable from an "LLM" node that extracts the query).
