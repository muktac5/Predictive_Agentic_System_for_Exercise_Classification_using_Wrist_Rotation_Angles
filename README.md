##Predictive Agentic System for Exercise Recognition

This project involves developing a predictive system to classify exercise types based on Euler angles derived from motion data. The system leverages time-series data and machine learning techniques to identify specific exercises and enhance exercise descriptions using domain-specific knowledge.

Project Overview:

Objective
The goal of this project is to create a system that accurately predicts the type of exercise based on rotation and Euler angles while addressing outliers and variations in exercise performance. The project also includes enhancements for generating personalized exercise advice based on user profiles using large language models (LLMs).

Data Understanding -
Data Processing: Focused on the progression of data during each exercise rep, with specific attention to handling rotational matrices and Euler angles.
Outlier Detection: Z-scores were used to detect outliers, particularly in the hammercurl exercise, where unrealistic rotations along the x-axis were observed.
Feature Engineering: Euler angles were transformed using sine/cosine functions to scale rotational values appropriately.

Model Architecture -
Initial Approach: Started by training on a single exercise (arm raise) to understand feature correlations and physical implications of Euler angles.
LSTM Model: A Long Short-Term Memory (LSTM) network was chosen for time-series prediction, achieving an initial validation accuracy of 74.75%.
Feature Enhancements: The inclusion of Euler angle derivatives improved the model’s performance, resulting in a final validation accuracy of 97.7%.

Predictive Modeling -
The model predicts exercise types by considering Euler angles and their rate of change, while adjusting for variations in user performance (e.g., weight differences, body composition).
Noise was introduced in testing, and a threshold-based softmax probability mechanism was added to classify uncertain predictions as "other."

Knowledge Base and Persona Integration -
Exercise Knowledge Base: A simple Retrieval-Augmented Generation (RAG) setup was created using a gym dataset containing exercise descriptions, types, targeted body parts, and required equipment.
User Personalization: Random user profiles (age, ailment, interests, goals) were generated, and personas were defined for the predictive system to respond in contextually appropriate ways (e.g., as a doctor or fitness coach).
LLM Integration: Different personas were created using a mini GPT-4 model to give customized exercise advice. Responses were generated based on exercise descriptions, user goals, and personas (e.g., orthopedic doctor, fitness coach).

System Features -
Exercise Classification: Predicts exercise type based on input features like Euler angles, rotation, and rep count.
Outlier Detection: Uses a Z-score to identify unrealistic rotations and corrects them with sine/cosine transformations.
Enhanced Feature Engineering: Adds derivatives of Euler angles to improve the prediction accuracy.
Noise Handling: Handles noisy data and predicts uncertain exercises as "other."
Exercise Knowledge Base: Provides descriptions of exercises using a domain-specific gym dataset.
Personalized Responses: Generates personalized exercise recommendations based on user profiles using LLM personas.

Future Enhancements -
Dynamic Input Handling: Building a function to accept live input data (e.g., rep count, Euler angles) and process it for real-time predictions.
Noisy Data Exploration: Investigating how real-world factors like inconsistent movement affect predictions and how to refine the system’s accuracy.
User Interface Development: Creating a simple user interface (UI) with Streamlit for easy interaction and application deployment.
