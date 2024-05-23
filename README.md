# Data Exploration and Analysis

## Table of Contents
- [Introduction](#introduction)
- [Dataset](#dataset)
- [Installation](#installation)
- [Usage](#usage)
- [Project Structure](#project-structure)
- [Data Exploration](#data-exploration)
- [Data Cleaning and Visualization](#data-cleaning-and-visualization)
- [Research Questions](#research-questions)
- [License](#license)

## Introduction
This project involves the exploration, cleaning, and visualization of a dataset related to car attributes. The aim is to gain insights into the data and answer specific research questions about car prices, fuel consumption, and power.

## Dataset
The dataset used in this project is related to various attributes of cars, including price, brand, fuel consumption, and power.

## Installation
To install the required dependencies, use the following commands:
```sh
pip install pandas
pip install numpy
pip install matplotlib
pip install seaborn
```

## Usage
1. Clone the repository.
2. Install the required dependencies as mentioned above.
3. Run the `miletone1_YahiaEhab_7037125.ipynb` notebook to execute the code.

## Project Structure
- `miletone1_YahiaEhab_7037125.ipynb`: The main Jupyter Notebook containing all the code for data exploration, cleaning, visualization, and analysis.

## Data Exploration
The project starts with loading and exploring the dataset to understand its structure and content.

### Code Example:
```python
import pandas as pd
import numpy as np

# Load data
df = pd.read_csv("data.csv")

# Display head
df.head(10)

# Description of data
print(df.describe())

# Data info
print(df.info())

# Check for nulls and duplicates
print(df.isnull().sum())
print(df.duplicated().sum())
```

## Data Cleaning and Visualization
The project includes data cleaning steps such as removing incorrect data types and handling missing values. It also involves visualizing the data to gain insights.

### Code Example:
```python
import pandas as pd

# Remove any string from attributes and leave the float
df["fuel_consumption_l_100km"] = pd.to_numeric(
    df["fuel_consumption_l_100km"].replace(regex=True, to_replace=r"[^0-9.]", value=""),
    errors="coerce",
)
df["power_kw"] = pd.to_numeric(
    df["power_kw"].replace(regex=True, to_replace=r"[^0-9.]", value=""), errors="coerce"
)

# Replace negative values with 0
df["fuel_consumption_l_100km"] = df["fuel_consumption_l_100km"].apply(lambda x: x if x > 0 else 0)
df["power_kw"] = df["power_kw"].apply(lambda x: x if x > 0 else 0)

# Visualization
import matplotlib.pyplot as plt
import seaborn as sns

# Bar Chart plot between price_in_euro and brand
plt.figure(figsize=(10, 4))
sns.barplot(
    data=df,
    x="brand",
    y="price_in_euro",
    hue="fuel_type",
    palette="Set1",
    alpha=0.7,
)
plt.xlabel("Brand")
plt.ylabel("Price in Euro")
plt.title("Price in Euro vs. Brand")
plt.show()
```

## Research Questions
The project addresses specific research questions related to car prices, fuel consumption, and power.

### Research Question 1
**Objective:** Explore the relationship between car attributes such as brand, fuel consumption, and power with car prices.

### Research Question 2
**Objective:** Examine price differences among the top 5 brands and different fuel types for German used cars in 2023.

#### Insights:
- Electric and hybrid cars are generally more expensive than petrol and diesel cars.
- Audi has the highest average used car costs in 2023, followed by Mercedes, BMW, Opel, and Volkswagen.

## License
This project is licensed under the MIT License. See the `LICENSE` file for more details.

## Notes
This project was given and managed by German International University
