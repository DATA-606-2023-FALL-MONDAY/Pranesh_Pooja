# DATA 606 CAPSTONE PROPOSAL

## Title: Fin Bot Powered by Generative AI

- Prepared for UMBC Data Science master’s degree Capstone by Dr. Chaojie (Jay) Wang
- Author name: Pooja Kangokar Pranesh
- [GitHub](https://github.com/DATA-606-2023-FALL-MONDAY/Pranesh_Pooja)
- [LinkedIn](https://www.linkedin.com/in/pooja-pranesh-507344153/)
- Powerpoint presentation - TBD
- Youtube Video - TBD 

## Background

With the emerging revolutions, big companies are utilizing and adapting to the new technological changes to perform better. Similarly, the financial industry has witnessed significant transformations by integrating AI and growing NLP technologies, leading to the development of tools like financial chatbots. This bot will become a helpful resource for individuals to navigate through complexities in finance. 

The capabilities of GenAI have been increasing day by day. The latest report from McKinsey on the economic potential of genAI says that its potential impact can be seen in two important lenses i.e., it can create 60+ organizational use cases and increase labor productivity by 40% leading to revenue impacts. 

![alt text](https://www.mckinsey.com/~/media/mckinsey/business%20functions/mckinsey%20digital/our%20insights/the%20economic%20potential%20of%20generative%20ai%20the%20next%20productivity%20frontier/svgz-vivatech-full-report-rgb-exh1.svgz?cq=50&cpy=Center)

The idea of building a financial chatbot on specific or general finance areas could be a helpful bot for employees who work in fin sectors and for clients who are entirely new to this sector and want to know more.

## Research Questions

- How can genAI handle new updates on the fin sector time to time?
- How can financail litreacy be improved among multiple demographics?
- Can this bot act as Personal finance assistance? 

## Data Source

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

