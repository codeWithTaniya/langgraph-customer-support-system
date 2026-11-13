# AI-Powered Customer Support Ticket System

An intelligent customer support workflow built using **LangGraph, LangChain, Groq LLM, and SQLite**.

This project automates customer support ticket handling by classifying queries, generating responses, reviewing response quality, and requesting human approval for billing-related issues.

## Project Overview

Customer support teams receive different types of queries every day. Handling and routing these queries manually can be time-consuming.

This project uses an AI-powered workflow to automate the process of handling customer support tickets while keeping human approval in important billing decisions.

## Key Features

- **Automatic Ticket Classification:** Classifies customer queries into Billing, Technical, and General categories.
- **Urgency Detection:** Identifies ticket urgency as High, Medium, or Low.
- **Specialized Handlers:** Uses separate handlers for billing, technical, and general queries.
- **Tool Calling:** Uses a custom `lookup_order` tool to retrieve simulated order information.
- **AI Response Generation:** Generates context-aware customer support replies.
- **AI Review System:** Reviews generated responses and provides feedback for improvement.
- **Human-in-the-Loop:** Pauses billing workflows for human approval or rejection.
- **Persistent Checkpointing:** Uses SQLite to save workflow state and support resuming interrupted workflows.

## Technologies Used

| Technology | Purpose |
|---|---|
| Python | Programming language |
| LangGraph | Workflow orchestration |
| LangChain | LLM integration and tools |
| Groq | LLM inference |
| Pydantic | Structured output validation |
| SQLite | Persistent workflow checkpointing |
| Jupyter Notebook | Development and testing |

## Workflow Architecture

1. Customer submits a support ticket.
2. Classifier identifies its category and urgency.
3. The ticket is routed to the appropriate handler.
4. The handler generates a response.
5. The AI reviewer checks the response quality.
6. If necessary, feedback is sent back for revision, with a maximum of three review attempts.
7. Billing tickets are paused for human approval.
8. Approved responses are returned to the customer.

## Project Workflow

**Customer Query → Classifier → Specialized Handler → AI Reviewer → Human Approval (Billing) → Final Response**

## Testing

The workflow has been tested using three customer query types:

### 1. General Query
Example: "What are your customer support working hours?"

- Expected category: General
- Generates a general customer support response.

### 2. Technical Query
Example: "I am unable to log in to my account. It keeps showing an incorrect password error."

- Expected category: Technical
- Generates troubleshooting instructions.

### 3. Billing Query
Example: "I was charged twice for order 1042. Please refund me."

- Expected category: Billing
- Uses the order lookup tool.
- Generates a billing response.
- Pauses for human approval before completing the workflow.

Actual code and execution outputs for these tests are included in the Jupyter Notebook.

## Installation and Setup

### 1. Clone the repository

```bash
git clone https://github.com/codeWithTaniya/langgraph-customer-support-system.git
cd langgraph-customer-support-system
```

### 2. Create a virtual environment

```bash
python -m venv myenv
```

Activate it on Windows:

```powershell
myenv\Scripts\activate
```

### 3. Install dependencies

```bash
pip install langchain langchain-core langchain-groq langgraph langgraph-checkpoint-sqlite pydantic ipykernel
```

### 4. Configure Groq API Key

Create a Groq API key and provide it when prompted by the notebook. Keep your API key private. Never upload it to GitHub.

### 5. Run the notebook

Open `mini_project.ipynb` in Jupyter Notebook or VS Code and execute the cells in order.

## Important Note

The order lookup tool currently uses simulated order information for demonstration. The project does not connect to a real payment gateway or execute actual refunds.

## Future Improvements

- Integrate a real order management database.
- Connect email or live chat support.
- Add more ticket categories.
- Integrate a real payment refund API with proper authorization.
- Build a web-based customer support dashboard.

## Author

**Taniya**

GitHub: https://github.com/codeWithTaniya

---

*Built as a practical project to explore AI agents, LangGraph workflows, tool calling, and human-in-the-loop systems.*