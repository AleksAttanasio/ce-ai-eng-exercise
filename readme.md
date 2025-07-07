# Client Engineering: Development Exercise
This interview focuses on building two different solutions:
1. A binary classifier system to predict the risk of heart failure using a publicly available dataset
2. A Retrieval-Augmented Generation (RAG) system using a company knowledge base dataset

You can use the AI models and providers that you are most comfortable with.

## Exercise 1 - Binary Classification
For this exercise the dataset can be found in `data/heart_failure_dataset.csv`
Additional details about the data can be found at the [following link](https://www.kaggle.com/datasets/fedesoriano/heart-failure-prediction).

The dataset contains the following columns:
1. **`Age`**: age of the patient [years]
2. **`Sex`**: sex of the patient [M: Male, F: Female]
3. **`ChestPainType`**: chest pain type [TA: Typical Angina, ATA: Atypical Angina, NAP: Non-Anginal Pain, ASY: Asymptomatic]
4. **`RestingBP`**: resting blood pressure [mm Hg]
5. **`Cholesterol`**: serum cholesterol [mm/dl]
6. **`FastingBS`**: fasting blood sugar [1: if FastingBS > 120 mg/dl, 0: otherwise]
7. **`RestingECG`**: resting electrocardiogram results [Normal: Normal, ST: having ST-T wave abnormality (T wave inversions and/or ST elevation or depression of > 0.05 mV), LVH: showing probable or definite left ventricular hypertrophy by Estes' criteria]
8. **`MaxHR`**: maximum heart rate achieved [Numeric value between 60 and 202]
9. **`ExerciseAngina`**: exercise-induced angina [Y: Yes, N: No]
10. **`Oldpeak`**: oldpeak = ST [Numeric value measured in depression]
11. **`ST_Slope`**: the slope of the peak exercise ST segment [Up: upsloping, Flat: flat, Down: downsloping]
12. **`HeartDisease`**: output class [1: heart disease, 0: Normal]

By using your preferred algorithm and model, provide a solution capable of predicting the `HeartDisease` target column 
starting from the provided features (columns from 1. to 11.)

### Expected Output
The expected outputs for this exercise are:
- Exploratory data analysis: feature distribution, correlation...
- Data preparation: clean, preprocess and, if considered valuable, enrichment of the input data 
- Modelling: choice and training of a specific model (or models)
- Evaluation: estimate of the most relevant metrics for model evaluation
- **[EXTRA]** Deploy: provide a simple API backend server to be exposed either locally or remotely

Each of the mentioned points must be motivated and described in a final document (Jupyter Notebook, presentation, report...)
that will be discussed during the next interview stage.

## Exercise 2 - RAG
### Part 1 - Data Cleaning
For this exercise the dataset can be found in `/data/rag_samples.csv` and contains IT support documentation covering topics such 
as setting up email on mobile devices, configuring VPN access, 
troubleshooting Microsoft Office issues, and other technical support scenarios.
The dataset is in csv format has 10 lines and 5 columns:
- **ki_topic** – The topic of the knowledge item (e.g., "Setting Up a Mobile Device for Company Email").
- **ki_text** – The full text of the knowledge item, usually providing instructions or explanations.
- **sample_question** – A sample user question related to the topic (e.g., "How do I set up my company email on my mobile?").
- **sample_ground_truth** – The expected response or answer to the sample question, often a concise summary or guidance.
- **sample_answer** – A response generated using AI, to be validated in exercise 4.

---

The provided knowledge base dataset contains several issues that need to be addressed to create an effective RAG system:
- Remove URL from the text samples
- Remove alphanumeric words from the text (e.g. `"Hello Maria whatsup123"`)
- Remove hashtags starting with the '#' character: (e.g.`"Mado is very good with last ball six #dhoni #six"`)
- Remove HTML Tags

Example of poisoned text to identify and remove:
```
Step 4: Verify Email Account**
http://example.com/886
#IT #http://example.com/503 #on #device #set #a
```

### Part 2 - RAG System Creation
Using the cleaned dataset, develop a simple RAG system that can effectively:
- Index and store the knowledge base articles appropriately
- Implement a retrieval mechanism that fetches relevant context based on user queries
- Create a generation component that produces helpful responses using the retrieved context
- Demonstrate how your system handles ambiguous queries that might match multiple knowledge base articles
- Implement a citation mechanism to indicate which parts of the knowledge base were used to generate the response

Provide your implementation and explain your design choices.