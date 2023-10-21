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

  - **EDA 5 - Applying Word2Vec to see most similar words learning from Model:**<br>
  
    <img align="middle" src="/data/Pictures/EDA5.png" alt="alt text" width="350" height="350"><br>

    This word2Vec graph shows us that the words that the model identified similar to invest are stocksbond, low risk, diversification, etc

  - **EDA 6 - Applying Word2Vec to see most similar words learning from Model:**<br>
  
    <img align="middle" src="/data/Pictures/EDA6.png" alt="alt text" width="350" height="350"><br>

    This word2Vec graph shows us that the words that the model identified similar to money are stash, cash, diversification, moneymarket etc<br>

Since the model, I am gonna build is a chatbot, it's very important to look at the data and understand if it has any biased content so that our model won't learn wrong. Looking at the analysis it is evident that the data is **unbiased** and good to move forward. The model mainly focuses on only 2 variables. In our case it is `instruction` and `output` and both look good. 

The second main analysis that I carried out was to see if the data is relevant to the finance sector and through the 100 most commonly used words I can say that **Yes** the data mostly revolves around the finance sector. 

The last analysis was to dig deeper and understand the cluster of the words the model has learned from the dataset passed. When I checked the word-vec similarity with `Invest` and `Money` words it looked good that the model is learning the cluster embeddings correctly. Proving that our dataset is good to move ahead for the analysis! 

    

