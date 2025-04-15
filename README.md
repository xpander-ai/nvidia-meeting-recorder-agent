# AI Meeting Recorder Agent Notebook

This Jupyter notebook demonstrates how to set up and configure an AI Meeting Recorder Agent using the Xpander SDK. The agent can record, transcribe, and summarize meetings.

## Features

- Meeting recording and transcription
- Recording status monitoring
- Email notifications
- Calendar integration

## Getting Started

1. Clone this repository
2. Create a `.env` file with your `XPANDER_API_KEY`
3. Install the required dependencies: `pip install -r requirements.txt`
4. Launch the Jupyter notebook: `jupyter notebook meeting_recorder_agent_setup.ipynb`

## Files

- `meeting_recorder_agent_setup.ipynb`: Interactive notebook for agent setup
- `generate_agent.py`: Original script version
- `agent_config.json`: Configuration of agent tools
- `requirements.txt`: Dependencies

## Notes

- The `.env` file containing your API keys is excluded from git for security
- Make sure to configure the agent with appropriate permissions in the Xpander dashboard

## Resources

- [Xpander Documentation](https://docs.xpander.ai)
- [Jupyter Notebooks](https://jupyter.org/)
