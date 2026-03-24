---
layout: post
title: chat-with-your-database-using-langchain-and-gpt-4
date: 2025-07-09
url_wayback_machine: https://web.archive.org/web/20250709225418/https://www.quantmetry.com/blog/chat-with-your-database-using-langchain-and-gpt-4/
---
NLP 

15/07/2024 

#  Chat with your database using LangChain and GPT-4 

[ ](https://www.linkedin.com/sharing/share-offsite/?url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fchat-with-your-database-using-langchain-and-gpt-4%2F "Linkedin") [ ](https://twitter.com/intent/tweet?text=Chat%20with%20your%20database%20using%20LangChain%20and%20GPT-4&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fchat-with-your-database-using-langchain-and-gpt-4%2F "Twitter") [ ](https://www.quantmetry.com/blog/chat-with-your-database-using-langchain-and-gpt-4/ "Email") [ ](https://www.quantmetry.com/blog/chat-with-your-database-using-langchain-and-gpt-4/ "Copy Link")

* * *

Auteurs : [ Lucas ISCOVICI ](https://www.linkedin.com/in/lucas-iscovici/) , [ Oussama MOUSTAINE ](https://www.linkedin.com/in/oussama-moustaine-67a183155/)

Temps de lecture : 41 minutes 

![Quantmetry.com : Chat with your database using LangChain and GPT-4](https://www.quantmetry.com/wp-content/uploads/2023/10/749fc9af-2702-4e87-93b4-77bd61f87793.jpeg)

##  Table of contents 

Here is an overview of our blog post, that highlights the key sections addressed : 

Section  |  Description   
---|---  
Introduction  |  Explanation of the general context.   
Setting the stage  |  Presentation of what will be discussed in the blog post.   
The base prompts and chain  |  Setup of the first base prompts and chain.   
The Base Implementation  |  Initial setup with an untouched database and LangChain.   
Elevating Implementation with Database Preparation  |  Enhancement of the setup by preparing meaningful tables and modalities in the database.   
Descriptive Implementation  |  Focus on adding clear and concise column descriptions to improve SQL query generation accuracy.   
Fact-Based Implementation  |  Enhancement of the user interaction by extracting facts from user inputs for more accurate and relevant SQL queries.   
Crafting Explainable Answers  |  How to provide contextually rich and understandable answers to user queries.   
Bonus 1: Implementing Memory for Conversational Continuity  |  Introduction of memory features for conversational continuity in the chatbot.   
Bonus 2: Enforcing Count in Summation  |  Addition of count metrics to summation queries for clearer and more comprehensive responses.   
Bonus 3: Preventing SQL Syntax Issues  |  Implementation of checks to prevent SQL syntax issues during data retrieval.   
Bonus 4: Implementing Early Stop and Clarification  |  Enhancement the chatbot’s accuracy by adding clarification requests for complex or incomplete user questions.   
Warnings and Considerations  |  introduction to the potential blocking points of our approach.   
Conclusion  |  Summary of the main points discussed and final thoughts.   
References  |  Listing of some references.   
  
##  Introduction 

Nowadays, **Artificial Intelligence** is seen not just as a tool, but also as a collaborator in **problem-solving** and creativity. Welcome to the era of **_GPT-4_ ** ! 

![](https://gulftoday.ae/-/media/gulf-today/images/articles/news/2023/4/26/openai-750.ashx?h=450&w=750&hash=E25267B1FBEC0792D6AC6404A9037D8C) Developed by **_OpenAI_ ** , GPT-4 is not merely an upgrade from its predecessors, but also a significant advancement in the field of _Natural Language Processing_ _(NLP)_ and Artificial Intelligence in general. It is a system that is not only capable of understanding and generating human-like text, but also possesses the ability to **solve complex problems with a remarkable accuracy** that was once thought to be the exclusive domain of **human** **intelligence** . GPT-4 brings to the table broader **general knowledge** , **advanced reasoning capabilities** , and **a nuanced understanding of context,** ensuring that the interactions are not just accurate but also meaningful and insightful. To exploit these facilities, one can use a framework called LangChain. 

![](https://cdn.analyticsvidhya.com/wp-content/uploads/2023/07/langchain3.png)

While providing a platform for developing applications, **LangChain** emphasizes the ease of use in its components, ensuring that developers find it accessible and **user-friendly** , regardless of their level of interaction with this framework. It allows the creation of **« Use-Case Specific Chains »** , which can be perceived as assembling components in specific configurations to best address a particular use case. These chains are intended to offer a **higher-level interface,** ensuring that the interactions and the functionalities are not just efficient but also tailored to specific use cases and specific requirements. To know more about LangChain and its documentation, you can explore it [ here ](https://docs.langchain.com/docs/) . 

![](https://upload.wikimedia.org/wikipedia/commons/8/86/Database-icon.svg)

**Databases** that are the repositories of knowledge, and chatbots that are the interfaces that allow us to **interact with this knowledge** , create together a strong relationship that enables users to extract, interact, and engage with data in a meaningful manner. The importance of ensuring that these interactions are **secure, reliable, and accurate** cannot be overstated, especially in an era where data drives decisions. This relationship between databases and chatbots ensures that data is not just stored but is accessible and actionable, **providing users with the insights they ask for when they need them** . 

**Through the chapters of this blog** , we will explore, understand, and delve into the world of chatbots, databases, and the confluence of the two through LangChain. From understanding the basics, exploring implementations, **to navigating through challenges and complexities** , this blog aims to be a comprehensive guide through the multifaceted world of chatbots and database interactions. 

##  Setting the stage 

Embarking on our journey, the first step involves acquainting ourselves with the essentials: **OpenAI, LangChain, and the database** . OpenAI, with its GPT-4 model, **provides the linguistic and reasoning capabilities** , while LangChain acts as the **architect** that structures our interactions and dialogues with the database, and ensures that they are not just some simple conversations but insightful and **data-driven dialogues.**

![](https://www.quantmetry.com/wp-content/uploads/2023/10/three.jpg)

_/!\ Making sure that the database is secure and that interactions are**read-only** for users is paramount. Even with safeguards against Data Manipulation Language (DML) in the following prompts, making sure that the database is inherently secure protects the data and preserves its integrity. _

![](https://www.quantmetry.com/wp-content/uploads/2023/10/lock.jpg)

In the realm of chatbots and data interactions, **simplicity** often trumps complexity. Small and efficient chains and prompts in LangChain not only ensure smoother and faster interactions, but also reduce the computational load and guarantee that the user’s experience is **seamless and efficient** . Considering that interactions with **OpenAI can be subject to latency and limitations** on the number of requests, **a minimalist approach** guarantees that every interaction and every request is used to its maximum potential. 

![](https://www.quantmetry.com/wp-content/uploads/2023/10/mini.jpeg)

In our journey, a key focus is placed on **crafting chains and prompts that are generalist rather than specific** , guaranteeing that they are versatile and adaptable to various databases. This approach allows also for easier transitions and **adaptability to different databases** , which makes the chatbot able to interact with various databases with minimal adjustments to the chains and prompts. **The specificity can be embedded within the descriptions of the tables** , ensuring that while the chains and prompts remain generalist, the interactions can still be specific, accurate and relevant. 

![](https://www.quantmetry.com/wp-content/uploads/2023/10/chameleon.jpeg)

##  The base prompts and chain 

To start, we create the base prompts and chain, that will be used to generate the appropriate SQL query and give the right answer to the user’s question. 

_You can find the code of this section in this repo:[ blog-chat-with-database ](https://github.com/lucasiscovici/blog-chat-with-database) _

###  The LLM 

The chat model used is OpenAI’s GPT-4. 
    
    
    from langchain.chat_models import ChatOpenAI
    # from langchain.chat_models import AzureChatOpenAI
    
    llm = ChatOpenAI(temperature=0, model="gpt-4")

We set « temperature » to the value « 0 » to reduce the level of the creativity of the LLM’s response. 

###  The base features of the SQL database 

We have the following SQL database’s basic features : 

  * Get the table names. 
  * Retrieve the table information (schema, sample rows). 
  * Execute the query. 


    
    
    from langchain.sql_database import SQLDatabase
    # Instantiate the SQLDatabase object
    db = SQLDatabase.from_uri("…") # Using directly the URI for example
    
    # Get the tables' names
    table_names_list = db.get_usable_table_names()
    
    # Get the tables' infos (schema, sample rows)
    table_infos_str = db.get_table_info_no_throw(table_names_list)
    
    # Execute the query
    query_response = db.run_no_throw("SELECT * FROM table_1") # Starts with "Error: " if the query does not work

###  The base chain 

  * The « SQL query » prompt: 



First, we prepare the prompt that will be used to generate the SQL query: 
    
    
    from langchain.prompts import PromptTemplate
    
    SQL_QUERY_PROMPT_TEXT="""
    -- Language : SQL
    -- Dialect : SQLITE
    -- Here are the table schemas :
    {schemas}
    -- A SQL query to return 1:
    SELECT 1;
    -- A SQL query for "{question}". Please only make a stand-alone query. DO NOT make any DML statements (INSERT, UPDATE, DELETE, DROP etc.) to the database. DO NOT RETURN Markdown Format SQL CODE. DO NOT ADD '{% raw %}```{% endraw %}' :
    """
    
    SQL_QUERY_PROMPT = PromptTemplate.from_template(SQL_QUERY_PROMPT_TEXT)

You can change the dialect (« SQLITE ») with others (PostgreSQL, MySQL, Oracle, …). 

  * The Response prompt: 



Second, we prepare the prompt that will be used to format the answer in a manner that humans can understand easily : 
    
    
    from langchain.prompts import PromptTemplate
    
    RESPONSE_PROMPT_TEXT="""
    As a SQL specialist, I'll format the answer to your question and query response, ensuring a conversational, polite, formal, and factual presentation, while adhering to standard financial notation for numerical values.
    
    The user's question : {question}.
    The query response : {response}.
    The answer:
    """
    
    RESPONSE_PROMPT = PromptTemplate.from_template(RESPONSE_PROMPT_TEXT)

  * The Chain: 



After that, we construct the class of SQL chains, using the prompts that we already created: 
    
    
    from langchain.chains.base import Chain
    from langchain.utilities import SQLDatabase
    from langchain.chains import LLMChain
    
    from .prompts import (
        SQL_QUERY_PROMPT,
        RESPONSE_PROMPT
    )
    
    class SQLChain(Chain):
    
        db: SQLDatabase
        llm_chain_query: LLMChain
        llm_chain_response: LLMChain
    
        input_key: str = "question" #: :meta private:
        output_key: str = "output"  #: :meta private:
    
        @property
        def input_keys(self):
            return [self.input_key]
    
        @property
        def output_keys(self):
            return [self.output_key]
    
        def _call(
            self,
            inputs,
            run_manager = None
        ):
            # get the tables' names
            table_names_list = self.db.get_usable_table_names() 
    
            # get the tables' infos
            table_infos_str = self.db.get_table_info_no_throw(table_names_list)
    
            # generate the sql query
            sql_query = self.llm_chain_query.run({**inputs, "schemas": table_infos_str})
            print("sql_query", sql_query)
    
            # execute the sql query
            query_response = self.db.run_no_throw(sql_query)
            
            # generate the response
            response = self.llm_chain_response.run({**inputs, "response": query_response})
    
            return {self.output_key: response}
    
    
        @classmethod
        def from_db_and_llm(
            cls,
            db,
            llm,
            prompt_sql_query = SQL_QUERY_PROMPT,
            prompt_response = RESPONSE_PROMPT,
            verbose = False,
            **kwargs
        ):
            return cls(
                db=db, 
                llm=llm, 
                llm_chain_query=LLMChain(llm=llm, prompt=prompt_sql_query, verbose=verbose), 
                llm_chain_response=LLMChain(llm=llm, prompt=prompt_response, verbose=verbose),
                **kwargs
            )

And then, we instantiate an object (chain) of this class, using the model that we have chosen before: 
    
    
    def create_chain():
        db = SQLDatabase(…)
        llm = ChatOpenAI(temperature=0, model="gpt-4")
        return SQLChain.from_db_and_llm(llm=llm, db=db)
    
    chain = create_chain()

Finally, we can run the chain on the user’s question as following : 
    
    
    chain("What were the revenue of SFR in 2022 ?")["output"]

##  The Base Implementation 

###  **Untouched Database and LangChain**

####  **The (not prepared) database**

_The code used in this section can be found in these git branchs:[ base-no-prepared. ](https://github.com/lucasiscovici/blog-chat-with-database/tree/base-no-prepared) _

There is only one table named « _data_ » which have theses columns: 

  * date : The date in the string format « MM-YYYY » (all months of 2022) 
  * company : The company’s name (TotalEnergies, haribo, SFR) 
  * sector : The company’s sector (Energy, confectionery, TELECOMMUNICATION) 
  * indicator : The indicators: ‘ebitda’, ‘SALES’ 
  * value : The indicator’s value 
  * type : The nature of the values (ebitda, SALES): ‘actual’ represents the true value, while ‘Budget’ denotes the budgeted value. 



_/!\ The data that we used in this article has been randomly generated. You can find the code we used in the repo[ blog-chat-with-database ](https://github.com/lucasiscovici/blog-chat-with-database) and the data in the file « data.csv ». _

Sample (5 rows): 

![](https://www.quantmetry.com/wp-content/uploads/2023/10/capture-decran-2023-10-10-a-153852.png)

Figure 1: The first 5 rows of the (not prepared) database 

####  **The run**

When we run the chain on the study question: 
    
    
    chain("What were the revenue of SFR in 2022 ?")["output"]

The following prompts and queries are generated in the order: 

  * The « SQL Query » prompt: 


    
    
    -- Language : SQL
    -- Dialect : SQLITE
    -- Here are the table schemas :
    
    CREATE TABLE data (
            date TEXT,
            company TEXT,
            sector TEXT,
            indicator TEXT,
            value INTEGER,
            type TEXT
    )
    
    /*
    3 rows from data table:
    date    company sector  indicator       value   type
    01-2022 TotalEnergies   Energy  ebitda  167621  actual
    02-2022 TotalEnergies   Energy  ebitda  29184   actual
    03-2022 TotalEnergies   Energy  ebitda  6556    actual
    */
    -- A SQL query to return 1:
    SELECT 1;
    -- A SQL query for "What were the revenue of SFR in 2022 ?". Please only make a stand-alone query. DO NOT make any DML statements (INSERT, UPDATE, DELETE, DROP etc.) to the database. DO NOT RETURN Markdown Format SQL CODE. DO NOT ADD '{% raw %}```{% endraw %}' :

  * The generated SQL query: 


    
    
    SELECT value FROM data WHERE company = 'SFR' AND date LIKE '%2022%' AND indicator = 'revenue';

_/!\ Because of the llm, the generated SQL query can still vary even with a temperature of 0._

  * The « Response » prompt: 


    
    
    As a SQL specialist, I'll format the answer to your question and query response, ensuring a conversational, polite, formal, and factual presentation, while adhering to standard financial notation for numerical values.
    
    The user's question : What were the revenue of SFR in 2022 ?.
    The query response : .
    The answer:

  * The response : 



` I'm sorry, but the query response doesn't provide any information about SFR's revenue in 2022. Could you please provide the necessary data? `

_/!\ Because of the llm, the generated response can still vary even with a temperature of 0._

As we can see, the response that we obtained is not what we are waiting for. So, how can we explain this ? Let’s delve into the details to understand it. 

The first problems that we can identify are : 

  * The « date » type is not in a standard SQL DATE type 
  * The « company » name is not normalized 
  * The « sector » name is not normalized 
  * The « indictor » modalities are not normalized 
  * The table is not pivoted for the « indicator » and « value » columns 
  * The « type » modalities are not normalized 



The challenges that we are facing here often stem from the complexity and unprocessed nature of the database, where generating SQL queries that are both accurate and efficient might pose a hurdle. Therefore, a database’ preparation becomes a necessity. In fact, the raw and unprocessed database, while still rich in information, may not be optimally structured for efficient interaction and query generation. Thus, transitioning from a basic implementation to a more complex and refined one becomes the next pivotal step in our journey. 

##  Elevating Implementation with Database Preparation 

###  Crafting meaningful tables and modalities 

As we delve deeper, the importance of structured and meaningful tables and modalities in the database becomes paramount. Ensuring that tables, columns, and modalities are not just data-rich but also meaningful and intuitive enhances the efficiency and accuracy of interactions and queries generation through LangChain. 

In the realm of SQL databases, the structure and organization of tables are pivotal. 

A well-structured table typically involves a clear distinction between « key/index » columns and « data/value » columns. Key or index columns are those that are used to search, sort, and organize the data, ensuring that data retrieval is efficient and accurate. On the other hand, data or value columns store the actual information that we want to retrieve and use. 

A « flat table » in database terminology refers to a table with more columns than rows, ensuring that data is spread out horizontally, providing a comprehensive, single-layer view that can be particularly useful for data analysis and reporting. This structure minimizes the need for complex joins or unions, thereby simplifying queries and enhancing retrieval speed. 

###  The preparation of the « flat » database 

_The code used in this section can be found in this git branch:_ _[ base-prepared ](https://github.com/lucasiscovici/blog-chat-with-database/tree/base-prepared) _

To improve the answer we obtained for our question, we apply some changes on our dataset. There is only one table named « _data_ » which have theses columns: 

  * date : The date  with the DATE format  « YYYY-MM-DD » (all months of 2021/2022) 
  * company: The company’s name  capitalized  (TotalEnergies, Haribo, SFR) 
  * sector : The company’s sector  uppercased  (ENERGY, CONFECTIONERY, TELECOMMUNICATION) 
  * sales :  The sales  for this date (the month) 
  * ebitda :  The ebitda  for this date (the month) 
  * type : This refers to the nature of the values (sales, ebitda)  lowercased  : ‘actual’ represents the true value, while ‘budget’ denotes the budgeted value. 



Sample (5 rows): 

![](https://www.quantmetry.com/wp-content/uploads/2023/10/capture-decran-2023-10-10-a-165137.png)

Figure 2: The first 5 rows of the (prepared) database 

And here are the changes that are done during this flattening step of the database: 

  * The « date » column is now in standard SQL DATE type 
  * The « company » name is capitalized 
  * The « sector » name is uppercased 
  * The « indicator » and « value » columns have been « flattened », to be only the « sales » and « ebitda » columns 
  * sales & ebitda columns’ names are lowercased 
  * The type modalities are lowercased 



###  **The run**

After making these changes (preparation of the « flat » database), we re-execute our run and see what we will obtain as an answer: 

  * Run the chain on the study question: 


    
    
    chain("What is the sales of SFR in 2022 ?")["output"]

  * The « SQL Query » prompt: 


    
    
    -- Language : SQL
    -- Dialect : SQLITE
    -- Here are the table schemas :
    
    CREATE TABLE data (
            date DATE, 
            company TEXT, 
            sector TEXT, 
            sales INTEGER, 
            ebitda INTEGER, 
            type TEXT
    )
    
    /*
    3 rows from data table:
    date    company sector  sales   ebitda  type
    2022-01-01      TotalEnergies   ENERGY  167621  29184   actual
    2022-02-01      TotalEnergies   ENERGY  6556    194393  actual
    2022-03-01      TotalEnergies   ENERGY  72097   64196   actual
    */
    -- A SQL query to return 1:
    SELECT 1;
    -- A SQL query for "What were the revenue of SFR in 2022 ?". Please only make a stand-alone query. DO NOT make any DML statements (INSERT, UPDATE, DELETE, DROP etc.) to the database. DO NOT RETURN Markdown Format SQL CODE. DO NOT ADD '{% raw %}```{% endraw %}' :
    
    

  * The generated SQL Query: 


    
    
    SELECT sales AS revenue FROM data WHERE company = 'SFR' AND strftime('%Y', date) = '2022';

_/!\ Because of the llm, the generated sql query can still vary even with a temperature of 0._

  * The « Response » prompt: 


    
    
    As a SQL specialist, I'll format the answer to your question and query response, ensuring a conversational, polite, formal, and factual presentation, while adhering to standard financial notation for numerical values.
    
    The user question : What were the revenue of SFR in 2022 ?.
    The query response : [(64175,), (121178,), (70765,), (180397,), (57570,), (85008,), (60043,), (82694,), (70186,), (55307,), (188196,), (55738,), (130870,), (168519,), (37452,), (36603,), (195294,), (141289,), (195825,), (112311,), (104700,), (57493,), (133569,), (23831,)].
    The answer:

  * The generated response: 


    
    
    The revenues of SFR in 2022 were as follows (in standard financial notation):
    
    - January: \$64,175
    - February: \$121,178
    - March: \$70,765
    - April: \$180,397
    - May: \$57,570
    - June: \$85,008
    - July: \$60,043
    - August: \$82,694
    - September: \$70,186
    - October: \$55,307
    - November: \$188,196
    - December: \$55,738
    
    Please note that these figures are subject to change as they are updated regularly.

_/!\ Because of the llm, the generated response can still vary even with a temperature of 0._

As we can see, the answer obtained is way better than the one we obtained before the preparation of the database. However, we still haven’t obtained the right answer that we are looking for unfortunately. Let’s keep investigating for the reasons of that. 

###  **The problems**

With a structured and a meaningful database in place, interactions and runs through LangChain are anticipated to be more coherent and accurate. However, challenges may still arise, which make it necessary to provide more additional descriptions and understanding implicit user queries, that we will address in subsequent steps. 

###  **The question**

The first source of problem may be the question itself, or in other words, how the model understand it. In this article, we will focus on the question: **« What were the revenue of SFR in 2022 ? »**

This question appears to be straightforward, yet as we will explore, it demands a **specific understanding** of the provided base and a comprehension of the **facts** that are **implicitly present** in the question **.**

In fact, the « data » table contains the « sales » and « ebitda » values **per month for a company** . What’s more, each of these values can be either « actual », i.e. real values, or « budget », i.e. budgeted values. 

So for the model to write the right sql query, it needs to **understand** this and more precisely: 

  * « SFR » is the **company name**
  * « revenue » refers to **the « sales » column**
  * « 2022 » refers to **the « date » column** AND is **the sum of monthly values**
  * the « **type » must be « actual »** if no further context is given in the question 



###  **The model understanding**

Some other problems that we can easily identify if we look at the SQL Query generated are : 

  * the missing of the « SUM » operation in the SQL query in order to get the annual revenue instead of the monthly ones. 
  * The missing of the condition: column « type » = « actual ». 



Consequently, addressing these challenges involves refining the prompts and potentially adding additional layers of complexity to the LangChain setup, like adding the descriptions of the columns. 

##  Descriptive Implementation 

The journey towards optimal interaction with databases through LangChain brings us to the crucial aspect of column descriptions. Ensuring that each column (and modalities, when necessary) in the database tables is accompanied by a clear and concise description enhances the model’s ability to generate accurate and relevant SQL queries. Descriptions act as guides, providing contextual insights to the model and guaranteeing that the generated queries are not just syntactically correct but also contextually relevant. 

By adding the descriptions, the prompts and runs through LangChain are expected to be more informed and accurate. The model now has additional context, which can be used to generate queries that are more aligned with the user inputs and requirements. 

_The code used in this section can be found in this git branch:[ description ](https://github.com/lucasiscovici/blog-chat-with-database/tree/description) _

###  The descriptions (description.csv) 

To do this, we create a description file that contains a brief description of each column. 
    
    
    table;column;column_type;description
    data;date;DATE; YYYY-MM-DD date format
    data;company;CHAR; The name of the company, always capitalized
    data;sector;CHAR; The sector of the company, "ENERGY" or "TELECOMMUNICATION" OR "CONFECTIONERY", always uppercased
    data;sales;INTEGER; the sales in dollars
    data;ebitda;INTEGER; the ebitda in dollars
    data;type;CHAR; the type is "actual" (the real value) or "budget" (the budgeted value), always lowercased

###  The updated chain and prompts 

Then, we update the « SQL query » prompt and the class of SQL chains in order to take these descriptions into account: 

  * The prompt: 


    
    
    SQL_QUERY_PROMPT_TEXT="""-- Language : SQL
    -- Dialect : SQLITE
    -- Here are the descriptions of the table schemas; please read them carefully to better understand the table:
    {descriptions}
    -- Here are the table schemas :
    {schemas}
    -- A SQL query to return 1:
    SELECT 1;
    -- A SQL query for "{question}". Please only make a stand-alone query. DO NOT make any DML statements (INSERT, UPDATE, DELETE, DROP etc.) to the database. DO NOT RETURN Markdown Format SQL CODE. DO NOT ADD '{% raw %}```{% endraw %}' :
    """

  * The class: 


    
    
    ...
    
    class SQLChain(Chain):
        ...
        table_descriptions: str
        ...
    
        def _call(
            self,
            inputs,
            run_manager = None
        ):
            ...
            # generate the sql query
            sql_query = self.llm_chain_query.run({**inputs, "schemas": table_infos_str, "descriptions": self.table_descriptions})
            ...
    
    
        @classmethod
        def from_db_and_llm(
            cls,
            db,
            llm,
            prompt_sql_query = SQL_QUERY_PROMPT,
            prompt_response = RESPONSE_PROMPT,
            table_descriptions = "",
            verbose = False,
            **kwargs
        ):
            return cls(
                db=db, 
                llm=llm, 
                llm_chain_query=LLMChain(llm=llm, prompt=prompt_sql_query, verbose=verbose), 
                llm_chain_response=LLMChain(llm=llm, prompt=prompt_response, verbose=verbose),
                table_descriptions=table_descriptions,
                **kwargs
            )
    
    

We also modify the instantiation of the class: 
    
    
    from pathlib import Path
    ...
    def create_chain(conn, verbose=True):
        ...
        descriptions_str = Path(__file__).parent.joinpath("description.csv").read_text()  # description of each columns
        return SQLChain.from_db_and_llm(llm=llm, db=db, verbose=verbose, table_descriptions=descriptions_str)
    

###  The run 

After these modifications, we run the chain again on the study question: 
    
    
    chain("What were the revenue of SFR in 2022 ?")["output"]

And here is the « SQL Query » prompt generated after these modifications : 
    
    
    -- Language : SQL
    -- Dialect : SQLITE
    -- Here are the descriptions of the table schemas; please read them carefully to better understand the table:
    table;column;column_type;description
    data;date;DATE; YYYY-MM-DD date format
    data;company;CHAR; The name of the company, always capitalized
    data;sector;CHAR; The sector of the company, "ENERGY" or "TELECOMMUNICATION" OR "CONFECTIONERY", always uppercased
    data;sales;INTEGER; the sales in dollars
    data;ebitda;INTEGER; the ebitda in dollars
    data;type;CHAR; the type is "actual" (the real value) or "budget" (the budgeted value), always lowercased
    -- Here are the table schemas :
    
    CREATE TABLE data (
            date DATE, 
            company TEXT, 
            sector TEXT, 
            sales INTEGER, 
            ebitda INTEGER, 
            type TEXT
    )
    
    /*
    3 rows from data table:
    date    company sector  sales   ebitda  type
    2022-01-01      TotalEnergies   ENERGY  167621  29184   actual
    2022-02-01      TotalEnergies   ENERGY  6556    194393  actual
    2022-03-01      TotalEnergies   ENERGY  72097   64196   actual
    */
    -- A SQL query to return 1:
    SELECT 1;
    -- A SQL query for "What were the revenue of SFR in 2022 ?". Please only make a stand-alone query. DO NOT make any DML statements (INSERT, UPDATE, DELETE, DROP etc.) to the database. DO NOT RETURN Markdown Format SQL CODE. DO NOT ADD '{% raw %}```{% endraw %}' :

And the generated SQL Query: 
    
    
    SELECT SUM(sales) AS revenue FROM data WHERE company = 'SFR' AND date LIKE '2022-%';

_/!\ Because of the llm, the generated sql query can still vary even with a temperature of 0._

And finally the « Response » prompt: 
    
    
    As a SQL specialist, I'll format the answer to your question and query response, ensuring a conversational, polite, formal, and factual presentation, while adhering to standard financial notation for numerical values.
    
    The user question : What were the revenue of SFR in 2022 ?.
    The query response : [(2429013,)].
    The answer:

So, the generated response now becomes: 
    
    
    The revenue of SFR in 2022 was \$2,429,013.

_/!\ Because of the llm, the generated response can still vary even with a temperature of 0._

Hurra ! The answer obtained now is better because it contains the sum of all the monthly revenues. However, if we re-execute the question different times, we still have the following problems: 

  * « SUM » operator ** not always  added ** in the SQL query. 
  * Missing the condition: column « type » equals « actual ». 



To fix that, let’s go more deeper in our implementation’s improvement. 

##  Fact-Based Implementation 

In the intricate dance of user interactions and database querying, understanding the implicit and explicit facts within a user’s question becomes pivotal. Extracting facts involves discerning the underlying intents, entities, and context from the user’s input, which can then be used to generate more accurate and relevant SQL queries, ensuring that the interaction is not just data-driven but also contextually aware. 

With the extracted facts in hand, the steps within LangChain can be enhanced and refined to better understand and interpret user questions. This involves potentially introducing additional steps or refining existing ones to ensure that the extracted facts are effectively used to generate queries that are both syntactically and contextually correct. 

_The code used in this section can be found in this git branch:[ facts ](https://github.com/lucasiscovici/blog-chat-with-database/tree/facts) _

###  The new step: Generation of implicit facts 

First, we create a prompt for extracting implicit facts from the user’s question 
    
    
    FACTS_PROMPT_STR = """
    -- Here is the question of the user :
    {question}
    -- Here are the descriptions of the table schemas; please read them carefully to better understand the table:
    {descriptions}
    -- Here are the table schemas :
    {schemas}
    Review the tables, noting that some columns are for filtering ("Key Columns" or "Index Columns") and others contain specific values ("Data Columns" or "Value Columns").
    -- Create a bulleted list identifying all implicit facts from a user’s question, focusing on implicit values in the 'Key' or 'Index Columns.'
    Use common sense to infer only obvious values, include pertinent date information (months/years, ...), and especially specify all necessary calculations (e.g., using SQL SUM, MAX, or simple column selection).
    Don't make hasty decisions; try to be factual and infer values only when truly necessary, using common sense.
    Ensure your decisions are thoughtful and factual, and then, rephrase the user’s question based on these facts, indicating it's a potential rewrite.
    Present your answer as a bulleted list:
    - """
    FACTS_PROMPT = PromptTemplate.from_template(FACTS_PROMPT_STR)

###  The updated prompts 

Taking into account this approach, we should update the « SQL query » prompt: 
    
    
    -- Language : SQL
    -- Dialect : SQLITE
    -- Here are the descriptions of the table schemas; please read them carefully to better understand the table:
    {descriptions}
    -- Here are the table schemas :
    {schemas}
    -- Here are the interesting facts:
    {facts}
    -- A SQL query to return 1:
    SELECT 1;
    -- A SQL query for {question}". Please only make a stand-alone query. DO NOT make any DML statements (INSERT, UPDATE, DELETE, DROP etc.) to the database. DO NOT RETURN Markdown Format SQL CODE. DO NOT ADD '{% raw %}```{% endraw %}' :
    
    

And the « Response » prompt: 
    
    
    As a SQL specialist, I'll format the answer to your question and query response, ensuring a conversational, polite, formal, and factual presentation, while adhering to standard financial notation for numerical values.
    
    The user question : {question}.
    The facts: {facts}.
    The SQL query: {query}.
    The query response : {response}.
    The answer:

###  The updated chain 

We should also update the SQL chains’ class: 
    
    
    ...
    from .prompts import ..., FACTS_PROMPT
    ...
    class SQLChain(Chain):
        ...
        llm_chain_facts: LLMChain
        ...
        def _call(self, inputs, run_manager=None):
            ...
            # get facts
            facts = self.llm_chain_facts.run(
                {
                    **inputs,
                    "schemas": table_infos_str,
                    "descriptions": self.table_descriptions,
                }
            )
    
            # generate the sql query
            sql_query = self.llm_chain_query.run(
                {
                    **inputs,
                    "schemas": table_infos_str,
                    "descriptions": self.table_descriptions,
                    "facts": facts # add facts
                }
            )
            ...
            # generate the response
            response = self.llm_chain_response.run(
                {**inputs, "query": sql_query, "facts": facts, "response": query_response} # add facts
            )
    
            return {self.output_key: response}
    
        @classmethod
        def from_db_and_llm(
            cls,
            db,
            llm,
            prompt_sql_query=SQL_QUERY_PROMPT,
            prompt_response=RESPONSE_PROMPT,
            prompt_facts=FACTS_PROMPT, # add facts prompt
            table_descriptions="",
            verbose=False,
            **kwargs
        ):
            return cls(
                db=db,
                llm=llm,
                llm_chain_query=LLMChain(llm=llm, prompt=prompt_sql_query, verbose=verbose),
                llm_chain_response=LLMChain(llm=llm, prompt=prompt_response, verbose=verbose),
                llm_chain_facts=LLMChain(llm=llm, prompt=prompt_facts, verbose=verbose), # add facts llm chain 
                table_descriptions=table_descriptions,
                **kwargs
            )
    

###  The run 

After that the modifications are done, we re-run the chain on the study question: 
    
    
    chain("What were the revenue of SFR in 2022 ?")["output"]

And we get the following results: 

  * The « Fact » prompt: 


    
    
    -- Here is the question of the user :
    What were the revenue of SFR in 2022 ?
    -- Here are the descriptions of the table schemas; please read them carefully to better understand the table:
    table;column;column_type;description
    data;date;DATE; YYYY-MM-DD date format
    data;company;CHAR; The name of the company, always capitalized
    data;sector;CHAR; The sector of the company, "ENERGY" or "TELECOMMUNICATION" OR "CONFECTIONERY", always uppercased
    data;sales;INTEGER; the sales in dollars
    data;ebitda;INTEGER; the ebitda in dollars
    data;type;CHAR; the type is "actual" (the real value) or "budget" (the budgeted value), always lowercased
    -- Here are the table schemas :
    
    CREATE TABLE data (
            date DATE, 
            company TEXT, 
            sector TEXT, 
            sales INTEGER, 
            ebitda INTEGER, 
            type TEXT
    )
    
    /*
    3 rows from data table:
    date    company sector  sales   ebitda  type
    2022-01-01      TotalEnergies   ENERGY  167621  29184   actual
    2022-02-01      TotalEnergies   ENERGY  6556    194393  actual
    2022-03-01      TotalEnergies   ENERGY  72097   64196   actual
    */
    Review the tables, noting that some columns are for filtering ("Key Columns" or "Index Columns") and others contain specific values ("Data Columns" or "Value Columns").
    -- Create a bulleted list identifying all implicit facts from a user’s question, focusing on implicit values in the 'Key' or 'Index Columns.'
    Use common sense to infer only obvious values, include pertinent date information (months/years, ...), and especially specify all necessary calculations (e.g., using SQL SUM, MAX, or simple column selection).
    Don't make hasty decisions; try to be factual and infer values only when truly necessary, using common sense.
    Ensure your decisions are thoughtful and factual, and then, rephrase the user’s question based on these facts, indicating it's a potential rewrite.
    Present your answer as a bulleted list:
    -

  * The extracted facts: 


    
    
    The user is asking for the revenue of a specific company, SFR, in a specific year, 2022.
    - The company name "SFR" is an implicit value for the 'company' column.
    - The year "2022" is an implicit value for the 'date' column.
    - The user is interested in the 'sales' column, which represents the revenue.
    - The user does not specify whether they want the actual or budgeted revenue, so we can assume they want the actual revenue. This is an implicit value for the 'type' column.
    - The user does not specify a specific month, so we can assume they want the total revenue for the year 2022. This requires a SUM calculation on the 'sales' column.

  * The « SQL Query » prompt: 


    
    
    -- Language : SQL
    -- Dialect : SQLITE
    -- Here are the descriptions of the table schemas; please read them carefully to better understand the table:
    table;column;column_type;description
    data;date;DATE; YYYY-MM-DD date format
    data;company;CHAR; The name of the company, always capitalized
    data;sector;CHAR; The sector of the company, "ENERGY" or "TELECOMMUNICATION" OR "CONFECTIONERY", always uppercased
    data;sales;INTEGER; the sales in dollars
    data;ebitda;INTEGER; the ebitda in dollars
    data;type;CHAR; the type is "actual" (the real value) or "budget" (the budgeted value), always lowercased
    -- Here are the table schemas :
    
    CREATE TABLE data (
            date DATE, 
            company TEXT, 
            sector TEXT, 
            sales INTEGER, 
            ebitda INTEGER, 
            type TEXT
    )
    
    /*
    3 rows from data table:
    date    company sector  sales   ebitda  type
    2022-01-01      TotalEnergies   ENERGY  167621  29184   actual
    2022-02-01      TotalEnergies   ENERGY  6556    194393  actual
    2022-03-01      TotalEnergies   ENERGY  72097   64196   actual
    */
    -- Here are the interesting facts:
    The user is asking for the revenue of a specific company, SFR, in a specific year, 2022.
    - The company name "SFR" is an implicit value for the 'company' column.
    - The year "2022" is an implicit value for the 'date' column.
    - The user is interested in the 'sales' column, which represents the revenue.
    - The user does not specify whether they want the actual or budgeted revenue, so we can assume they want the actual revenue. This is an implicit value for the 'type' column.
    - The user does not specify a specific month, so we can assume they want the total revenue for the year 2022. This requires a SUM calculation on the 'sales' column.
    
    Rephrased Question: What was the total actual sales (revenue) for the company SFR in the year 2022?
    -- A SQL query to return 1:
    SELECT 1;
    -- A SQL query for "What were the revenue of SFR in 2022 ?". Please only make a stand-alone query. DO NOT make any DML statements (INSERT, UPDATE, DELETE, DROP etc.) to the database. DO NOT RETURN Markdown Format SQL CODE. DO NOT ADD '{% raw %}```{% endraw %}' :

  * The generated SQL Query: 


    
    
    SELECT SUM(sales) AS total_revenue FROM data WHERE company = 'SFR' AND type = 'actual' AND strftime('%Y', date) = '2022';

  * The « Response » prompt: 


    
    
    As a SQL specialist, I'll format the answer to your question and query response, ensuring a conversational, polite, formal, and factual presentation, while adhering to standard financial notation for numerical values.
    
    The user question : What were the revenue of SFR in 2022 ?.
    The facts: The user is asking for the revenue of a specific company, SFR, in a specific year, 2022.
    - The company name "SFR" is an implicit value for the 'company' column.
    - The year "2022" is an implicit value for the 'date' column.
    - The user is interested in the 'sales' column, which represents the revenue.
    - The user does not specify whether they want the actual or budgeted revenue, so we can assume they want the actual revenue. This is an implicit value for the 'type' column.
    - The user does not specify a specific month, so we can assume they want the total revenue for the year 2022. This requires a SUM calculation on the 'sales' column.
    
    Rephrased Question: What was the total actual sales (revenue) for the company SFR in the year 2022?.
    The SQL query: SELECT SUM(sales) AS total_revenue
    FROM data
    WHERE company = 'SFR' 
    AND type = 'actual' 
    AND strftime('%Y', date) = '2022';.
    The query response : [(1091257,)].
    The answer:

  * Finally, the generated response: 


    
    
    The total actual revenue for the company SFR in the year 2022 was $1,091,257.

Eureka! Finally, we’ve successfully obtained the right answer that we were looking for! 

But, is there still a way to further improve this answer? 

The answer is yes. In fact, we can improve the user’s experience and ensure that it is smooth, intuitive, and insightful by giving more details in the answer, especially explain how it was obtained. By doing this, the user doesn’t just receive the answer but also understands the context behind it, enhancing the overall interactions and experience. 

##  Crafting Explainable Answers 

In the realm of data interaction, providing answers that are accurate and sufficiently explanatory enhances the user’s experience. Crafting answers that provide the context and the explanation without delving into overly technical jargon ensures that the interaction is insightful yet accessible to users with varying levels of technical expertise. 

_The code used in this section can be found in this git branch:[ explainable ](https://github.com/lucasiscovici/blog-chat-with-database/tree/explainable) _

###  The updated prompt 

To apply these adjustments, we update the « Response » prompt: 
    
    
    ...
    The answer (with clear, concise explanations to the user, not an SQL specialist, using facts, the SQL query, and response) :

###  The run 

After that, we re-run the chain on the study question: 
    
    
    chain("What were the revenue of SFR in 2022 ?")["output"]

The « Response » prompt generated now is: 
    
    
    As a SQL specialist, I'll format the answer to your question and query response, ensuring a conversational, polite, formal, and factual presentation, while adhering to standard financial notation for numerical values.
    
    The user question : What were the revenue of SFR in 2022 ?.
    The facts: The user is asking for the revenue of a specific company, SFR, in a specific year, 2022.
    - The company name "SFR" is an implicit value for the 'company' column.
    - The year "2022" is an implicit value for the 'date' column.
    - The user is interested in the "sales" column, which represents the revenue.
    - The user does not specify whether they want the actual or budgeted sales, so we can assume they want the actual sales. This is an implicit value for the 'type' column.
    - The user does not specify a particular month, so we can assume they want the total sales for the entire year. This requires a SUM calculation on the 'sales' column.
    
    Rephrased Question: What was the total actual sales revenue for the company SFR in the year 2022?.
    The SQL query: SELECT SUM(sales) AS total_revenue
    FROM data
    WHERE company = 'SFR' 
    AND type = 'actual' 
    AND strftime('%Y', date) = '2022';.
    The query response : [(1091257,)].
    The answer (with clear, concise explanations to the user, not an SQL specialist, using facts, the SQL query, and response) :

And the generated response: 
    
    
    The total actual sales (revenue) for the company SFR in the year 2022 was 1,091,257. This value was obtained by summing up all the actual sales for SFR in 2022 from our database.

Voilà! The answer now looks more understandable, which improve the user’s experience. 

##  Bonus Chapters: Enhancing the Chatbot 

###  **Bonus 1: Implementing Memory for Conversational Continuity**

_The code used in this section can be found in this git branch:[ memory ](https://github.com/lucasiscovici/blog-chat-with-database/tree/memory) _

Ensuring that the chatbot can maintain conversational continuity by remembering previous interactions and using them in subsequent interactions enhances the conversational flow and the user’s experience.   
So, in order to achieve this, we should make some updates in different parts of the code. 

###  **The Updated prompts**

First, we should update the different prompts so that they take the « history » of the chat into account: 

  * The Updated « Facts » prompt: 


    
    
    -- Here is the question of the user :
    {question}
    -- Here is the conversation with the user (the last is the most recent); Use it to better understand the question of the user :
    {history}
    ...

  * The Updated « SQL Query » prompt: 


    
    
    ...
    -- Here is the conversation with the user (the last is the most recent). Don't use it to generate the SQL query, it's only used to understand the context.
    {history}
    -- A SQL query to return 1:
    SELECT 1;
    -- A SQL query for "{question}". Please only make a stand-alone query. DO NOT make any DML statements (INSERT, UPDATE, DELETE, DROP etc.) to the database. DO NOT RETURN Markdown Format SQL CODE. DO NOT ADD '{% raw %}```{% endraw %}' :

  * The Updated « Response » prompt: 


    
    
    As a SQL specialist, I'll format the answer to your question and query response, ensuring a conversational, polite, formal, and factual presentation, while adhering to standard financial notation for numerical values.
    
    The history of the conversation (the last is the most recent):
    ---------
    {history}
    ---------
    ...

###  **The Updated « create_chain » function**

Then, we should update the chain creation by adding a _« ConversationBufferMemory »_ : 
    
    
    from langchain.memory import ConversationBufferMemory
    ...
    
    def create_chain(conn, verbose=True):
        ...
        memory = ConversationBufferMemory()
        return SQLChain.from_db_and_llm(llm=llm, db=db, verbose=verbose, table_descriptions=descriptions_str, memory=memory)

###  **The run**

After making the updates, we re-run the chain on the study question, and on another question that depends to the study one: 
    
    
    print(chain("What were the revenue of SFR in 2022 ?")["output"]) 
    print(chain("in 2021 ?")["output"]) # -> FOCUS

So, the generated « Fact » prompt for the second question becomes: 
    
    
    -- Here is the question of the user :
    in 2021 ?
    -- Here is the conversation with the user (the last is the most recent); Use it to better understand the question of the user :
    Human: What were the revenue of SFR in 2022 ?
    AI: The actual revenue of the company SFR in the year 2022 was 1,091,257. This value was obtained by summing up all the sales for SFR in 2022, as indicated in our records.
    -- Here are the descriptions of the table schemas; please read them carefully to better understand the table:
    table;column;column_type;description
    data;date;DATE; YYYY-MM-DD date format
    data;company;CHAR; The name of the company, always capitalized
    data;sector;CHAR; The sector of the company, "ENERGY" or "TELECOMMUNICATION" OR "CONFECTIONERY", always uppercased
    data;sales;INTEGER; the sales in dollars
    data;ebitda;INTEGER; the ebitda in dollars
    data;type;CHAR; the type is "actual" (the real value) or "budget" (the budgeted value), always lowercased
    -- Here are the table schemas :
    
    CREATE TABLE data (
            date DATE, 
            company TEXT, 
            sector TEXT, 
            sales INTEGER, 
            ebitda INTEGER, 
            type TEXT
    )
    
    /*
    3 rows from data table:
    date    company sector  sales   ebitda  type
    2022-01-01      TotalEnergies   ENERGY  167621  29184   actual
    2022-02-01      TotalEnergies   ENERGY  6556    194393  actual
    2022-03-01      TotalEnergies   ENERGY  72097   64196   actual
    */
    Review the tables, noting that some columns are for filtering ("Key Columns" or "Index Columns") and others contain specific values ("Data Columns" or "Value Columns").
    -- Create a bulleted list identifying all implicit facts from a user’s question, focusing on implicit values in the 'Key' or 'Index Columns.'
    Use common sense to infer only obvious values, include pertinent date information (months/years, ...), and especially specify all necessary calculations (e.g., using SQL SUM, MAX, or simple column selection).
    Don't make hasty decisions; try to be factual and infer values only when truly necessary, using common sense.
    Ensure your decisions are thoughtful and factual, and then, rephrase the user’s question based on these facts, indicating it's a potential rewrite.
    Present your answer as a bulleted list:
    -

And the extracted facts are: 
    
    
    -- Here are the interesting facts:
    The user is asking for the revenue of SFR in 2021.
    - The company name is "SFR".
    - The year is 2021.
    - The type of data needed is "actual".
    - The revenue corresponds to the "sales" column in the data table.
    - The total revenue for the year needs to be calculated, likely using a SQL SUM function on the "sales" column.
    
    Rephrased Question: What was the total actual sales for the company SFR in the year 2021?

For the « SQL Query » prompt, it becomes: 
    
    
    -- Language : SQL
    -- Dialect : SQLITE
    -- Here are the descriptions of the table schemas; please read them carefully to better understand the table:
    table;column;column_type;description
    data;date;DATE; YYYY-MM-DD date format
    data;company;CHAR; The name of the company, always capitalized
    data;sector;CHAR; The sector of the company, "ENERGY" or "TELECOMMUNICATION" OR "CONFECTIONERY", always uppercased
    data;sales;INTEGER; the sales in dollars
    data;ebitda;INTEGER; the ebitda in dollars
    data;type;CHAR; the type is "actual" (the real value) or "budget" (the budgeted value), always lowercased
    -- Here are the table schemas :
    
    CREATE TABLE data (
            date DATE, 
            company TEXT, 
            sector TEXT, 
            sales INTEGER, 
            ebitda INTEGER, 
            type TEXT
    )
    
    /*
    3 rows from data table:
    date    company sector  sales   ebitda  type
    2022-01-01      TotalEnergies   ENERGY  167621  29184   actual
    2022-02-01      TotalEnergies   ENERGY  6556    194393  actual
    2022-03-01      TotalEnergies   ENERGY  72097   64196   actual
    */
    -- Here are the interesting facts:
    The user is asking for the revenue of SFR in 2021.
    - The company name is "SFR".
    - The year is 2021.
    - The type of data needed is "actual".
    - The revenue corresponds to the "sales" column in the data table.
    - The total revenue for the year needs to be calculated, likely using a SQL SUM function on the "sales" column.
    
    Rephrased Question: What was the total actual sales for the company SFR in the year 2021?
    -- Here is the conversation with the user (the last is the most recent). Don't use it to generate the SQL query, it's only used to understand the context.
    Human: What were the revenue of SFR in 2022 ?
    AI: The actual revenue of the company SFR in the year 2022 was 1,091,257. This value was obtained by summing up all the sales for SFR in 2022, as indicated in our records.
    -- A SQL query to return 1:
    SELECT 1;
    -- A SQL query for "in 2021 ?". Please only make a stand-alone query. DO NOT make any DML statements (INSERT, UPDATE, DELETE, DROP etc.) to the database. DO NOT RETURN Markdown Format SQL CODE. DO NOT ADD '{% raw %}```{% endraw %}' :

And the generated SQL Query for the second question is: 
    
    
    SELECT SUM(sales) as total_sales
    FROM data
    WHERE company = 'SFR' AND type = 'actual' AND strftime('%Y', date) = '2021';

Finally, the « Response » prompt becomes: 
    
    
    As a SQL specialist, I'll format the answer to your question and query response, ensuring a conversational, polite, formal, and factual presentation, while adhering to standard financial notation for numerical values.
    
    The history of the conversation (the last is the most recent):
    ---------
    Human: What were the revenue of SFR in 2022 ?
    AI: The actual revenue of the company SFR in the year 2022 was 1,091,257. This value was obtained by summing up all the sales for SFR in 2022, as indicated in our records.
    ---------
    The user question : in 2021 ?.
    The facts: The user is asking for the revenue of SFR in 2021.
    - The company in question is SFR.
    - The year in question is 2021.
    - The user is interested in the "sales" column, which represents the revenue.
    - The user is likely interested in the "actual" type of data, as they are asking for the revenue that was, not the budgeted revenue.
    
    Rephrased Question: What was the total actual sales for the company SFR in the year 2021?.
    The SQL query: SELECT SUM(sales) as total_sales
    FROM data
    WHERE company = 'SFR' AND type = 'actual' AND strftime('%Y', date) = '2021';.
    The query response : [(1078356,)].
    The answer (with clear, concise explanations to the user, not an SQL specialist, using facts, the SQL query, and response) :

And the generated response is now: 
    
    
    The total actual sales for the company SFR in the year 2021 was 1,078,356. This value was calculated by summing up all the actual sales for SFR in 2021, as indicated in our records.

###  **Bonus 2: Enforcing Count in Summation**

Ensuring that summation queries are accompanied by count metrics enhances the clarity and the comprehensiveness of the responses, providing additional context and insights to the user. 

_The code used in this section can be found in this git branch:[ count ](https://github.com/lucasiscovici/blog-chat-with-database/tree/count) _

###  **The updated « SQL query » prompt**

To achieve that, we update the « SQL Query » prompt like this: 
    
    
    ...
    -- A SQL query to return 1:
    SELECT 1;
    -- A SQL query for "{question}". Please only make a stand-alone query. DO NOT make any DML statements (INSERT, UPDATE, DELETE, DROP etc.) to the database. DO NOT RETURN Markdown Format SQL CODE. DO NOT ADD '{% raw %}```{% endraw %}'.
    Always include a WHERE condition to exclude NULL values. IMPORTANT: Whenever you use a SQL 'SUM' operation, always accompany it with a 'COUNT' operation for the NOT NULL values being summed:

###  **The run**

And then, we re-run the chain on the two questions studied in the Bonus 1: 
    
    
    print(chain("What were the revenue of SFR in 2022 ?")["output"]) 
    print(chain("in 2021 ?")["output"])

As a result, the **first** SQL query becomes: 
    
    
    SELECT 
        SUM(sales) AS total_sales, 
        COUNT(sales) AS count_sales_not_null 
    FROM 
        data 
    WHERE
        company = 'SFR' 
        AND type = 'actual' 
        AND date BETWEEN '2022-01-01' AND '2022-12-31'
        AND sales IS NOT NULL;

And the **first** response: 
    
    
    The total actual sales (revenue) for the company SFR in the year 2022 was 1,091,257. This total is based on 12 months of sales data, indicating that there were no months in 2022 for which the sales data was not available.

While the **second** SQL query becomes: 
    
    
    SELECT 
        SUM(sales) AS total_sales, 
        COUNT(sales) AS count_sales 
    FROM 
        data 
    WHERE 
        company = 'SFR' 
        AND type = 'actual' 
        AND date BETWEEN '2021-01-01' AND '2021-12-31'
        AND sales IS NOT NULL;

And the **second** response: 
    
    
    The total actual sales (revenue) for the company SFR in the year 2021 was 1,078,356. This total is based on 10 months of sales data, indicating that there were 2 months in 2021 for which the sales data was not available.

To have more clarifications, you can also ask this question to search which months are available: 
    
    
    chain("for that year, which months are available ?")["output"]

And the response will be: 
    
    
    The available months in the year 2021 for which we have actual sales data for the company SFR are January, February, March, April, June, July, August, September, November, and December. Please note that we do not have data for the months of May and October.

###  **Bonus 3: Preventing SQL Syntax Issues**

One other way to ensure that the interactions and data retrievals are smooth and error-free is implementing safeguards and checks to prevent SQL syntax issues. 

_The code used in this section can be found in this git branch:[ sql-check ](https://github.com/lucasiscovici/blog-chat-with-database/tree/sql-check) _

###  **The new prompt « SQL fixer »**

To achieve that, we first create a new prompt that we call « SQL Fixer » prompt : 
    
    
    You have to rewrite the sql query which causes the errors listed bellow. You must use the table descriptions and schemas to rewrite the sql query.
    
    -- Here are the descriptions of the table schemas; please read them carefully to better understand the table:
    {descriptions}
    -- Here are the table schemas :
    {schemas}
    -- Here is the query to check:
    {query}
    -- Here are the query errors:
    {errors}
    
    Double check the SQLITE query above for common mistakes, including:
    - Using NOT IN with NULL values
    - Using UNION when UNION ALL should have been used
    - Using BETWEEN for exclusive ranges
    - Data type mismatch in predicates
    - Properly quoting identifiers
    - Using the correct number of arguments for functions
    - Casting to the correct data type
    - Using the proper columns for joins
    
    Output the final SQL query only.
    
    SQL Query:

###  **The updated chain**

Then, we update the SQL Chain class to take that SQL Fixer into account: 
    
    
    from langchain.chains.base import Chain
    
    from langchain.utilities import SQLDatabase
    from langchain.chains import LLMChain
    
    from .prompts import SQL_QUERY_PROMPT, RESPONSE_PROMPT, FACTS_PROMPT, SQL_FIXER_PROMPT
    
    
    class SQLChain(Chain):
        ...
        llm_chain_sql_fixer: LLMChain
        ...
        def _call(self, inputs, run_manager=None):
            ...
    
            # execute the sql query
            query_response = self.db.run_no_throw(sql_query)
    
            # check the sql query
            if query_response.startswith("Error: "):
                sql_query_fixed = self.llm_chain_sql_fixer.run(
                    {
                        "schemas": table_infos_str,
                        "descriptions": self.table_descriptions,
                        "errors": query_response,
                        "query": sql_query
                    }
                )
                # execute the fixed sql query
                query_response = self.db.run_no_throw(sql_query_fixed)
                sql_query = sql_query_fixed
    
            # generate the response
            response = self.llm_chain_response.run(
                {**inputs, "query": sql_query, "facts": facts, "response": query_response}
            )
    
            return {self.output_key: response}
    
        @classmethod
        def from_db_and_llm(
            cls,
            ...
            prompt_sql_fixer=SQL_FIXER_PROMPT, # new sql fixer
            table_descriptions="",
            verbose=False,
            **kwargs
        ):
            return cls(
                ...
                llm_chain_sql_fixer=LLMChain(llm=llm, prompt=prompt_sql_fixer, verbose=verbose),
                table_descriptions=table_descriptions,
                **kwargs
            )
    

###  **The run**

After making the updates, we re-run the chain on the 3 questions studied in the bonus 3: 
    
    
    print(chain("What were the revenue of SFR in 2022 ?")["output"]) 
    print(chain("in 2021 ?")["output"])
    print(chain("for that year, which months are available ?")["output"]) # FOCUS

We make just a focus on the important part of the generated « SQL query » because it’s too long: 
    
    
    ```sql SELECT strftime('%m', date) as month
    FROM data
    WHERE company = 'SFR' AND strftime('%Y', date) = '2021' AND date IS NOT NULL
    GROUP BY month
    ORDER BY month;```

And the generated « SQL fixer » prompt now is: 
    
    
    You have to rewrite the sql query which causes the errors listed bellow. You must use the table descriptions and schemas to rewrite the sql query.
    
    -- Here are the descriptions of the table schemas; please read them carefully to better understand the table:
    table;column;column_type;description
    data;date;DATE; YYYY-MM-DD date format
    data;company;CHAR; The name of the company, always capitalized
    data;sector;CHAR; The sector of the company, "ENERGY" or "TELECOMMUNICATION" OR "CONFECTIONERY", always uppercased
    data;sales;INTEGER; the sales in dollars
    data;ebitda;INTEGER; the ebitda in dollars
    data;type;CHAR; the type is "actual" (the real value) or "budget" (the budgeted value), always lowercased
    
    -- Here are the table schemas :
    
    CREATE TABLE data (
            date DATE, 
            company TEXT, 
            sector TEXT, 
            sales INTEGER, 
            ebitda INTEGER, 
            type TEXT
    )
    
    /*
    3 rows from data table:
    date    company sector  sales   ebitda  type
    2022-01-01      TotalEnergies   ENERGY  167621  29184   actual
    2022-02-01      TotalEnergies   ENERGY  6556    194393  actual
    2022-03-01      TotalEnergies   ENERGY  72097   64196   actual
    */
    -- Here is the query to check:
    ```sql SELECT strftime('%m', date) as month
    FROM data
    WHERE company = 'SFR' AND strftime('%Y', date) = '2021' AND date IS NOT NULL
    GROUP BY month
    ORDER BY month;```
    -- Here are the query errors:
    Error: (sqlite3.OperationalError) near "```sql SELECT strftime('%m', date) as month
    FROM data
    WHERE company = 'SFR' AND strftime('%Y', date) = '2021' AND date IS NOT NULL
    GROUP BY month
    ORDER BY month;```": syntax error
    [SQL: ```sql SELECT strftime('%m', date) as month
    FROM data
    WHERE company = 'SFR' AND strftime('%Y', date) = '2021' AND date IS NOT NULL
    GROUP BY month
    ORDER BY month;```]
    (Background on this error at: https://sqlalche.me/e/20/e3q8)
    
    Double check the SQLITE query above for common mistakes, including:
    - Using NOT IN with NULL values
    - Using UNION when UNION ALL should have been used
    - Using BETWEEN for exclusive ranges
    - Data type mismatch in predicates
    - Properly quoting identifiers
    - Using the correct number of arguments for functions
    - Casting to the correct data type
    - Using the proper columns for joins
    
    Output the final SQL query only.
    
    SQL Query:

After using this prompt, we can see here a focus on the generated **FIXED** « SQL query »: 
    
    
    SELECT strftime('%m', date) as month
    FROM data
    WHERE company = 'SFR' AND strftime('%Y', date) = '2021' AND date IS NOT NULL
    GROUP BY month
    ORDER BY month

And the generated response is: 
    
    
    The available sales data for the company SFR in the year 2021 is for the months of January, February, March, April, June, July, August, September, November, and December. This information was obtained by examining the 'date' column in our database for entries corresponding to the company 'SFR' and the year '2021'. It appears that the data for May and October is not available.

###  **Bonus 4: Implementing Early Stop and Clarification**

Sometimes, the chatbot can makes a bad understanding of the user’s question, and consequently generates potentially inaccurate or irrelevant responses. To resolve this problem and enhance the accuracy and the relevance of the interaction, we can make the chatbot ask for more clarification when he considers the user’s question as complex or incomplete. 

_The code used in this section can be found in this git branch:[ early-stop ](https://github.com/lucasiscovici/blog-chat-with-database/tree/early-stop) _

###  **The new prompt « Early stop question »**

To do that, we should update our prompt as you can see below: 
    
    
    -- Here is the question of the user :
    {question}
    -- Here is the conversation with the user (the last is the most recent); Use it to better understand the question of the user :
    {history}
    -- Here are the descriptions of the table schemas; please read them carefully to better understand the table:
    {descriptions}
    -- Here are the table schemas :
    {schemas}
    -- Here are the interesting facts:
    {facts}
    -- Based on the user's question, table schemas, schemas descriptions, and conversation history, consider posing a clarifying question if necessary. 
    In the tables, some columns serve as filters ("Key Columns" or "Index Columns") while others store specific data ("Data Columns" or "Value Columns").
    If you're unable to determine the correct value for any "Key" or "Index" column from the table descriptions and schemas, and it's crucial for addressing the user's query, seek further clarity.
    However, use discretion. If you genuinely cannot discern a value and deem it vital, prompt the user with a question.
    -- If you can formulate a PostgreSQL query to aptly address the user's question, return 'OK'.
    -- Your response should either be 'OK' or a clarifying question.
    

###  **The updated chain**

And we should update the class of the SQL chains to look like this: 
    
    
    ...
    from .prompts import ..., EARLY_STOP_QUESTION_PROMPT
    ...
    
    class SQLChain(Chain):
        ...
        llm_early_stop_question: LLMChain
        ...
    
        def _call(self, inputs, run_manager=None):
            ...
    
            # get facts
            facts = self.llm_chain_facts.run(
                {
                    **inputs,
                    "schemas": table_infos_str,
                    "descriptions": self.table_descriptions,
                }
            )
    
            ask_question_text = self.llm_early_stop_question.run(
                {
                    **inputs,
                    "schemas": table_infos_str,
                    "descriptions": self.table_descriptions,
                    "facts": facts,
                }
            )
    
            if ask_question_text != "OK":
                return {self.output_key: ask_question_text}
    
            ...
    
            return {self.output_key: response}
    
        @classmethod
        def from_db_and_llm(
            cls,
            ...
            prompt_early_stop_question=EARLY_STOP_QUESTION_PROMPT,
            ...
            **kwargs
        ):
            return cls(
                ...
                llm_early_stop_question=LLMChain(llm=llm, prompt=prompt_early_stop_question, verbose=verbose),
                ...
                **kwargs
            )
    

###  **The run**

After making the updates, we re-run the chain on the _« test »_ question that is incomplete: 
    
    
    print(chain("What were the revenue ?")["output"])

We can see here the new generated prompt: 
    
    
    -- Here is the question of the user :
    What were the revenue ?
    -- Here is the conversation with the user (the last is the most recent); Use it to better understand the question of the user :
    
    -- Here are the descriptions of the table schemas; please read them carefully to better understand the table:
    table;column;column_type;description
    data;date;DATE; YYYY-MM-DD date format
    data;company;CHAR; The name of the company, always capitalized
    data;sector;CHAR; The sector of the company, "ENERGY" or "TELECOMMUNICATION" OR "CONFECTIONERY", always uppercased
    data;sales;INTEGER; the sales in dollars
    data;ebitda;INTEGER; the ebitda in dollars
    data;type;CHAR; the type is "actual" (the real value) or "budget" (the budgeted value), always lowercased
    
    -- Here are the table schemas :
    
    CREATE TABLE data (
            date DATE, 
            company TEXT, 
            sector TEXT, 
            sales INTEGER, 
            ebitda INTEGER, 
            type TEXT
    )
    
    /*
    3 rows from data table:
    date    company sector  sales   ebitda  type
    2022-01-01      TotalEnergies   ENERGY  167621  29184   actual
    2022-02-01      TotalEnergies   ENERGY  6556    194393  actual
    2022-03-01      TotalEnergies   ENERGY  72097   64196   actual
    */
    -- Here are the interesting facts:
    The user's question does not provide specific details about the revenue they are interested in. However, based on the table schemas, we can infer the following:
    
    - The user might be referring to the 'sales' column as the revenue.
    - The user did not specify a particular company, sector, or date range for which they want the revenue.
    - The user did not specify whether they want the actual or budgeted revenue.
    
    Potential rewrite: "Could you please specify the company, sector, and date range for which you want to know the revenue? Also, do you want to know the actual revenue or the budgeted revenue?"
    -- Based on the user's question, table schemas, schemas descriptions, and conversation history, consider posing a clarifying question if necessary. 
    In the tables, some columns serve as filters ("Key Columns" or "Index Columns") while others store specific data ("Data Columns" or "Value Columns").
    If you're unable to determine the correct value for any "Key" or "Index" column from the table descriptions and schemas, and it's crucial for addressing the user's query, seek further clarity.
    However, use discretion. If you genuinely cannot discern a value and deem it vital, prompt the user with a question.
    -- If you can formulate a PostgreSQL query to aptly address the user's question, return 'OK'.
    -- Your response should either be 'OK' or a clarifying question.

And here is the response that we get : 
    
    
    Could you please specify the company, sector, and date range for which you want to know the revenue? Also, do you want to know the actual revenue or the budgeted revenue?

As we can see here, the chatbot has asked for more clarifications because the question was incomplete. 

##  Warnings and Considerations 

###  **Navigating Through LLMs and Hallucinations**

Being mindful of the limitations and potential pitfalls of Large Language Models (LLMs), such as hallucinations, ensures that interactions are verified and validated for accuracy and relevance. 

###  **Database Interactions and Write Permissions**

Ensuring that interactions with the database are secure and that write permissions are safeguarded protects the integrity and security of the data being interacted with. 

###  **OpenAI Usage: Cost and Latency Considerations**

Navigating the realms of OpenAI, especially with potent models like GPT-4, necessitates a mindful balance between cost management and efficient and low-latency interactions. The intricate dance of API usage, influenced by the query’s complexity and frequency, directly impacts the overall cost and demands strategic optimization to ensure technical adeptness without breaking the bank. Simultaneously, ensuring swift and responsive interactions is paramount to uphold a seamless and intuitive user experience. Thus, striking a harmonious balance between cost, efficiency, and user experience becomes the linchpin in crafting a sustainable and user-friendly chatbot interaction through OpenAI and LangChain. Finally, depending on your project, you can use Azure OpenAI to have more privacy. 

##  Conclusion 

###  **Recapitulating the Journey**

While navigating through the multifaceted journey of chatbot and database interactions, we’ve traversed from the fundamental steps of initial setup to the nuanced art of crafting insightful and explanatory answers. Our exploration took us through the pivotal steps of ensuring structured and descriptive databases, elucidating the implicit facts within user queries, and meticulously crafting responses that are not only accurate but also rich in explanation and context. Each stage of this journey, from managing the simplicity and complexity of databases to explicating the implicit facts and nuances within user interactions, has been a step towards refining and enhancing the interaction between chatbots, powered by OpenAI and LangChain, and databases. 

###  **The Road Ahead**

As we gaze into the future, the realm of chatbot and database interactions presents a canvas of endless possibilities. With ongoing advancements in natural language understanding, the pathway ahead is ripe with opportunities for crafting interactions that are even more intuitive, insightful, and seamless. The evolution of models like GPT-4 and platforms like LangChain signals a future where the conversation with databases becomes increasingly natural and user-friendly, unlocking new potentials and horizons in the world of data exploitation and interaction. 

##  References 

  * [ LangChain ](https://www.langchain.com/)
  * [ OpenAI ](https://www.openai.com/)



[ ![NLP](https://www.quantmetry.com/wp-content/uploads/2022/06/Logo-Expertise-nlp.svg) ](https://www.quantmetry.com/experts/#nlp)

Les membres de l’ [ expertise NLP ](https://www.quantmetry.com/experts/#nlp) exploitent le potentiel des données textuelles à l’aide de solutions d’IA à forte valeur ajoutée grâce à la maîtrise des technologies à l’état de l’art (modèles de deep-learning « pré-entrainés » BERT, ELMo, GPT-2 ou FlauBERT). 

* * *

![Lucas ISCOVICI](https://www.quantmetry.com/wp-content/uploads/2024/07/image.jpeg)

[ Lucas ISCOVICI  ](https://www.linkedin.com/in/lucas-iscovici/)

Data Scientist 

Data scientist with extensive experience in developing and delivering advanced machine learning solutions across diverse sectors such as Health, Cosmetics, Finance/Insurance, and Home Appliances. At Quantmetry, I apply my expertise in Natural Language Processing (NLP), Retrieval-Augmented Generation (RAG), prompt engineering, and software engineering. My role focuse on translating data insights into practical business solutions. 

![Oussama MOUSTAINE](https://www.quantmetry.com/wp-content/uploads/2024/07/photo-e1720711493467.jpg)

[ Oussama MOUSTAINE  ](https://www.linkedin.com/in/oussama-moustaine-67a183155/)

Data Scientist 

As a data scientist, with over 3 years of experience, I have worked on numerous projects across diverse sectors such as energy, insurance, and finance. Collaborating closely with fellow data scientists and engineers, I consistently aim to deliver innovative solutions in various IA domains, including Computer Vision, NLP, and Time Series analysis. 
