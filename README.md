# Census Data Analysis

A small town sits between two larger cities. The local council has one unoccupied plot of land and a limited budget. What should they build, and where should the money go after that?

This project answers both questions from a census of 7,773 residents, and the answer is a train station.
## What the data said
### Finding
### Town
### England and Wales (2021)
Adults who are likely commuters
79.2%
—
Unemployment rate
8.75%
4.3%
People per household
2.60
2.4
Largest age band
35–39, then 40–44
—
School-age share
17.79%
—


The commuter figure is the one that decides it. Nearly four in five working-age adults either work or study, and the town sits between two cities joined by a single motorway. Every one of those journeys is currently a car journey.

Unemployment running at double the national rate looks alarming until you see where it sits: concentrated in the 40 to 64 group, so it's a mid-career and pre-retirement problem rather than a young-workforce one. Different problem, different fix.

Household size slightly above the national average, with a high count of one and two person households, points to demand for smaller higher-density units rather than family housing.

## Recommendations
Build the train station. 79.2% commuter dependency against one motorway is the clearest pressure in the data. Rail takes cars off that road and reaches the largest share of the population.

Housing came second and was ruled out for now. Demand exists, but at 2.60 people per house the existing stock isn't overcrowded, so it isn't urgent. A Methodist place of worship is the one real gap in religious provision, and that can be privately funded. An emergency medical building isn't supported: infirmity rates are low and pregnancies are moderate.

Then invest in general infrastructure, then elderly care. A station attracts residents, and the existing facilities have to absorb them. After that, the pre-retirement bulge in the population pyramid becomes a care problem within about five years. Schools and employment training both matter less: the school-age share is manageable and the unemployment picture calls for targeted retraining, not a large programme.
## Data cleaning
The messy part, and most of the work. The raw file had 1,813 missing marital statuses, 474 missing household relationships, 7,721 blank infirmity fields and scattered blanks elsewhere.

Rather than dropping rows or filling with a column mean, missing values were inferred from household structure:

### Relationship to head of house. 
Ranked every household by age, made the oldest person the head, demoted duplicate heads to other relatives. Minors listed as head were reassigned to son or daughter by gender.
### Marital status. 
Anyone under 18 became Not Applicable, following the 2022 Act raising the minimum marriage age. Missing values where the relationship column said husband or wife became married. Remaining blanks over 65 became widowed, the rest single.
### Religion. 
Filled from other members of the same household where that household had one consistent religion, otherwise No Religion. Four categories with one or two entries were merged into Other Religion, including one respondent who had written "Private".
### Age. 
One blank belonged to a daughter in a household headed by a 30 year old man. The column mean of 37 would have made her older than her father, so the mean age of children under 12 was used instead.
### Infirmity.
7,721 blanks meant no disability, not missing data, so they were filled as None.

The cleaned file is saved as Cleaned_census_data.csv.
Repository contents
.

├── census-analysis/

│   ├── census.ipynb                              # cleaning, analysis, visualisation

│   └── FUNDAMENTALS OF DATA SCIENCE PROJECT.pdf  # full written report

└── README.md

The notebook shows how. The PDF explains why it matters to a council making the decision.
Built with
Python, pandas, NumPy, Matplotlib, Seaborn, Jupyter.
References
Office for National Statistics (2022) Census 2021: age structure, religion, household composition, disability, unemployment, and occupancy rating for England and Wales.

Marriage and Civil Partnership (Minimum Age) Act 2022.
Author
Rosemary Akpovi MSc Artificial Intelligence and Data Science, University of Hull


