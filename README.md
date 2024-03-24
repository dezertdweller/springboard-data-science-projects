# API Mini Project

## Course: Unit 7 Module 2: Data Collection

Description: This mini project is part of my Springboard Data Science curriculum. The exercise will require that I extract data from Nasdaq using an API and then answer a few questions about the data. For this mini project, I will focus on equities data from the Frankfurt Stock Exhange (FSE), which is available for free. I'll analyze the stock prices of a company called Carl Zeiss Meditec, which manufactures tools for eye examinations, as well as medical lasers for laser eye surgery: [company website](https://www.zeiss.com/meditec/int/home.html). The company is listed under the stock ticker AFX_X.

### Requirements
You will need to register an account with NASDAQ at [https://data.nasdaq.com/institutional-investors] and keep the unique API key. Create a .env file for this project and save the API key there. There are detailed instructions for the NASDAQ API [here](https://docs.data.nasdaq.com/docs/in-depth-usage).

### Instructions
We were asked to analyze the data without using pandas. I found this challenging to start so I went ahead and created a dataframe from the JSON data. Afterwards, I revisited the challenges without using pandas with ChatGPT's guidance. 

### Analysis Questions to Answer
1. Calculate what the highest and lowest opening prices were for the stock in this period.
2. What was the largest change in any one day (based on High and Low price)?
3. What was the largest change between any two days (based on Closing Price)?
4. What was the average daily trading volume during this year?
5. What was the median trading volume during this year. (Note: you may need to implement your own function for calculating the median.)
