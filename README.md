# Sentiment Analysis Backend

This repository contains a simple **Flask-based API** that performs **sentiment analysis** using the **Hugging Face transformers** library. The API allows users to submit text (e.g., product reviews) and receive sentiment analysis results indicating whether the sentiment is **positive**, **negative**, or **neutral**.

## Table of Contents
1. [Requirements](#requirements)
2. [Setup Instructions](#setup-instructions)
3. [API Documentation](#api-documentation)
4. [Testing the API](#testing-the-api)
5. [Troubleshooting](#troubleshooting)
6. [Deactivating Virtual Environment](#deactivating-virtual-environment)

---

## Requirements

Before setting up this project, ensure you have the following installed:

- **Python 3.8+**: Ensure that Python is installed on your machine.
- **Pip**: Python's package installer, used to install the project dependencies.
- **Git**: To clone the repository.

You can download Python from [here](https://www.python.org/downloads/) if it's not already installed.

---

## Setup Instructions

Follow these steps to set up the sentiment analysis backend on your local machine:

### Step 1: Clone the Repository

1. Clone this repository to your local machine:
   ```bash
   git clone https://github.com/your-username/sentiment-analysis-backend.git
   ```

   Replace `your-username` with your GitHub username.

2. Navigate into the project directory:
   ```bash
   cd sentiment-analysis-backend
   ```

### Step 2: Set Up a Virtual Environment (Optional but Recommended)

Creating a virtual environment helps avoid conflicts with other projects or system-wide Python installations.

1. Create a virtual environment:
   ```bash
   python -m venv venv
   ```

2. Activate the virtual environment:

   **On Windows:**
   ```bash
   venv\Scripts\activate
   ```

   **On macOS/Linux:**
   ```bash
   source venv/bin/activate
   ```

### Step 3: Install Dependencies

Install the required Python libraries using the provided `requirements.txt` file:

```bash
pip install -r requirements.txt
```

This will install:
- **Flask**: A lightweight Python web framework to build the API.
- **transformers**: The Hugging Face library for the sentiment analysis model.
- **torch**: Required for running the transformer models.

---

## API Documentation

### POST /analyze

**Description:** This endpoint analyzes the sentiment of the provided text.

**Request body (JSON format):**
```json
{
  "text": "I absolutely love this product! It's amazing."
}
```

**Response:**
```json
[
  {
    "label": "POSITIVE",
    "score": 0.9998760228157043
  }
]
```

**Explanation:**
- The `label` field indicates the sentiment: `POSITIVE`, `NEGATIVE`, or `NEUTRAL`.
- The `score` field shows the confidence score of the sentiment classification.

---

## Testing the API

### Step 1: Run the Flask App

Once you have installed the dependencies, run the Flask app:

```bash
python app.py
```

The server will start and will be accessible at `http://127.0.0.1:5000/`.

### Step 2: Send a Test Request

You can test the API using tools like **Postman**, **curl**, or directly from your frontend.

**Using curl:**
```bash
curl -X POST http://127.0.0.1:5000/analyze \
  -H "Content-Type: application/json" \
  -d '{"text": "I absolutely love this product! It'\''s amazing."}'
```

**Expected Response:**
```json
[
  {
    "label": "POSITIVE",
    "score": 0.9998760228157043
  }
]
```

### Step 3: Handling Errors

If the `text` field is missing in the request, the API will return an error:

```json
{
  "error": "No text provided"
}
```

---

## Troubleshooting

### 1. Error: Could not find the model "distilbert-base-uncased-finetuned-sst-2-english"

This indicates that the model hasn't been downloaded properly. Ensure you have an active internet connection, as the `transformers` library will download the model the first time it runs.

### 2. Error: Port 5000 is already in use

If port 5000 is already in use, you can change the port number by modifying the `app.run()` line in `app.py`:

```python
app.run(debug=True, port=5001)
```

### 3. Error: ModuleNotFoundError

If you encounter a `ModuleNotFoundError`, make sure all dependencies are installed correctly using:

```bash
pip install -r requirements.txt
```

---

## Deactivating Virtual Environment

After you're done working on the project, you can deactivate the virtual environment:

```bash
deactivate
```

---

## Conclusion

This API provides a straightforward way to integrate sentiment analysis into your web application. You can easily test the backend and use it to build your frontend for Task 3. If you encounter any issues, refer to the troubleshooting section or reach out for further assistance.