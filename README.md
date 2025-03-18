# `TravelAssistAI: Chatbot for Travel Assistance and Holiday Recommendations`

## `Project Background`
In today’s fast-paced world, travelers struggle with information overload when planning vacations. `TravelAssistAI` solves this by integrating `large language models` with `rule-based systems` to provide personalized holiday recommendations.

## `Problem Statement`
Using a structured dataset of holiday packages (`package name, destination, duration, sightseeing options, etc.`), the chatbot analyzes user preferences and suggests the most suitable travel packages.

## `Dataset`
The dataset is sourced from Kaggle’s [Traveler Trip Dataset](https://www.kaggle.com/datasets/rkiattisak/traveler-trip-data). Due to processing constraints, a reduced version with `4 rows` is used.

## `Approach`

### `1. Conversation and Information Gathering`
The chatbot interacts naturally with users to collect their travel preferences.

### `2. Information Extraction`
Once preferences are gathered, a rule-based system processes the data to match relevant holiday packages.

### `3. Personalized Recommendations`
The chatbot suggests tailored holiday packages based on user input.

## `System Design`
The chatbot follows a `five-layered` architecture:

1. **Intent Clarity Layer** – Captures user preferences through structured conversation.
2. **Intent Confirmation Layer** – Ensures all necessary details are collected.
3. **Product Mapping Layer** – Matches user preferences against available packages.
4. **Product Information Extraction Layer** – Extracts relevant details from the dataset.
5. **Product Recommendation Layer** – Presents tailored holiday recommendations.

## `Core Functions`

### `1. Initializing the Conversation`
- `initialize_conversation()`: Starts the conversation with structured prompts.
- Uses `Few-Shot Prompting` to guide user interactions.

### `2. Intent Confirmation Layer`
- `intent_confirmation_layer()`: Ensures user preferences include:
  - `Destination`
  - `Package Type`
  - `Origin City`
  - `Duration`
  - `Budget`

### `3. Dictionary Validation and Moderation`
- `dictionary_present()`: Ensures user preferences are stored in a structured dictionary.
- `moderation_check()`: Scans user inputs for inappropriate content.

### `4. Product Mapping and Information Extraction`
- `product_map_layer()`: Defines matching rules for holiday packages.
- `extract_dictionary_from_string()`: Converts user inputs into a structured format.
- `compare_holiday_with_user()`: Matches preferences against available packages.

### `5. Product Recommendation Layer`
- Provides personalized recommendations.
- Formats results for clarity.
- Engages users with follow-up questions.

## `Dialogue Management System`
The `dialogue_mgmt_system()` function orchestrates interaction across different layers for a seamless experience.

---

## `User Interface`
The chatbot is deployed within a `Flask web application`, ensuring a smooth user experience.

---

## `Chatbot Functionalities, Challenges, and Limitations`

### `Functionalities`
- Responds to queries beyond travel assistance.
- Filters inappropriate content.
- Supports alternative origin cities if not in the dataset.
- Manages cases where the budget is too low.

### `Challenges and Limitations`
- `Loading Time`: The chatbot requires `2 minutes` to process and return results.
- `Limited Data`: Uses a small dataset due to API constraints.
- `Response Variation`: Users should rephrase queries if they receive unexpected responses.

---

## `Usage Example`

### `Step 1: Initial Greeting`
The chatbot introduces itself and asks for the travel destination.


### `Step 2: User Input – Destination`
User specifies a travel destination.
e.g. I want to travel to Paris.

### `Step 3: Chatbot Asks for Duration`
e.g. Great choice! For how many nights would you like to visit Paris?
### `Step 4: User Input – Number of Nights`
e.g. 3 nights


**⚠ Important:** The system will **load for 2 minutes** to process recommendations.

### `Step 5: Chatbot Lists Holiday Packages`
e.g. Here are some holiday packages sorted by price per person:

Paris, France: Eiffel Tower, Seine River Cruise – $171 per day.
Rome, Italy: Vatican City, Venice – $16.67 per day.
London, UK: British Museum, Tower of London – $400 per day. ...


### `Step 6: User Requests More Information`
I want more information about number 7 Egypt.

### `Step 7: Chatbot Provides Details`
answer:The holiday to Egypt includes visits to Giza, Alexandria, and Sharm-el-Sheikh beach. Package Type: Premium Starting from: Barcelona, Spain Duration: 7 days Accommodation: Hotel Transportation: Flight Tour Guide: Sophia Lee, 37, Canada


### `Step 8: User Queries Specific Details`
question:What is the accommodation type for Egypt?

### `Step 9: Chatbot Responds`
answer:The accommodation type for Egypt is a hotel.


---

## `Additional Notes`
- If the chatbot responds with `"yes" or "no"`, rephrase the query.
- A `demo` is included in the root 

---

## `Technology Stack`
- **Programming Language**: Python
- **Framework**: Flask
- **AI Model**: GPT-3.5-Turbo
- **Dataset Source**: Kaggle
- **Frontend**: HTML, CSS, JavaScript

---

## `License`
This project is released under the `MIT License`.

