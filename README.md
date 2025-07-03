Learning Assistant Application

Overview

The Learning Assistant is a Python-based desktop application built using Tkinter and spaCy to help users explore and learn about various topics interactively. It provides detailed content about a user-specified topic, generates quizzes to test knowledge, and tracks learning progress. The application supports a wide range of topics through an internal knowledge base and simulates web searches for unsupported topics.

Features





Content Generation: Users can input a topic (e.g., "machine learning") and related interests to receive a detailed overview, including:





Topic description with historical context



Real-world examples



Reasons for significance



Actionable steps to learn more



Fun facts and recommendations



Quiz Generation: Creates multiple-choice quizzes based on the topic with questions covering core concepts, applications, and more.



Progress Tracking: Saves quiz results with timestamps and scores for later review.



Content Saving: Allows users to save generated content as text files and progress as JSON files.



User-Friendly Interface: A Tkinter-based GUI with input fields, buttons for generating content, taking quizzes, and managing progress, and a scrollable text area for output.

Prerequisites

To run the application, ensure the following dependencies are installed:





Python 3.x



Tkinter (usually included with Python)



spaCy (pip install spacy)



en_core_web_sm spaCy model (automatically downloaded if missing)

python -m spacy download en_core_web_sm

Installation





Clone or download the source code to your local machine.



Install the required dependencies:

pip install spacy



Ensure the en_core_web_sm spaCy model is installed (the application will attempt to download it if not present).



Run the application:

python learning_assistant.py

How to Use





Launch the Application:





Run the script to open the Tkinter GUI window titled "Learning Assistant".



Enter Inputs:





In the "Enter your learning goal or topic" field, type a topic (e.g., "biology", "quantum computing").



In the "Enter interests" field, provide comma-separated interests (e.g., "AI, robotics").



Generate Content:





Click Generate Content to display topic details in the output text area.



If the input is too vague (e.g., a single word not in the knowledge base), a warning is shown.



Take a Quiz:





Click Take Quiz to open a new window with a scrollable multiple-choice quiz based on the topic.



Select answers and click Submit Quiz to see your score, correct answers, and a recommendation.



Manage Content and Progress:





Regenerate: Refreshes content for the same topic and interests.



Clear Inputs: Resets input fields and clears the output.



Save Content: Saves the displayed content to a .txt file.



Save Progress: Saves quiz results (timestamp, topic, score) to a .json file.



Show Progress: Displays quiz history in a pop-up.



Exit: Close the application window to exit.

Code Structure





Dependencies:





tkinter: For the GUI.



spacy: For natural language processing to extract keywords and entities from user input.



subprocess, sys: For downloading the spaCy model if missing.



random, uuid, os, json, datetime: For random selection, unique file names, file handling, and progress tracking.



Knowledge Base:





A dictionary (KNOWLEDGE_BASE) with 20 predefined topics (e.g., "machine learning", "physics") containing details, examples, reasons, actions, context, fun facts, and recommendations.



Web Search Simulation:





The web_search function simulates web results for topics not in the knowledge base, returning structured data for "artificial intelligence" and "quantum computing" or generic placeholders.



Content Generation:





The generate_content function processes user input using spaCy to extract keywords and entities, matches them to the knowledge base or web search, and generates formatted markdown content.



Quiz Generation:





The generate_quiz_questions function creates eight multiple-choice questions based on the topic, covering details, examples, significance, and more.



GUI:





The LearningAssistantApp class defines the Tkinter interface with input fields, buttons, and a scrollable text area.



Methods handle content generation, quiz display, quiz evaluation, content saving, progress tracking, and input clearing.

Step-by-Step Execution





Initialization:





The application checks for the en_core_web_sm spaCy model and downloads it if missing.



The Tkinter window is initialized with a styled interface (900x600 pixels, light-themed background).



User Input:





Users enter a topic and optional interests.



The generate method validates input and calls _generate_content.



Content Generation:





The input is processed with spaCy to extract keywords and entities.



The topic is matched to the knowledge base or web search results.



A markdown-formatted string is generated with a random detail, example, reason, action, fun fact, and recommendation.



Quiz Creation:





The open_quiz_window method creates a new window with a scrollable canvas containing eight multiple-choice questions.



Questions are generated based on the topic’s details, examples, and context.



Quiz Evaluation:





The evaluate_quiz method compares user answers to correct answers, calculates the score, and stores progress with a timestamp.



A pop-up displays the score, correct/incorrect answers, a recommendation, and next steps.



Saving and Progress:





Content is saved as a .txt file with a unique name using uuid.



Progress is saved as a .json file with quiz results.



Progress can be viewed via a pop-up showing timestamps, topics, and scores.

Sample Output

Input





Topic: machine learning



Interests: AI, data science

Generated Content

# Machine Learning

**Overview**: Machine Learning is a fascinating subject focusing on neural networks. Originating in the 1950s with pioneers like Alan Turing, machine learning has grown into a cornerstone of AI, powering innovations like generative models.

**Example**: For instance, image recognition in self-driving cars. This demonstrates how neural networks impact everyday life.

**Why It Matters**: This is significant because of enabling predictive analytics.

**Get Started**: To dive deeper, try taking an online course. You can also explore connections with AI, data science.

**Fun Fact**: The first neural network, the Perceptron, was invented in 1958 and could recognize simple patterns!

**Recommendation**: Explore TensorFlow tutorials

Quiz Example





Question: What is a core component of Machine Learning?





Options: [neural networks, random concept, unrelated term, generic idea]



Correct: neural networks



Quiz Result (after submission):

Score: 6/8
Q1: ✅ Correct
Q2: ❌ Incorrect (Correct: recommendation systems)
...
**Recommendation**: Join Kaggle competitions
**Next Steps**: Try another quiz on machine learning or explore related topics: AI, data science.

Saved Progress (JSON)

[
    ["2025-07-03 23:20:00", "machine learning", 6, 8]
]

Limitations





The web_search function is a placeholder and only supports "artificial intelligence" and "quantum computing" with predefined data.



The knowledge base is limited to 20 topics; other topics rely on generic web search placeholders.



No real-time web search is implemented (e.g., no SerpAPI integration).



The quiz is static with eight questions and may repeat similar content for the same topic.

Future Improvements





Integrate a real web search API (e.g., SerpAPI) for dynamic content generation.



Expand the knowledge base with more topics and richer data.



Add adaptive quiz difficulty based on user performance.



Implement user profiles to save preferences and progress persistently.



Enhance the GUI with themes or customizable layouts.

Troubleshooting





spaCy Model Error: Ensure en_core_web_sm is installed (python -m spacy download en_core_web_sm).



No Content Generated: Check if the topic is too vague or not in the knowledge base.



File Save Error: Verify write permissions in the save directory.



Quiz Not Available: Generate content before attempting a quiz.

License

This project is open-source and available under the MIT License.
