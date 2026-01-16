# AI-Based Citizen Grievance Intelligence Platform

A production-ready MERN stack application with a microservice architecture for automated grievance processing.

## 🏗️ Architecture

- **Frontend**: React (Vite), Tailwind CSS, Chart.js
- **Backend**: Node.js, Express.js, MongoDB
- **AI Service**: Python (FastAPI) [Microservice]

The system serves as an intelligent bridge between citizens and the government. It takes a complaint text, uses AI to categorize it and assign priority, and then routes it to the specific government department (e.g., PWD, PHED, Police).

## 🚀 Getting Started

### Prerequisites

1.  **Node.js** (v18+)
2.  **Python** (v3.9+)
3.  **MongoDB Atlas** (URI is pre-configured in this build, but you should use your own for production).

### Installation (One-Shot)

Run the following command from the root directory to install dependencies for all 3 services:

```bash
npm install
npm run setup
```

*Note: You also need to install Python dependencies manually if not using a system package manager that handles it automatically.*

```bash
cd ml-server
pip install -r requirements.txt
cd ..
```

### Running the Application

To start all services (Frontend, Backend, AI Server) simultaneously:

```bash
npm run dev
```

- **Frontend**: [http://localhost:5173](http://localhost:5173)
- **Backend API**: [http://localhost:5000](http://localhost:5000)
- **AI Service**: [http://localhost:8000](http://localhost:8000)

## 🧪 Testing

1.  Open the Frontend at `http://localhost:5173`.
2.  Enter a complaint (e.g., "There is a massive pothole in the main road causing accidents").
3.  Select a District.
4.  Click **Submit**.
5.  Watch as the AI automatically classifies it as **Roads & Bridges**, sets priority to **High/Critical**, and assigns it to **PWD**.
6.  Go to the **Dashboard** to see the analytics update in real-time.

## 🤖 Replacing Dummy AI with Real Models

Currently, `/ml-server/main.py` uses keyword matching and rules. To upgrade to a Transformer model (HuggingFace):

1.  Open `ml-server/main.py`.
2.  Import `transformers`.
3.  Load a model like `facebook/bart-large-mnli` (Zero-Shot Classification).
4.  Replace the `predict_category` function to use the model's output.
5.  The API contract (`/predict` input/output) is already designed to support this swap without changing the Frontend or Node Backend.
