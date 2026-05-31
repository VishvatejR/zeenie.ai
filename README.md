Here's a GitHub-ready README based on your workflow configuration. It reflects the actual nodes and settings from the uploaded workflow. 

# WhatsApp AI Assistant

A WhatsApp AI Assistant built with MachinaOS that combines Gemini, conversation memory, and live web search to provide intelligent responses directly on WhatsApp.

## Features

* 💬 WhatsApp message handling
* 🧠 Google Gemini-powered AI responses
* 🔍 Live web search using DuckDuckGo
* 📝 Conversation memory for contextual chats
* ⚡ Real-time response generation
* 🌐 Access to current information when needed

## Workflow Architecture

```text
WhatsApp Receive
        │
        ▼
    AI Agent
    ├── Simple Memory
    ├── Master Skill
    └── DuckDuckGo Search
        │
        ▼
   WhatsApp Send
```

## How It Works

### 1. Receive Messages

The workflow listens for incoming WhatsApp messages.

### 2. Process with AI Agent

The AI Agent uses:

* Gemini Flash Latest
* Conversation memory
* DuckDuckGo Search tool
* Master Skill integration

### 3. Live Information Retrieval

When users ask for:

* Current events
* Latest news
* Real-time information
* Recent developments

The AI Agent automatically uses DuckDuckGo Search to gather current information before generating a response.

### 4. Send Response

The generated answer is sent back to WhatsApp.

## Tech Stack

| Component          | Technology          |
| ------------------ | ------------------- |
| Workflow Engine    | MachinaOS           |
| LLM                | Gemini Flash Latest |
| Search Engine      | DuckDuckGo Search   |
| Memory             | Simple Memory       |
| Messaging Platform | WhatsApp            |

## Nodes Used

### WhatsApp Receive

Receives incoming WhatsApp messages.

Configuration:

```text
Message Type Filter: All
Include Media Data: False
```

### AI Agent

Main reasoning engine.

Configuration:

```text
Provider: Gemini
Model: gemini-flash-latest
```

Prompt:

```text
{{whatsappreceive.text}}
```

System Instruction:

```text
You are a helpful assistant.

In case if user asks for some live information or data,
use duckduckgo search tool and use the time as
{{whatsappreceive.timestamp}}
```

### Simple Memory

Maintains conversation history.

Configuration:

```text
Window Size: 100
Long Term Memory: Disabled
Retrieval Count: 3
```

### DuckDuckGo Search

Provides real-time information.

Configuration:

```text
Query: {{whatsappreceive.text}}
Max Results: 5
```

### WhatsApp Send

Sends AI responses back to WhatsApp.

Configuration:

```text
Message Type: Text
Message: {{aiagent.response}}
Markdown Enabled: True
```

## Installation

### 1. Clone Repository

```bash
git clone https://github.com/yourusername/whatsapp-ai-assistant.git
cd whatsapp-ai-assistant
```

### 2. Import Workflow

Import the provided JSON workflow into MachinaOS.

### 3. Configure Gemini

Add your Gemini API credentials within MachinaOS.

### 4. Configure WhatsApp

Connect your WhatsApp integration.

### 5. Run

Start the workflow.

## Example Queries

### General Questions

```text
Explain quantum mechanics.
```

```text
How does WhatsApp make money?
```

### Live Information

```text
What are today's top AI news stories?
```

```text
Latest IPL updates.
```

```text
Current Bitcoin price.
```

The assistant will automatically use DuckDuckGo Search when real-time information is required.

## Future Improvements

* Voice message support
* Weather API integration
* News API integration
* Multi-language support
* Long-term memory
* Stock market tracking
* Cryptocurrency tracking
* Calendar integration
* Email integration
* Custom skills

## Project Structure

```text
Whatsapp AI Assistant workflow.json
README.md
```

## License

MIT License

## Author

Built using MachinaOS, Gemini, WhatsApp Integration, and DuckDuckGo Search.

---

