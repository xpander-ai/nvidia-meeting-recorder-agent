# AI Meeting Recorder Agent

<p align="center">
  <img src="images/recorder.png" alt="AI Meeting Recorder" width="300">
</p>

An intelligent Jupyter notebook-based solution for automated meeting recording and transcription powered by the collaboration between Xpander AI platform and NVIDIA NIM.

xpander.ai is an AI Agent platform that accelerates developer experience for building, testing and deploying AI agents. It allows developers to design AI Agent behaviors, and invoke them with an SDK. The platform handles the complex infrastructure needed for managing thousands of AI Agent to user interactions, maintaining complex AI agent states via the state machine, and orchestrating multi-step agent workflows.

## Features

- 🎙️ **Automated Meeting Recording**: Connect to online meetings and record them automatically
- 📝 **Transcription**: Generate accurate text transcripts from recorded meetings
- 📊 **Status Monitoring**: Track recording status in real-time
- 📩 **Email Notifications**: Send meeting summaries and assets via email
- 📅 **Calendar Integration**: Seamless Google Calendar integration for meeting scheduling
- 💾 **Memory Persistence**: Maintain context across multiple interactions

## Overview

Critical and important information often gets lost quickly in meetings. The AI Meeting Recorder Agent built with xpander.ai automates the meeting documentation workflow: setting up recording in meetings, recording conversations, generating transcripts, monitoring status in real-time, and delivering assets via email.

This blueprint showcases how NVIDIA NIM microservices can be easily integrated with xpander.ai to build a powerful AI agent. Developers can use this blueprint as a starting point to incorporate NVIDIA AI into xpander workflow, or apply it to different use cases that combine xpander and NVIDIA NIM.


## Prerequisites

- Xpander Cloud account with API access
- Python 3.10+ environment
- Node.js v22.15.0+

## Getting Started

1. Clone this repository to your local machine
2. Create a `.env` file in the root directory with the following variables:
   ```
   XPANDER_API_KEY=
   NVIDIA_NIM_API_KEY=
   XPANDER_AGENT_ID=
   ```
3. Install the required dependencies:
   ```bash
   pip install -r requirements.txt
   ```
4. Install xpander CLI
   ```bash
   npm install -g xpander-cli
   ```
4. Run the `nvidia-meeting-recorder-agent.ipynb` notebook:
   ```bash
   jupyter nvidia-meeting-recorder-agent.ipynb
   ```


## Project Structure

- `nvidia-meeting-recorder-agent.ipynb`: Detailed walkthrough for setting up and executing the agent to solve example use cases.
- `images/`: Visual assets for the notebooks
- `requirements.txt`: Required Python dependencies


## Agent Capabilities

The Meeting Recorder Agent includes four primary tools:

1. **Calendar Integration**: Checks scheduled meeting on Google Calendar
2. **Create Recording Bot**: Schedules and initiates meeting recordings
3. **Check Recorder Status**: Monitors recording progress and retrieves assets
4. **Send Email**: Delivers recordings, transcripts, and summaries of the meeting via email

## Usage Examples

### List Upcoming Meetings

```python
prompt = """
Please list my upcoming meetings for the next 3 days. 
For each meeting, include the title, date, time, and participants if available.
"""
result, thread_id = meeting_agent.run(prompt=prompt)
```

### Record a Meeting

```python
prompt = """
Can you record the onboarding meeting scheduled today? 
"""
result, thread_id = meeting_agent.run(prompt=prompt, thread_id=user_thread_id)
```

### Check Recording Status

```python
prompt = """
Please check the current status of the meeting recorder bot.
"""
result, thread_id = meeting_agent.run(prompt=prompt, thread_id=user_thread_id)
```

## Resources

- [Xpander Documentation](https://docs.xpander.ai)
- [Jupyter Notebooks](https://jupyter.org/)
- [NVIDIA NIM API](https://build.nvidia.com/)

## License

This project uses the Xpander SDK which has its own licensing terms. Refer to the Xpander documentation for details.

# nvidia-meeting-recorder-agent
