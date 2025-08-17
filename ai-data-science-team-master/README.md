
</div>
<div align="center">
  <em>An AI-powered data science team of agents to help you perform common data science tasks 10X faster</em>
</div>


# Data Science and ML Automation Multi-Agent System 

**An AI-powered data science team of agents to help you perform common data science tasks 10X faster**.





---

The AI Data Science Team of Copilots includes Agents that specialize data cleaning, preparation, feature engineering, modeling (machine learning), and interpretation of various business problems like:

- Churn Modeling
- Employee Attrition
- Lead Scoring
- Insurance Risk
- Credit Card Risk
- And more



## Installation

You can install via PyPI (note that this is a beta version and breaking changes may occur until 0.1.0):

``` bash
pip install ai-data-science-team
```


## Usage

[See all examples here.](/examples)



``` python
# Import libraries
from langchain_openai import ChatOpenAI
import pandas as pd
import h2o 
import os
from ai_data_science_team.ml_agents import H2OMLAgent

# Load the data
df = pd.read_csv("data/churn_data.csv")
df

# Initialize the language model
os.environ['OPENAI_API_KEY'] = "YOUR_OPENAI_API_KEY"
llm = ChatOpenAI(model=MODEL)
llm

# Initialize the H2O ML Agent
ml_agent = H2OMLAgent(
    model=llm, 
    log=True, 
    log_path="logs/",
    model_directory="h2o_models/", 
    enable_mlflow=True, # Use this if you wish to log models to MLflow 
)
ml_agent

# Run the agent
ml_agent.invoke_agent(
    data_raw=df.drop(columns=["customerID"]),
    user_instructions="Please do classification on 'Churn'. Use a max runtime of 30 seconds.",
    target_variable="Churn"
)

# Retrieve and display the leaderboard of models
ml_agent.get_leaderboard()
```

## Contributing

1. Fork the repository
2. Create a feature branch
3. Commit your changes
4. Push to the branch
5. Create a Pull Request



