
# AI Career Chatbot

An AI-powered career assistant that represents me on a personal website. Visitors can ask about my background, skills, and experience, and the bot answers in character using my LinkedIn profile and a written summary.

## Live Demo

Try the chatbot here: [Career Conversation](https://huggingface.co/spaces/Sushil2k4/career_conversation)


## Features

Built as part of the LLM Engineering course (Week 1 — Foundations).
- In-character chat that answers career questions as Sushil Kumar Mishra
- Context from `me/linkedin.pdf` and `me/summary.txt`
- OpenAI tool calling for actions during conversation
- Lead capture when a visitor wants to get in touch
- Unknown question logging when the bot cannot answer
- Push notifications via Pushover
- Live deployment on Hugging Face Spaces (demo available on request)

## Tech Stack

- Python
- OpenAI API (gpt-4o-mini)
- Gradio
- Pushover
- Hugging Face Spaces

## How It Works

1. On startup, the app reads my LinkedIn PDF and summary text.
2. A system prompt instructs the model to act as me and stay professional.
3. When a user chats, the model responds using that context.
4. If the user shares an email or asks something unanswerable, the model calls tools:
   - `record_user_details` — saves contact info and sends a Pushover alert
   - `record_unknown_question` — logs the question and notifies me

## Project Structure

```text
.
├── app.py
├── requirements.txt
├── me/
│   ├── linkedin.pdf
│   └── summary.txt
└── README.md
```

## Run Locally

**1. Clone the repo**

```bash
git clone https://github.com/Sushil2k4/career-chatbot.git
cd career-chatbot
```

**2. Install dependencies**

```bash
pip install -r requirements.txt
```

**3. Create a `.env` file**

```env
OPENAI_API_KEY=your_openai_key_here
PUSHOVER_USER=your_pushover_user_here
PUSHOVER_TOKEN=your_pushover_token_here
```

Do not commit `.env` to GitHub.

**4. Run the app**

```bash
python app.py
```

Open the URL shown in the terminal (usually http://127.0.0.1:7860).

## Deploy to Hugging Face

1. Create a Hugging Face account and run `hf auth login`.
2. From the project folder, run `gradio deploy`.
3. In Space Settings, add these secrets:
   - `OPENAI_API_KEY`
   - `PUSHOVER_USER`
   - `PUSHOVER_TOKEN`

## Update Profile Content

1. Edit `me/linkedin.pdf` and/or `me/summary.txt`.
2. Run `gradio deploy` again to update the live Space.

## Author

**Sushil Kumar Mishra**

Software Developer · CSE @ SRM IST · Chennai
