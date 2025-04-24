# 🌟 PlotSense: AI-Powered Data Visualization Assistant

## 📌 Overview

**PlotSense** is an AI-powered assistant that helps data professionals and analysts make smarter, faster, and more explainable data visualizations. Whether you're exploring a new dataset or building dashboards, PlotSense simplifies the process with:

- ✅ Smart Visualization Suggestions - Recommends the best plots based on your data structure and relationships.
- 🧠 Natural Language Explanations – Automatically explains charts in plain English.
- 🔗 Seamless Integration – Works out of the box with pandas, matplotlib, and seaborn.

Let AI supercharge your EDA (Exploratory Data Analysis).

## ⚡ Quickstart

### 🔧 Install the package

```bash
pip install plotsense
```

### 🧠 Import PlotSense:

```bash
import plotsense as ps
from plotsense import recommender, generate_plot, explainer, 
```
### 🔐 Authenticate with Groq API:
Get your free API key from Groq Cloud https://console.groq.com/home

```bash
import os
# Set GROQ_API_KEY environment variable
os.environ['GROQ_API_KEY'] = 'your-api-key-here'

#or

# Set API key (one-time setup)
ps.set_api_key("your-api-key-here")
```

## 🚀 Core Features
### 🎯 1. AI-Recommended Visualizations
Let PlotSense analyze your data and suggest optimal charts.

```bash
import pandas as pd
# Load your dataset (e.g., pandas DataFrame)
df = pd.read_csv("data.csv")

# Get AI-recommended visualizations
suggestions = ps.recommender(df)
print(suggestions)
```
### 📊 Sample Output:
```bash
	plot_type	variables	       rationale	                                    ensemble_score	model_agreement	    source_models
0	hist	    age	            Shows the distribution of passenger ages, help...	0.50	2	[llama3-70b-8192, llama-3.3-70b-versatile]
1	scatter	    age, fare	    Reveals any relationships between passenger fa...	0.50	2	[llama3-70b-8192, llama-3.3-70b-versatile]
2	hist	    fare	        Displays the distribution of fare values, help...	0.50	2	[llama3-70b-8192, llama-3.3-70b-versatile]
3	scatter 	age, sibsp	    Reveals any relationships between passenger ag...	0.50	2	[llama3-70b-8192, llama-3.3-70b-versatile]
4	bar	        survived, who	Compares the survival rates across different p...	0.50	2	[llama3-70b-8192, llama-3.3-70b-versatile]
5	scatter	    fare, parch	    Reveals any relationships between passenger fa...	0.50	2	[llama3-70b-8192, llama-3.3-70b-versatile]
6	hist	    sibsp	        Displays the distribution of the number of sib...	0.50	2	[llama3-70b-8192, llama-3.3-70b-versatile]
7	bar	        deck, survived	Compares the survival rates across different d...	0.50	2	[llama3-70b-8192, llama-3.3-70b-versatile]
8	pie	        alive	        Displays the proportion of passengers who surv...	0.50	2	[llama3-70b-8192, llama-3.3-70b-versatile]
9	bar	        pclass, survived	Compares the survival rates across different p...	0.25	1	[llama3-70b-8192]
10	pie	        sex	Displays the proportion of male and female pas...	            0.25	1	[llama3-70b-8192]
11	boxplot 	fare	Visualizes the distribution of fare values and...	        0.25	1	[llama3-70b-8192]
12	line	    parch, sibsp	Shows the relationship between the number of s...	0.25	1	[llama3-70b-8192]
13	bar	        embarked, survived	Compares the survival rates across different e...	0.25	1	[llama3-70b-8192]
14	violinplot	fare, pclass	Visualizes the distribution of fare values acr...	0.25	1	[llama3-70b-8192]
15	heatmap	    pclass, sex, survived	Identifies correlations between passenger clas...	0.25	1	[llama3-70b-8192]
```

### 📈 2. One-Click Plot Generation
Generate recommended charts instantly:

```bash
plot1 = ps.generate_plot(df, suggestions[0]) # This will plot a bar chart with variables 'survived', 'pclass'
plot2 = ps.generate_plot(df, suggestions[1]) # This will plot a bar chart with variables 'survived', 'sex'
plot3 = ps.generate_plot(df, suggestions[2]) # This will plot a histogram with variable 'age'
```
🎛️ Want more control?

``` bash
plot1 = ps.generate_plot(df, suggestions[0], x='pclass', y='survived') 
```

### 🧾 3. AI-Powered Plot Explanation
Turn your visualizations into stories with natural language insights:

``` bash
explanation = ps.explainer(plot1)

print(explanation)
```

### ⚙️ Advanced Options
- Custom Prompts: You can provide your own prompt to guide the explanation

``` bash
explanation = refine_plot_explanation(
    fig,
    prompt="Explain the key trends in this sales data visualization"
)
```
- Multiple Refinement Iterations: Increase the number of refinement cycles for more polished explanations:

```bash  
explanation = refine_plot_explanation(fig, iterations=3)  # Default is 2
```
- Using Different Models: The package automatically selects the best available model, but you can specify models:

``` bash
explanation = refine_plot_explanation(fig, model_rotation=['llama-3.2-90b-vision-preview'])  # Use only this model
``` 

## 🔄 Combined Workflow: Suggest → Plot → Explain
``` bash
suggestions = ps.recommender(df)
plot = ps.generate_plot(df, suggestions[0])
insight = ps.explainer(plot)
```

## 🤝 Contributing
We welcome contributions!

### Branching Strategy
- main → The stable production-ready version of PlotSense.
- dev → Active development
- feature/<feature-name> → Branches for specific features (e.g., feature/ai-visualization-suggestions).

### 💡 How to Help
- 🐞 **Bug Reports** → GitHub Issues
- 💡 **Suggest features** → Open a discussion
- 🚀 **Submit PRs** → Fork → Branch → Test → Pull Request

### 📅 Roadmap
- More model integrations
- Automated insight highlighting
- Jupyter widget support

### 📥 Install or Update
``` bash
pip install --upgrade plotsense  # Get the latest features!
```
## 🛡 License
MIT License (Open Source)

## 🔐 API & Privacy Notes
- Your API key is securely held in memory for your current Python session.
- All requests are processed via Groq's API servers—no data is stored locally by PlotSense.
- Requires an internet connection for model-backed features.

Let your data speak—with clarity, power, and PlotSense.
📊✨





