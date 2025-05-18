# NVIDIA Meeting Recorder Agent

<p align="center">
  <img src="https://assets.xpanderai.io/agents/agent/tamplates/meeting-recorder.png" alt="NVIDIA Meeting Recorder Agent" width="600">
</p>

<div align="center">
  <a href="https://app.xpander.ai/templates/48039a71-c99c-4691-8b66-a6faca3ccbe4" target="_blank">
    <button style="background-color:#6741d9;color:white;padding:10px 20px;font-size:14px;border:none;border-radius:8px;cursor:pointer;">
      Deploy NVIDIA Meeting Recorder to xpander.ai
    </button>
  </a>
</div>

## Overview

An autonomous AI Agent that records, transcribes, and summarizes meetings across Google Meet and Zoom. Integrated with Google Calendar, it joins scheduled calls, captures insights in real-time, and enables end-to-end meeting automation.

Never miss critical information from your meetings again. The NVIDIA Meeting Recorder Agent automates the entire meeting documentation workflow: from scheduling and recording to transcription and delivery of meeting assets via email.

This blueprint demonstrates the powerful integration between the Xpander AI platform and NVIDIA NIM microservices, providing developers with a production-ready starting point for creating intelligent meeting assistants.

## Demo

<p align="center">
  <video width="600" controls>
    <source src="https://assets.xpanderai.io/agents/agent/tamplates/meeting-recorder-demo.mp4" type="video/mp4">
    Your browser does not support the video tag.
  </video>
</p>

## Features

- 🎙️ **Automated Meeting Recording**: Seamlessly joins Google Meet and Zoom calls
- 📝 **Real-time Transcription**: Generates accurate text transcripts from meetings
- 📊 **Live Status Monitoring**: Tracks recording status in real-time
- 🧠 **Intelligent Summarization**: Creates concise meeting summaries
- 📩 **Email Delivery**: Sends meeting assets (video, transcript, summary) via email
- 📅 **Calendar Integration**: Connects with Google Calendar for meeting scheduling
- 💾 **Persistent Memory**: Maintains context across multiple interactions

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
5. Run the Jupyter notebook for a complete guide:
   ```bash
   jupyter notebook nvidia-meeting-recorder-agent.ipynb
   ```

## Quick Start

The fastest way to get started is to use our pre-built Xpander template. Just click the "Deploy to Xpander" button at the top of this README and follow the setup instructions.

## Project Structure

- `nvidia-meeting-recorder-agent.ipynb`: Complete walkthrough and implementation guide
- `requirements.txt`: Required Python dependencies

## Agent Capabilities

The Meeting Recorder Agent includes four primary tools:

1. **Calendar Integration**: Checks scheduled meetings on Google Calendar
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

## Detailed Documentation

For complete implementation details, usage examples, and customization options, refer to the [Jupyter notebook](./nvidia-meeting-recorder-agent.ipynb) included in this repository.

## Resources

- [Xpander Documentation](https://docs.xpander.ai)
- [Jupyter Notebooks](https://jupyter.org/)
- [NVIDIA NIM API](https://build.nvidia.com/)

## License

This project uses the Xpander SDK which has its own licensing terms. Refer to the Xpander documentation for details.

# nvidia-meeting-recorder-agent
