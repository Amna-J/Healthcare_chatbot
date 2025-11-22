HealthChatBot 
Link: https://anarthrously-unsated-claud.ngrok-free.dev/
This project develops a friendly, rule-based medical assistant chatbot deployed via a simple web interface using Flask and exposed publicly using Pyngrok.

The bot's core functionality is powered by the OpenAI GPT-3.5-Turbo model, guided by a strict system prompt to ensure safe, general, and non-diagnostic health-related interactions.

🚀 Key Features
Rule-Based AI: Uses a strict system prompt to define the bot's persona and limitations.

Safety Guards: Explicitly programmed to refuse medical diagnoses, medication advice, and non-health-related inquiries.

Web Interface: A simple, modern chat UI built with Flask and HTML/CSS/JavaScript for easy interaction.

Cloud Deployment: Utilizes Pyngrok to create a secure public URL, making the chatbot accessible outside the Colab environment.

🛠️ Technologies & Dependencies
This project relies on the following Python libraries:

flask: The web framework used to create the server and handle API requests.

openai: The official SDK used to communicate with the GPT-3.5-turbo model.

pyngrok: Used to tunnel the local Flask port (5000) to a public URL for external access.

🧠 Chatbot Logic (System Prompt)
The bot's personality and safety limitations are enforced by the following system instructions:

Role: Friendly medical assistant.

Safety Rules (Strict Refusals):

Do NOT give medical diagnoses.

Do NOT recommend medicine names or doses.

Do NOT give emergency instructions.

Handling Serious Issues: If a question requires a doctor, the bot responds with: "I am not able to give medical advice. Please consult a doctor."

Handling Off-Topic Questions: If a question is not medical, the bot responds with: "I can only answer medical or health-related questions. Please ask a medical question."

⚙️ Setup and Execution
This notebook is designed to run directly in a Google Colaboratory environment.

Prerequisites
You need a valid OpenAI API Key and an ngrok Auth Token set up in the notebook environment.

Notebook Steps
Install Dependencies:

Python

!pip install flask openai pyngrok
Set API Keys: The notebook sets the OPENAI_API_KEY and configures the pyngrok auth token.

Define LLM Function: The ask_llm function is defined, incorporating the strict SYSTEM_PROMPT to guide the AI's behavior.

Define Web Interface: The HTML template for the chat interface is defined, including client-side JavaScript to send messages via AJAX.

Define Flask Endpoints:

/: Serves the HTML chat interface.

/chat (POST): Receives the user's message, passes it to the ask_llm function, and returns the AI's response.

Run Server and Ngrok:

Python

ngrok.kill()
public_url = ngrok.connect(5000)
print("Public URL:", public_url)
app.run(port=5000)
This step starts the Flask application and provides a publicly accessible URL for testing the chatbot.
