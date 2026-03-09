# PulseAI | Intelligent Sentiment Analysis Engine 🧠✨

PulseAI is a full-stack serverless application that analyzes the emotional tone of text input. It uses a custom-weighted heuristic algorithm to determine if a statement is **Positive, Negative, or Neutral**, stores the results in a NoSQL database, and displays them through a high-performance, modern web interface.

![Version](https://img.shields.io/badge/version-1.0.0-blue)
![License](https://img.shields.io/badge/license-MIT-green)
![AWS](https://img.shields.io/badge/AWS-Lambda%20%7C%20API%20Gateway%20%7C%20DynamoDB-orange)

## 🚀 Live Architecture Flow
The application follows a modern serverless event-driven architecture:

1.  **Frontend**: A Tailwind CSS-powered UI hosted (e.g., S3/Vercel) sends a JSON payload via `POST`.
2.  **API Gateway**: Acts as the entry point, routing the request and handling CORS.
3.  **AWS Lambda**:
    *   Processes the text using a **Weighted Heuristic Engine**.
    *   Handles "Negators" (e.g., "not good") and "Intensifiers" (e.g., "extremely happy").
4.  **DynamoDB**: Persists the analysis result, timestamp, and UserID for historical tracking.
5.  **Response**: The UI receives the sentiment score and dynamically updates the "Pulse" bar and theme.

## Author
Arjun Nalge - DevOps Engineer

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-blue?logo=linkedin)](https://www.linkedin.com/in/arjun-nalge-313642398)
[![GitHub](https://img.shields.io/badge/GitHub-Follow-black?logo=github)](https://github.com/Arjun-Nalge/Arjun-Nalge.git)

```mermaid
graph LR
    A[User Browser] -->|POST Request| B(AWS API Gateway)
    B --> C[AWS Lambda]
    C -->|Analyze Sentiment| D{Heuristic Engine}
    C -->|Store Result| E[(Amazon DynamoDB)]
    D --> C
    C -->|JSON Response| B
    B -->|UI Update| A


