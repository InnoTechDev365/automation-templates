🤖 AI Personal Planner (n8n Ecosystem)
This is a modular system for creating a personal assistant in Telegram that doesn't just "chat," but actually manages your schedule. It integrates Google Calendar for meetings and Todoist for tasks, understands voice messages, and can provide a morning briefing.

✨ What this template can do
Voice control: Send the bot a "voice message," and it will transcribe it via OpenAI Whisper, and then create a task or event.

Smart Management: Thanks to the AI Agent, the system itself decides where to send the information—to the calendar or to the to-do list.

Morning summaries: The bot automatically checks both services and sends a motivating message with a plan for the day.

Full CRUD cycle: You can create, retrieve, update, and delete events and tasks directly from the chat.

🏗 Project Structure
The system is divided into three logical blocks for easy scaling:

Main.json (Brain): Receives messages from Telegram, manages dialogue memory, and coordinates the work of other workflows.

Calendar.json (Tool): Isolated logic for working with the Google Calendar API.

Todoist.json (Tool): Isolated logic for working with the Todoist API.

🚀 How to launch
1. Preparation in n8n
Import all three .json files into your n8n.

Create (or select existing) Credentials:

Telegram API (via @BotFather).

OpenAI API (for GPT and Whisper).

Google Calendar OAuth2.

Todoist OAuth2.

2. Workflow Linking
Since workflow IDs change upon import, they need to be "re-linked":

Open the Main workflow.

Find the Google Calendar and Todoist nodes (Workflow Tool type).

In the Workflow ID field, select the corresponding imported scenarios from the drop-down list.

3. Time zone setting
The system prompts of the agents specify the Asia/Jerusalem time zone. If you are in a different zone (for example, Europe/Moscow), replace it in the AI Agent nodes in all three files so that the bot correctly understands phrases like "tomorrow at 10 am."

🛠 Technology stack
n8n (LangChain integration)

LLM: GPT-4o / GPT-4-mini

Speech-to-Text: OpenAI Whisper

Memory: Window Buffer Memory

📝 Personal note
I created this template to free up my head. Instead of opening two apps, I just record a short audio on the go. I would be glad if this tool helps you become a little more productive too!

Important: The files have been cleared of personal API keys but contain technical IDs and example requests in Pin Data for testing.







