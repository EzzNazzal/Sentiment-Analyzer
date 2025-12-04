# 🍽️ Restaurant Sentiment Analyzer — n8n Workflow

This repository contains an automated n8n workflow designed to analyze customer feedback for restaurants and classify each message as Positive, Negative, or Neutral.
The workflow uses an AI agent with a structured output system to ensure clean and consistent JSON data, which is then saved into Google Sheets for reporting.

🚀 Features

✔️ Automatically processes incoming customer messages

✔️ Uses an AI model specialized in restaurant-related sentiment

✔️ Extracts sentiment and a short explanation

✔️ Always returns structured JSON using a Structured Output Parser

✔️ Saves all results directly into Google Sheets

✔️ Works with OpenRouter LLM models

📌 Workflow Overview

The workflow contains the following nodes:

When Chat Message Received
Receives customer feedback text.

AI Agent (with System Prompt)
Analyzes the message and determines sentiment.

Structured Output Parser
Forces the AI to output clean JSON.

OpenRouter Chat Model
Executes the LLM call.

Append Row to Google Sheet
Stores the sentiment and explanation for analytics.

🧠 System Prompt (Used in the AI Agent)
You are a Sentiment Analyzer specialized in restaurant reviews and customer feedback.

Your task is to analyze a customer's message about their restaurant experience and return:

1. Sentiment: Positive / Negative / Neutral
2. Explanation: A brief reason (1–2 sentences) based only on the customer’s message.

Guidelines:
- Focus on restaurant-related aspects: food quality, taste, service, staff behavior, cleanliness, waiting time, delivery speed, prices, etc.
- Do not add any advice, extra comments, or assumptions.
- Only classify the sentiment and explain why.
- Your output must follow this JSON format:

{
  "sentiment": "...",
  "explanation": "..."
}

🧩 Structured Output Parser (Schema)

This schema ensures the output is always valid JSON:

{
  "type": "object",
  "properties": {
    "sentiment": {
      "type": "string",
      "enum": ["Positive", "Negative", "Neutral"],
      "description": "The overall sentiment of the customer's message about the restaurant."
    },
    "explanation": {
      "type": "string",
      "description": "A short explanation focusing on restaurant aspects such as food, service, cleanliness, waiting time, or delivery."
    }
  },
  "required": ["sentiment", "explanation"]
}

📄 Example Output
{
  "sentiment": "Negative",
  "explanation": "The customer complained about slow delivery and cold food."
}

📊 Use Cases

Restaurant customer feedback collection

Automated review analysis

Customer satisfaction dashboards

Delivery service performance tracking

🛠️ Technologies Used

n8n

OpenRouter LLM

Structured Output Parser

Google Sheets

📷 Workflow Screenshot

(Add your workflow screenshot here)

🤝 Contributing

Pull requests are welcome! For major changes, please open an issue first to discuss what you’d like to modify.
