# DATA 606 CAPSTONE PROPOSAL

## 1. Title: Fin Bot Powered by Generative AI

- Prepared for UMBC Data Science master’s degree Capstone by Dr. Chaojie (Jay) Wang
- Author name: Pooja Kangokar Pranesh
- [GitHub](https://github.com/DATA-606-2023-FALL-MONDAY/Pranesh_Pooja)
- [LinkedIn](https://www.linkedin.com/in/pooja-pranesh-507344153/)
- Powerpoint presentation - TBD
- Youtube Video - TBD 

## 2. Background

With the emerging revolutions, big companies are utilizing and adapting to the new technological changes to perform better. Similarly, the financial industry has witnessed significant transformations by integrating AI and growing NLP technologies, leading to the development of tools like financial chatbots. This bot will become a helpful resource for individuals to navigate through complexities in finance. 

The capabilities of GenAI have been increasing day by day. The latest report from McKinsey on the economic potential of genAI says that its potential impact can be seen in two important lenses i.e., it can create 60+ organizational use cases and increase labor productivity by 40% leading to revenue impacts. 

![alt text](https://www.mckinsey.com/~/media/mckinsey/business%20functions/mckinsey%20digital/our%20insights/the%20economic%20potential%20of%20generative%20ai%20the%20next%20productivity%20frontier/svgz-vivatech-full-report-rgb-exh1.svgz?cq=50&cpy=Center)

The idea of building a financial chatbot on specific or general finance areas could be a helpful bot for employees who work in financial sectors and for clients who are entirely new to this sector and want to know more.

This project matters as it provides guidance to people who want to excel in financial knowledge and who want to be financially educated. It also helps professionals to cross-verify their ideas and search for second or new paths for investment.

### Research Questions

- How can genAI handle new updates on the fin sector from time to time?
- How can financial literacy be improved among multiple demographics?
- Can this bot act as Personal finance assistance? 

## 3. Data Source

- **Data set:** [Hugging Face](https://huggingface.co/datasets/gbharti/wealth-alpaca_lora)
- **Data size:** 31.3 MB
- **Data shape:** 44,341 (rows) x 3(columns/features)
- **Data Contains the following columns:**
    - **Columns:**
        - **Output:** The expected output string 
        - **Input:** Any input instructions that can be added are specified here.
        - **Instruction:** Multiple financial scenario questions.
    - **Data Type:**
        - **Output:** String
        - **Input:** String
        - **Instructions:** String
- **Target Column:** Output
- **Main column:** All features are considered
    
- This dataset is a combination of Stanford's Alpaca (https://github.com/tatsu-lab/stanford_alpaca) and FiQA (https://sites.google.com/view/fiqa/) with another 1.3k pairs custom generated using GPT 3.5

- **Example of bot:**
    - "question": "Why are big companies like Apple or Google not included in the Dow Jones Industrial Average (DJIA) index?",
    - "answers": "That is a pretty exclusive club and for the most part they are not interested in highly volatile companies like Apple and Google. Sure, IBM is part of the DJIA, but that is about as stalwart as you can get these days. The typical profile for a DJIA stock would be one that pays fairly predictable dividends, has been around since money was invented, and are not going anywhere unless the apocalypse really happens this year. In summary, DJIA is the boring reliable company index." ," timestamp": "Sep 11 '12 at 0:53"
 
## 4. EDA

- **Data Pre-Processing & Cleaning:**
  
  - **NULL Values:** Overall Zero null values found in the dataset.
  - **Data Cleaning:** Since the data is in text format to carry out the analysis it needs to be cleaned up. The cleaning steps involve removing punctuations, stop words, and lemmatization. After these steps finally, our data is ready for EDA analysis!

- **Data Analysis:**
  
  - **EDA 1 - Sentiment Check on Output feature:**<br>
  
    <img align="middle" src="/data/Pictures/EDA1.png" alt="alt text" width="350" height="350"><br>

    The above graph shows that most of our output column content revolves between 0 and 0.25 indicating most of them have positive words. A few words are negative as well but our dataset seems to be fair as it has a very minimal negative word distribution.

  - **EDA 2 - Sentiment Check on Instruction feature:**<br>
  
    <img align="middle" src="/data/Pictures/EDA2.png" alt="alt text" width="350" height="350"><br>

    Similar to output sentiment graph the instructions feature column as well have the the neutral polarity which indicates that our data is not **Biased**

  - **EDA 3 - 100 Most common words in Output features:**<br>
  
    <img align="middle" src="/data/Pictures/EDA3.png" alt="alt text" width="350" height="350"><br>

    Looking at the graph we can say that the most commonly used words in output include money, invest, use, stock, etc

  - **EDA 4 - 100 Most common words in Instruction features:**<br>
  
    <img align="middle" src="/data/Pictures/EDA4.png" alt="alt text" width="350" height="350"><br>

    Similarly, in the instruction feature, we can see most common words are use, follow, sentence, money, etc

  - **EDA 5 - Applying Word2Vec to see most similar words learning from Model for word 'INVEST':**<br>
  
    <img align="middle" src="/data/Pictures/EDA5.png" alt="alt text" width="300" height="400"><br>

    This word2Vec table shows us that the words that the model identified similar to invest are stocksbond, low risk, diversification, etc

  - **EDA 6 - Applying Word2Vec to see most similar words learning from Model for word 'MONEY':**<br>
  
    <img align="middle" src="/data/Pictures/EDA6.png" alt="alt text" width="300" height="400"><br>

    This word2Vec table shows us that the words that the model identified similar to money are stash, cash, diversification, moneymarket etc<br>

Since the model, I am gonna build is a chatbot, it's very important to look at the data and understand if it has any biased content so that our model won't learn wrong. Looking at the analysis it is evident that the data is **unbiased** and good to move forward. The model mainly focuses on only 2 variables. In our case it is `instruction` and `output` and both look good. 

The second main analysis that I carried out was to see if the data is relevant to the finance sector and through the 100 most commonly used words I can say that **Yes** the data mostly revolves around the finance sector. 

The last analysis was to dig deeper and understand the cluster of the words the model has learned from the dataset passed. When I checked the word-vec similarity with `Invest` and `Money` words it looked good that the model is learning the cluster embeddings correctly. Proving that our dataset is good to move ahead for the analysis! 

## 5. Model Training

- **Model:**

  🚀 Falcon-7B: This is a causal decoder-only model released and built by TII. It's trained on 1500B tokens of curated corpora. This model is available for public and research purposes under the Apache 2.0 license. This model is also trained with multiple languages they are English, German, Spanish, French (and limited capabilities in Italian, Portuguese, Polish, Dutch, Romanian, Czech, Swedish); The main Falcon-7B model has been trained on the following kinds of datasets.

  <img align="middle" src="/data/Pictures/Falcon-Dataset.png" alt="alt text" width="600" height="350"><br>

  The diverse nature of base model training has been used by my code to fine-tune the model on my financial dataset.



 - **Libraries and Packages used for training:**

    This model requires "Pytorch" framework to run on. Needs at least 16B memory to swiftly run inference with Falcon-7B.

## 6. Machine Learning Models Performance Evaluation

- **Human Evaluation:**
  
  - Since the output of the bot is human-like text, I have conducted testing on ~50 questions and answers on the bot to look at the results. So far bot answers are human-understandable and match the expected answers. The bot ends the line in the middle as the length of the model has been pre-defined keeping the resource utilization in mind.
    
- **Training and Inference Time:**

  - Inference time is  highly affected by the model selected for training, dataset size, and available computational sizes. For this project, I have used open open-source falcon-7B Model for fine-tuning, with a data size of around ~ 32 MB, and used an A100 GPU to train the model. The model inference time would be fast based on the GPU configurations and the above-mentioned details. Currently model inferencing was tested on a Tesla T4 GPU which is currently turned down. The latency will be minimal if higher computational resources are provided.

- **Ethical Considerations:**
  - Model data was tested on the TextBlob model to check the sentiment of the training data, most of the training data contains words that are either neutral or positive indicating that the model wouldn't be trained on "biased" content. This model testing made sure that this LLM as been built by taking care of ethical values. 
  



    

