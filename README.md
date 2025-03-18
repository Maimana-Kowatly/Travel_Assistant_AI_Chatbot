<<<<<<< HEAD
TravelAssistAI: Chatbot for Travel Assistance and Holiday Recommendations
Part 1: Introduction
Project Background
In today’s fast-paced world, people seek quick getaways to relax, but the overwhelming number of travel options and lack of personalized advice make holiday planning difficult. TravelAssistAI was developed to solve this problem by integrating large language models with rule-based systems, providing accurate and tailored travel recommendations.

Problem Statement
Using a dataset of holiday packages (including fields such as package name, destination, duration, sightseeing options, etc.), the chatbot analyzes user preferences and suggests the most suitable holiday packages.

Dataset
The dataset was sourced from Kaggle’s traveler trip dataset:
🔗 Traveler Trip Dataset

The original dataset contains 30,000 rows, but to prevent OpenAI timeout errors, this project uses a reduced version with 4 rows.
Approach
1. Conversation & Information Gathering
The chatbot interacts naturally with users to understand their requirements.

2. Information Extraction
Once user preferences are gathered, rule-based functions process the data to match holiday packages.

3. Personalized Recommendations
The chatbot suggests tailored holiday packages and answers related queries.

System Design
The system consists of five layers:

Intent Clarity Layer – Captures user preferences through structured conversation.
Intent Confirmation Layer – Validates that all necessary information is collected.
Product Mapping Layer – Analyzes the dataset to match user requirements.
Product Information Extraction Layer – Extracts the most relevant packages.
Product Recommendation Layer – Provides tailored recommendations in a user-friendly manner.
Core Functions
1. Initializing the Conversation
initialize_conversation() – Starts the conversation using prompt engineering and chain-of-thought reasoning, ensuring the chatbot asks relevant questions until the user’s preferences are captured.

Uses Few-Shot Prompting to demonstrate ideal interactions.
2. Intent Confirmation Layer
intent_confirmation_layer() – Ensures that the chatbot captures the following user details:
✅ Destination
✅ Package Type
✅ Origin City
✅ Duration
✅ Budget

3. Dictionary Validation & Moderation
dictionary_present() – Ensures the chatbot stores user preferences as a Python dictionary.
moderation_check() – Scans for inappropriate content in user or assistant messages and terminates the conversation if necessary.
4. Product Mapping & Information Extraction
product_map_layer() – Extracts holiday features from the dataset based on defined rules.
extract_dictionary_from_string() – Converts user preferences into a structured dictionary.
compare_holiday_with_user() – Matches user preferences against the dataset and returns the top recommendations in JSON format.
5. Product Recommendation Layer
Initiates the recommendation phase.
Formats results for clear presentation.
Engages users with follow-up questions about the recommendations.
Dialogue Management System
The dialogue_mgmt_system() function orchestrates all chatbot layers, ensuring smooth and seamless user interaction.

User Interface
TravelAssistAI is built as a Flask web application, allowing users to interact with the chatbot smoothly.

Chatbot Functionalities, Challenges & Limitations
Functionalities
✅ Handles irrelevant queries beyond travel assistance.
✅ Moderates inappropriate content from users and assistant.
✅ Offers limited origin city options but allows user-entered alternatives.
✅ Responds appropriately when the provided budget is below the dataset’s minimum.

Challenges & Limitations
The chatbot may misinterpret vague queries.
Users must follow the structured conversation format for best results.
Data processing may take up to 2 minutes when fetching holiday options.
Usage & Example
Step 1: Start the Conversation
💬 Chatbot: Hello! Welcome to our holiday planning service. I'm here to help you find the perfect holiday package based on your preferences. Please share your holiday requirements with me.

Step 2: Enter Destination
🧑‍💻 User: I want to travel to Paris.

Step 3: Enter Duration
💬 Chatbot: Great choice! For how many nights would you like to visit Paris?
🧑‍💻 User: 3 nights.

Step 4: Data Processing
⏳ Important Note: The website will load for 2 minutes to fetch data. Please wait for the result.

Step 5: Display Holiday Packages
💬 Chatbot:
🔹 Summary of holiday packages (sorted by price per person):
1️⃣ Honolulu, Hawaii – Waikiki Beach, Haleakalā National Park, Nā Pali Coast – $375 per day
2️⃣ Paris, France – Notre-Dame Cathedral, Eiffel Tower, Seine River Cruise – $171 per day
3️⃣ New York, USA – Times Square, Central Park – $143 per day
4️⃣ Bali – Seminyak, Uluwatu – $225 per day
5️⃣ Rome, Italy – Rome, Venice, Vatican City – $16.67 per day
6️⃣ Sydney, Australia – Opera House, Harbour Bridge, Bondi Beach – $50 per day
7️⃣ Egypt – Giza, Alexandria, Sharm el-Sheikh Beach – $20 per day
8️⃣ London, UK – British Museum, London Eye, Tower of London – $400 per day
9️⃣ Tokyo, Japan – Shibuya Crossing, Senso-ji Temple, Meiji Shrine – $150 per day
🔟 Bangkok, Thailand – Bangkok – $285.71 per day

💬 How can I assist you further with this information?

Step 6: Request More Information
🧑‍💻 User: I want more information about number 7 Egypt.

💬 Chatbot:
🛫 Trip to Egypt (Trip ID: 34):

Destinations: Giza, Alexandria, Sharm el-Sheikh Beach
Package Type: Premium
Origin City: Barcelona, Spain
Duration: 7 Days
Accommodation Cost: $700
Transportation: Flight
Tour Guide: Sophia Lee (37, Canada)
Total Cost per Person: Not provided in the dataset.
Step 7: Ask for Accommodation Type
🧑‍💻 User: What is the accommodation type for Egypt?

💬 Chatbot: The accommodation type for Egypt is a hotel.

Important Notes
🚀 Follow the structured conversation format for the best experience.
⏳ If the chatbot takes time to respond, please wait 2 minutes while data is fetched.
❌ If the chatbot replies with "yes" or "no" unexpectedly, rephrase your query.
