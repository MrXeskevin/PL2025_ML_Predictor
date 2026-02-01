# Premier League 2025/26 Match Predictor

A machine learning project that predicts the outcome of the 2025/26 Premier League season using a Random Forest Classifier. The model analyzes historical match data from the past six seasons to predict final league positions and individual match outcomes.

## Overview

This project builds a classification model that takes historical Premier League data from the 2018/19 to 2023/24 seasons and generates predictions for the upcoming 2025/26 campaign. The model accounts for newly promoted teams (Leeds United, Burnley, and Sunderland) by assigning them average statistics based on the bottom three clubs from the previous season.

The predictor offers two main features:
- A predicted final league table for all 20 Premier League clubs
- I have also improved it by adding an interactive match score predictor that calculates expected goals and win probabilities

## How It Works

The script processes match data from CSV files containing every Premier League fixture from the past six seasons. For each season, it computes summary statistics for every club including points, wins, draws, losses, goals scored and conceded, and goal difference.

The Random Forest Classifier is trained using data from season n to predict outcomes in season n+1. Teams are ranked based on points, goal difference, and goals scored. The model uses a pipeline that standardizes features before training, with 100 decision trees and a maximum depth of 8 to prevent overfitting.

For match predictions, the system calculates attack and defense strength ratings for each team based on historical performance. It then uses Poisson distribution to estimate expected goals and outcome probabilities for any given fixture.

## Installation

Clone the repository and install the required dependencies:

```bash
git clone https://github.com/MrXeskevin/PL2025_ML_Predictor.git
cd PL2025_ML_Predictor
pip install -r requirements.txt
```

## Usage

Run the main prediction script from your terminal:

```bash
python pl_2025_26_prediction.py
```

The script will output:
1. A predicted league table showing all 20 clubs ranked from first to twentieth
2. An interactive prompt where you can enter two team names to predict match outcomes

Example interaction:
```
Home Team: Arsenal
Away Team: Liverpool
```

The predictor will return the most likely scoreline, expected goals (xG), and win/draw/loss probabilities.

## Data Source

The historical match data comes from open-source football CSV files available on GitHub. Each file contains 380 matches per season with columns for date, home team, final score, half-time score, and away team.

The following season files are included:
- eng1_2018-19.csv
- eng1_2019-20.csv
- eng1_2020-21.csv
- eng1_2021-22.csv
- eng1_2022-23.csv
- eng1_2023-24.csv

## Model Details

The Random Forest Classifier is configured with the following hyperparameters:
- Number of estimators: 100
- Maximum depth: 8
- Random state: 42 (for reproducibility)
- Class weight: balanced

The model uses StandardScaler for feature normalization and computes expected finishing positions by calculating probability-weighted averages across all possible league positions.

## Features

- Predicts final league standings for the 2025/26 season
- Handles newly promoted teams with intelligent default statistics
- Interactive match predictor with expected goals and outcome probabilities
- Flexible team name matching (supports partial names and common variations)
- Uses historical data to build attack and defense strength metrics

## Requirements

- Python 3.x
- numpy
- pandas
- scikit-learn
- scipy

## License

This project is open source and available under the MIT License.

## Acknowledgments

This project is forked from Erik-Cupsa/PL2025_ML_Predictor. Historical match data sourced from publicly available Premier League statistics.
