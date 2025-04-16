# AI Meeting Recorder Agent

<p align="center">
  <img src="images/recorder.png" alt="AI Meeting Recorder" width="300">
</p>

An intelligent Jupyter notebook-based solution for automated meeting recording, transcription, and summarization powered by the Xpander AI platform.

## Features

- 🎙️ **Automated Meeting Recording**: Connect to online meetings and record them automatically
- 📝 **Transcription**: Generate accurate text transcripts from recorded meetings
- 📊 **Status Monitoring**: Track recording status in real-time
- 📩 **Email Notifications**: Send meeting summaries and assets via email
- 📅 **Calendar Integration**: Seamless Google Calendar integration for meeting scheduling
- 💾 **Memory Persistence**: Maintain context across multiple interactions

## Prerequisites

- Xpander Cloud account with API access
- Python 3.10+ environment
- Google Calendar API access (for calendar integration)

## Getting Started

1. Clone this repository to your local machine
2. Create a `.env` file in the root directory with the following:
   ```
   XPANDER_API_KEY=your_xpander_api_key
   OPENAI_API_KEY=your_openai_api_key
   ```
3. Install the required dependencies:
   ```bash
   pip install -r requirements.txt
   ```
4. Launch the welcome notebook:
   ```bash
   jupyter notebook welcome.ipynb
   ```

## Project Structure

- `welcome.ipynb`: Introduction to the project with visual overview
- `step1-create-agent.ipynb`: Detailed walkthrough for configuring the agent
- `step2-execute-agent.ipynb`: Examples of running the agent and accessing recordings
- `agent_config.json`: Configuration file defining agent tools and capabilities
- `images/`: Visual assets for the notebooks
- `requirements.txt`: Required Python dependencies

## Agent Capabilities

The Meeting Recorder Agent includes four primary tools:

1. **Create Recording Bot**: Schedules and initiates meeting recordings
2. **Check Recorder Status**: Monitors recording progress and retrieves assets
3. **Send Email**: Delivers recordings, transcripts, and summaries via email
4. **Calendar Integration**: Creates and manages calendar events

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
Can you record all the meetings scheduled for today?
"""
result, thread_id = meeting_agent.run(prompt=prompt, thread_id=user_thread_id)
```

### Check Recording Status

```python
prompt = """
Check the status of the meeting recorder I just created for today's meeting.
"""
result, thread_id = meeting_agent.run(prompt=prompt, thread_id=user_thread_id)
```

## Resources

- [Xpander Documentation](https://docs.xpander.ai)
- [Jupyter Notebooks](https://jupyter.org/)
- [OpenAI API](https://platform.openai.com/)

## License

This project uses the Xpander SDK which has its own licensing terms. Refer to the Xpander documentation for details.
# nvidia-meeting-recorder-agent
