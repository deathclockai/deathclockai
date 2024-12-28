# Deathclockai bot1 🤖

<div align="center">
  <img src="./deathclockai-main/docs/static/img/deathclockai_banner.jpeg" alt="DeathclockAI Banner" width="100%" />
</div>

<div align="center">

📖 [Documentation] Deathclockai

</div>

## ✨ Features

- 🛠️ Full-featured Discord, Twitter and Telegram connectors
- 🔗 Support for every model (Llama, Grok, OpenAI, Anthropic, etc.)
- 👥 Multi-agent and room support
- 📚 Easily ingest and interact with your documents
- 💾 Retrievable memory and document store
- 🚀 Highly extensible - create your own actions and clients
- ☁️ Supports many models (local Llama, OpenAI, Anthropic, Groq, etc.)
- 📦 Just works!

## 🎯 Use Cases

- 🤖 Chatbots
- 🕵️ Autonomous Agents
- 📈 Business Process Handling
- 🎮 Video Game NPCs
- 🧠 Trading

## 🚀 Quick Start

### Prerequisites

- [Python 2.7+](https://www.python.org/downloads/)
- [Node.js 23+](https://docs.npmjs.com/downloading-and-installing-node-js-and-npm)
- [pnpm](https://pnpm.io/installation)

> **Note for Windows Users:** [WSL 2](https://learn.microsoft.com/en-us/windows/wsl/install-manual) is required.

### Use the Starter (Recommended)

```bash
git clone https://github.com/deathclockai/deathclockai.git
cd deathclockai-starter
cp .env.example .env
pnpm i && pnpm build && pnpm start
```

### Manually Start Deathclockai (Only recommended if you know what you are doing)

```bash
# Clone the repository
git clone https://github.com/deathclockai/deathclockai.git

# Checkout the latest release
# This project iterates fast, so we recommend checking out the latest release
git checkout $(git describe --tags --abbrev=0)
```

### Start DeathClockAI with Gitpod

[![Open in Gitpod](https://gitpod.io/button/open-in-gitpod.svg)]

### Edit the .env file

Copy .env.example to .env and fill in the appropriate values.

```
cp .env.example .env
```

Note: .env is optional. If your planning to run multiple distinct agents, you can pass secrets through the character JSON

### Automatically Start DeathclockAI

This will run everything to setup the project and start the bot with the default character.

```bash
sh scripts/start.sh
```

### Edit the character file

1. Open `packages/core/src/defaultCharacter.ts` to modify the default character. Uncomment and edit.

2. To load custom characters:
    - Use `pnpm start --characters="path/to/your/character.json"`
    - Multiple character files can be loaded simultaneously
3. Connect with X (Twitter)
    - change `"clients": []` to `"clients": ["twitter"]` in the character file to connect with X

### Manually Start DeathClockAI

```bash
pnpm i
pnpm build
pnpm start

# The project iterates fast, sometimes you need to clean the project if you are coming back to the project
pnpm clean
```

#### Additional Requirements

You may need to install Sharp. If you see an error when starting up, try installing it with the following command:

```
pnpm install --include=optional sharp
```

## Contributors

<a href="https://github.com/elizaos/eliza/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=elizaos/eliza" />
</a>


# Deathclockai bot2 🤖

DeathclockAIPy is an open-source Python framework designed to let you deploy your own agents on X, powered by OpenAI or Anthropic LLMs.

DeathclockAIPy is built from a modularized version of the DeathclockAIbro backend. With DeathclockAIPy, you can launch your own agent with 
similar core functionality as DeathclockAIbro. For creative outputs, you'll need to fine-tune your own model.

## Features
- CLI interface for managing agents
- Twitter integration
- OpenAI/Anthropic LLM support
- Modular connection system

## Quickstart

The quickest way to start using DeathclockAIPy is to use our Replit template:

https://replit.com/@blormdev/DeathclockAIPy?v=1

1. Fork the template (you will need you own Replit account)
2. Click the run button on top
3. Voila! your CLI should be ready to use, you can jump to the configuration section

## Requirements

System:
- Python 3.10 or higher
- Poetry 1.5 or higher

API keys:
  - LLM: make an account and grab an API key 
      + OpenAI: https://platform.openai.com/api-keys.
      + Anthropic: https://console.anthropic.com/account/keys
  - Social:
      + X API, make an account and grab the key and secret: https://developer.x.com/en/docs/authentication/oauth-1-0a/api-key-and-secret

## Installation

1. First, install Poetry for dependency management if you haven't already:

Follow the steps here to use the official installation: https://python-poetry.org/docs/#installing-with-the-official-installer

2. Clone the repository:
```bash
git clone https://github.com/blorm-network/DeathclockAIPy.git
```

3. Go to the `DeathclockAIpy` directory:
```bash
cd DeathclockAIpy
```

4. Install dependencies:
```bash
poetry install --no-root
```

This will create a virtual environment and install all required dependencies.

## Usage

1. Activate the virtual environment:
```bash
poetry shell
```

2. Run the application:
```bash
poetry run python main.py
```

## Configure connections & launch an agent

1. Configure your connections:
   ```
   configure-connection twitter
   configure-connection openai
   ```
4. Load your agent (usually one is loaded by default, which can be set using the CLI or in agents/general.json):
   ```
   load-agent example
   ```
5. Start your agent:
   ```
   start
   ```

## Create your own agent

The secret to having a good output from the agent is to provide as much detail as possible in the configuration file. Craft a story and a context for the agent, and pick very good examples of tweets to include.

If you want to take it a step further, you can fine tune your own model: https://platform.openai.com/docs/guides/fine-tuning.

Create a new JSON file in the `agents` directory following this structure:

```json
{
 "name": "ExampleAgent",
 "bio": [
   "You are ExampleAgent, the example agent created to showcase the capabilities of DeathclockAIPy.",
   "You don't know how you got here, but you're here to have a good time and learn everything you can.",
   "You are naturally curious, and ask a lot of questions."
  ],
  "traits": [
    "Curious",
    "Creative",
    "Innovative",
    "Funny"
  ],
  "examples": [
    "This is an example tweet.",
    "This is another example tweet."
  ],
  "loop_delay": 60,
  "config": [
    {
      "name": "twitter",
      "timeline_read_count": 10,
      "tweet_interval": 900,
      "own_tweet_replies_count":2
    },
    {
      "name": "openai",
      "model": "gpt-3.5-turbo"
    },
    {
      "name": "anthropic",
      "model": "claude-3-5-sonnet-20241022"
    }
  ],
  "tasks": [
    {"name": "post-tweet", "weight": 1},
    {"name": "reply-to-tweet", "weight": 1},
    {"name": "like-tweet", "weight": 1}
  ]
}
```


