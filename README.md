# NVIDIA Meeting Recorder Agent 📹

<div align="center">
  <img src="https://assets.xpanderai.io/agents/agent/tamplates/meeting-recorder.png" alt="NVIDIA Meeting Recorder Agent" width="700">

  <a href="https://app.xpander.ai/templates/48039a71-c99c-4691-8b66-a6faca3ccbe4"><img src="https://img.shields.io/badge/Deploy%20to-Xpander.ai-6014FE?style=for-the-badge&logo=appveyor" alt="Deploy to xpander.ai"></a>
  <a href="./nvidia-meeting-recorder-agent.ipynb"><img src="https://img.shields.io/badge/View%20Jupyter%20Notebook-6014FE?style=for-the-badge&logo=read-the-docs" alt="View Jupyter Notebook"></a>
</div>

## Overview

An open-source autonomous AI agent implementation built on xpander.ai, a complete backend for agents, and NVIDIA NIM. This reference architecture demonstrates how to build multi-step autonomous agents with persistent memory, tool orchestration, and state management using a low-abstraction approach.

This implementation provides a foundation for building agents that can:
- Access external APIs (Calendar, Meeting Services)
- Execute complex multi-turn operations (Recording setup, asset retrieval)
- Maintain state across interactions
- Process and synthesize information from various sources

## Technical Architecture

The agent uses a modular design based on:
- **LLM**: NVIDIA NIM with llama-3.1-nemotron-ultra-253b-v1
- **Foundation**: xpander.ai SDK for agent orchestration
- **Tools**: Calendar, Recorder, Status, Email, each implemented as composable functions
- **Memory**: Persistent thread-based context retention
- **Session Management**: Dynamic session tracking for multi-step operations

## Demo Videos

<div align="center">
  
  # Demo 1 (Ask the Agent to record meetings)

https://github.com/user-attachments/assets/5099acce-8327-451c-b0ee-fc3de2254feb


  
  # Demo 2 (Ask the Agent to summarize the meeting notes and email you the video + the meeting summary)
  

https://github.com/user-attachments/assets/da5649c8-4d58-44f1-82a5-5cdf2d4b8729


   
</div>

## Core Components

| Component | Implementation |
|---------|-------------|
| **Agent Wrapper** | Python class encapsulating LLM interaction and tool execution |
| **Tool Registry** | Dynamically loads available tools from xpander.ai SDK |
| **Session Management** | Thread-based state persistence |
| **API Integration** | Calendar, meeting services and email connectors |
| **Token Management** | Efficient token tracking and accounting |
| **Error Handling** | Graceful degradation with error recovery |

## xpander.ai - Backend for Agents

This agent is built on xpander.ai, a complete backend for agents that provides several key capabilities:

- **Managed Agent Runtime**: Deploy and run any AI agent regardless of the framework used
- **Tool Orchestration**: Comprehensive library of pre-built tools + ability to create custom tools
- **State & Memory Management**: Persistent context across agent sessions and interactions
- **Tracing & Observability**: Step-by-step execution analysis including model responses and API calls
- **Flexible Model Support**: Use any LLM provider with your own keys or xpander.ai managed options
- **A2A Communication**: Enable multiple agents to collaborate and pass context between each other

As a backend for agents, xpander.ai handles the complex infrastructure needed for production-grade agent deployment, allowing developers to focus on agent logic and behaviors rather than backend concerns.

## Quick Setup for Developers

```bash
# Clone the repository
git clone https://github.com/xpander-ai/nvidia-meeting-recorder-agent.git
cd nvidia-meeting-recorder-agent

# Set up environment
python -m venv .venv
source .venv/bin/activate  # On Windows: .venv\Scripts\activate
pip install -r requirements.txt

# Install xpander CLI
npm install -g xpander-cli

# Configure credentials
echo "XPANDER_API_KEY=your_key" > .env
echo "NVIDIA_NIM_API_KEY=your_key" >> .env
echo "XPANDER_AGENT_ID=your_id" >> .env
```

## Implementation Details

The core agent implementation is in `MeetingAgent` class which provides:

```python
class MeetingAgent:
    """Wrapper around an xpander agent backed by NVIDIA NIM."""

    MODEL = "nvidia/llama-3.1-nemotron-ultra-253b-v1"

    def __init__(self, xpander_key: str, nim_key: str, agent_id: str):
        self.client      = XpanderClient(api_key=xpander_key)
        self.agent: Agent= self.client.agents.get(agent_id=agent_id)
        self.agent.select_llm_provider(llm_provider=LLMProvider.NVIDIA_NIM)
        self.llm         = OpenAI(base_url="https://integrate.api.nvidia.com/v1",
                                  api_key=nim_key)
```

The agent executes a multi-step processing loop that:
1. Processes user input
2. Manages context (including time)
3. Generates LLM responses
4. Extracts and executes tool calls
5. Updates state and returns results

## Usage Examples

### Calendar Integration

```python
# Get upcoming meetings
result, thread_id = meeting_agent.run("List my upcoming meetings for the next 3 days")
```

### Recording Control

```python
# Start recording a specific meeting
result, thread_id = meeting_agent.run(
    "Create a recorder for the onboarding meeting",
    thread_id=thread_id
)

# Check recording status
result, thread_id = meeting_agent.run(
    "Check the recorder status and give me the asset links",
    thread_id=thread_id
)
```

### Email Delivery

```python
# Email meeting assets with summary
result, thread_id = meeting_agent.run(
    "Email the video & transcript to team@example.com with a summary",
    thread_id=thread_id
)
```

## Building on Top of This Agent

This implementation leverages key capabilities of xpander.ai as a backend for agents, making it ideal for extension:

### Development Acceleration

- **Visual Workbench**: Rapidly test and debug agent behavior through the xpander.ai Agent Workbench
- **Tool Management**: Add custom tools or use pre-built tools from the library
- **Framework Flexibility**: Switch between different LLM providers without code changes
- **State Persistence**: Thread management across agent calls handled automatically

### Production Integration

- **Multi-endpoint Triggering**: Expose agents via API, Agent-to-Agent (A2A), or communication platforms
- **Custom UI Integration**: Wrap agent with web UI, embed in existing applications, or integrate with Slack/Teams
- **Observability**: Monitor execution paths, performance metrics, and error patterns
- **Versioning & Lifecycle**: Deploy multiple versions and manage agent lifecycle

### Customization Options

1. **Additional Tools**: Extend the agent with new tools for different meeting platforms or data sources
2. **UI Development**: Build custom interfaces on top of the agent API
3. **Multi-agent Orchestration**: Connect multiple specialized agents working together
4. **Domain Adaptation**: Customize the agent for specific industries or use cases

## Development

For detailed development instructions and to access the full implementation, refer to the [Jupyter notebook](./nvidia-meeting-recorder-agent.ipynb).

## Resources

- [xpander.ai Documentation](https://docs.xpander.ai)
- [NVIDIA NIM API](https://build.nvidia.com/)
- [xpander.ai GitHub](https://github.com/xpander-ai/xpander.ai)
- [xpander.ai Backend for Agents](https://app.xpander.ai)

## 📜 License

This project uses the Xpander SDK which has its own licensing terms. Refer to the Xpander documentation for details.
