# Festo Plant for Discrete Manufacturing Developing Simulation Models for Industrial Copilots

**Technical University of Munich (TUM)**
**Siemens Technology AG**
**Course:** Software Lab 2025 

## 📌 Project Overview

This project is an implementation of both **Single Agent** and **Multi-Agent** systems that through the usage of developed tools aim to predict the wear and quality of the drilling process in a Festo Plant. With this project, new users can query the agentic system about different drilling processes and receive natural language responses from the Large Language Models. 

The goal of the project is to create an interface that allows users (with little experience about Festo Plant Drilling Processes) to get responses about different characteristics of the process, by only the usage of natural language. 

The dataset used was from: *https://www.kaggle.com/datasets/raphaelwallsberger/xai-drilling-dataset*

## ✨ Key Features & Tasks

This software implements the agentic systems and tool extensions derived from the project requirements:

### 🔹 Agentic Systems
* **Single Agent System**: Created only 1 Agent to logically respond to user's queries by handling simultaneously all tasks.
* **Multi Agent (Supervisor System)**: Implemented 3 Agents: **Quality Agent**, **Wear Agent**, **Supervisor**. These 3 agents work together to respond to queries by specializing in only 1 part of the tasks needed. 


### 🚀 Tools Created

#### Tool 1: Wear and Degradation Tool
* **Inputs**: Material to be used for drilling, feed rate when drilling [mm/min] and cutting speed [m/min].
* **Outputs**: The tool uses XGBoost to classify different probabilities of failure. By dividing the wear into 3 categories: 0 (no wear), 1 (degradation) and 2 (failure of flank), the tool outputs the probability of the system falling into each category. More information inside the Degradation Tool folder. 

#### Tool 2: Quality of Drilling Tool
* **Inputs**: Cooling rate [%] used in drilling process, feed rate, cutting speed and drill bit material.
* **Outputs**: The tool also uses a decision tree algorithm with boosting to create different criteria for decision. With these criteria, the tool is able to correctly predict if there will be Good or Bad quality of drilling following the BEF and CCF data. More information inside Quality Tool folder.


## 📂 Project Structure

```text
LLMs-Drill-Wear/
├── Literature/                  # Project assignment and theoretical background.
│   ├── presentations/           # Contains all the presentations + poster of the group.
│   └── ...
├── Dataset/                     # Folder containing dataset and initial analysis of features.
│   ├── XAI_Drilling_Dataset.csv # Datase file.
│   └── PreAnalysis/             # Analysis of feature's importance and processing time independence.
│       ├── features_importance.ipynb   # Feature's Importanced Ranked for Flank Wear Failure (FWF).
│       ├── time_issue.ipynb     # Proof that Processing Time Data is Irrelevant.
│       └── README.md            # Further explanation about pre-analysis.
├── Tools/            # Folder containing development of Wear/Degradation and Quality Tools.
│   ├── Degradation_Tool/        # Folder for the development of the degradation tool. 
│   ├── Quality_Tool/            # Folder for the development of the quality tool.
│   └── Tools_LLM/               # Folder for containing the translation of tools into python functions.
├── LLM_Choice/                  # Folder containing analysis over different LLMs performance on responses.
│   └── Tools_LLM/               # Folder containing the implementation of Degradation and Quality Tools into Python functions. 
│       ├── saved_models/        # Saved models for wear prediction from Degradation tool. 
│       └── __init__.py          # Python functions for agentic system
│   ├── correct_answers_EASY_MEDIUM.json     # JSON file with expected responses for user's queries.
│   ├── CorrectAnswers.py                    # Python file to create JSON file above.
│   ├── ChooseLLM.ipynb                      # Notebook to evaluate different LLMs performance based on accuracy and time.
│   └── README.md                            # More information regarding LLM choice for the agentic systems.
├── PromptEngineering/                  # Folder containing analysis over different prompt techniques.
│   └── Analysis_SAvsMA/           # Folder containing the analysis and comparison of both agentic systems together. 
│       ├── ...         
│       └── Comparison_SA_MA.py   # Comparison between best Single Agent and Multi-Agent systems.
│   └── MultiAgentAnalysis/           # Folder containing the analysis of Multi-Agent.
│       ├── ...         
│       └── MultiPromptAnalysis.py   # Analysis of Multi-Agent responses for different prompts.
│   └── SingleAgentAnalysis/           # Folder containing the analysis of Single Agent. 
│       ├── ...         
│       └── SinglePromptAnalysis.py.py   # Analysis of Single Agent responses for different prompts.
│   ├── Prompts_MA.ipynb     # Notebook for acquiring performance of Multi-Agent for Prompts.
│   ├── Prompts_SA.ipynb     # Notebook for acquiring performance of Single Agent for Prompts.
│   └── README.md            # More information for Prompt Engineering.
├── RESULT/      # Folder that creates final agentic systems given all performance analysis and features importance.
│   ├── ...
│   ├── MultiAgent.ipynb  # Result Product for Multi-Agent.
│   └── SingleAgent.ipynb # Result Product for Single Agent.
├── requirements.txt             # libraries dependencies  
└── README.md                    # Project documentation


```

## ⚙️ Installation To run this project:

### **Conda Environment and Libraries:**

Initially, it is necessary to create a virtual environment for python. For example, creating a conda environment. 
All the documentation is available online or at the following link:

After this, install all the required packages by using the following commands:
```bash
conda activate my_env
pip install -r requirements.txt
```

With this, all the packages are installed for the right usage of the repository. 

### **Ollama and Langchain:**

For developing the LLMs and Prompt Engineering, it is necessary to use Ollama's library. Some more documentation about how to install it and how to incorporate it with Langchain is available in the following links:

* https://ollama.com/

* https://docs.langchain.com/oss/python/integrations/providers/ollama


## 👥 Contributors

* **Eduardo Silva (03805057) eduardo.silva@tum.de** - *Responsible for LLM choice, Agentic System, Prompt Engineering and Code Documentation*
* **Adrian Almohalla (03804037) adrian.almohalla@tum.de** - *Resposible for Degradation/Wear tool literature and development*
* **Nien-Ying Lin (03803153) go57vov@tum.de** - *Responsible for Quality tool literature and development* 
