---
layout: project
type: project
image: img/CITRUS.PNG
title: "Hawaii Bird Populations Data Visualization"
date: 2024
published: true
labels:
  - Python
  - CSV files
  - VSCode
summary: "A research project for the Hawaii Data Science Institute's Cyberinfrastructure Training for Undergraduates in Summer program. Python and the Python libraries Pandas, NumPy, and Seaborn were used to manipulate csv data and create data visualizations of birds sighted in Hawaii by year, species, and geographical origin."
---

<img class="img-fluid" src="../img/logo_5.png"> 

As a part of the Hawaii Data Science Institute's Cyberinfrastructure Training for Undergraduates in Summer (CITRUS) program, I learned data visualization skills with Python and the Python libraries Pandas, NumPy, and Seaborn. My research project was studying bird populations in Hawaii, by using CSV data of birds sighted in transects by the Hawaii Forest Bird Survey, done in 1977 and 2015. The dataset was found on [US Geological Survey](https://www.usgs.gov/) website.

VSCode was used to condense the data into a more managable format, with Python dataframes, and translate the abbreviated bird codes to their names, and add their geographical origin. Then, the Pandas and Seaborn libraries were used to visualize the data to compare the change in population of birds by the year, and their species or geographical origin. From this, conclusions could be made about the trajectory of bird populations in Hawaii, and more research questions could be formulated. 

The full presentation can be viewed on [Canva](https://www.canva.com/design/DAGID3fbhmw/5fEp1DBwysevsWmc7BMkeA/edit?utm_content=DAGID3fbhmw&utm_campaign=designshare&utm_medium=link2&utm_source=sharebutton). 

Here is some example code to illustrate the data processing and visualization that was done:

```python
import pandas as pd

# Load the dataframes from CSV files
df_1977 = pd.read_csv('HaBiTATS_bird_data_1977.csv')
df_2015 = pd.read_csv('HaBiTATS_bird_data_2015.csv')

# Extract bird columns from both datasets (excluding first four columns)
bird_codes_1977 = set(df_1977.columns[4:])
bird_codes_2015 = set(df_2015.columns[4:])

# Union of bird codes from both years
all_bird_codes = bird_codes_1977.union(bird_codes_2015)

# Create empty DataFrames to store summed populations
df_1977_sums = pd.DataFrame(columns=list(all_bird_codes))
df_2015_sums = pd.DataFrame(columns=list(all_bird_codes))

# Fill in sums for 1977 data
for bird_code in all_bird_codes:
    if bird_code in df_1977.columns:
        df_1977_sums[bird_code] = [df_1977[bird_code].sum()]
    else:
        df_1977_sums[bird_code] = [0]

# Fill in sums for 2015 data
for bird_code in all_bird_codes:
    if bird_code in df_2015.columns:
        df_2015_sums[bird_code] = [df_2015[bird_code].sum()]
    else:
        df_2015_sums[bird_code] = [0]

# Concatenate sums into a single DataFrame with year labels
df_pops_union = pd.concat([df_1977_sums, df_2015_sums], keys=['1977', '2015'])

# Transpose to have bird names as rows and years as columns
df_pops_union = df_pops_union.transpose()

# Reset index to include bird names as a column
df_pops_union.reset_index(inplace=True)
df_pops_union.rename(columns={'index': 'bird_code'}, inplace=True)

# Sort by bird codes in alphabetical order
df_pops_union = df_pops_union.sort_values(by='bird_code')

# Reset index for a clean structure
df_pops_union.reset_index(drop=True, inplace=True)

# Drop rows with bird codes OUXX & UNBI
df_pops_union = df_pops_union.drop([23, 29])

# Reset index for a clean structure
df_pops_union.reset_index(drop=True, inplace=True)

# Add bird names and origin as lists
name = [
    "Akiapolaau", "Apapane", "California Quail", "Common Myna", "Erckel's Francolin",
    "Gambel's Quail", "Hawaii Akepa", "Hawaii Amakihi", "Hawaii Elepaio", "Hawaiian Goose (Nene)",
    "Hawaii Creeper (Alawi)", "House Finch", "House Sparrow", "Hawaiian Hawk",
    "Scarlet Honeycreeper (Iiwi)", "Japanese Bush-Warbler", "Japanese White-eye", "Kalij Pheasant",
    "Melodius Laughing-Thrush", "Northern Cardinal", "Northern Mockingbird", "Nutmeg Mannikin",
    "Hawaiian thrush (Omao)", "Red-billed Leiothrix", "Ring-necked Pheasant", "Saffron Finch",
    "Sky Lark", "Spotted Dove", "Wild Turkey", "Yellow-fronted Canary", "Zebra Dove"
]
origin = [
    "Hawaii", "Hawaii", "North America", "Asia", "Africa", "North America", 
    "Hawaii", "Hawaii", "Hawaii", "Hawaii", "Hawaii", 
    "North America", "Europe", "Hawaii", "Hawaii", 
    "Asia", "Asia", "Asia", "Asia", "South America", 
    "North America", "Asia", "Hawaii", "Asia", 
    "North America", "South America", "Europe", "Asia", 
    "North America", "Africa", "Asia"
]

# Add the lists as a new column
df_pops_union["Name"] = name
df_pops_union["Origin"] = origin

# Print the resulting DataFrame
print(df_pops_union)
```
``` python
# Convert columns to NumPy arrays
names = df_pops_union['Name'].to_numpy()
origins = df_pops_union['Origin'].to_numpy()
pop_1977 = df_pops_union['1977'].to_numpy()
pop_2015 = df_pops_union['2015'].to_numpy()

# Plotting
plt.figure(figsize=(16, 8))  # Increased figure width and height

# Loop through each bird species and plot bars
bar_width = 0.4
indices = np.arange(len(names)) * 2  # Increase spacing between bars

for i, (name, origin) in enumerate(zip(names, origins)):
    color = origin_colors[origin]
    bar1 = plt.bar(indices[i] - bar_width/2, pop_1977[i], width=bar_width, color=color, alpha=0.6, label=f'{origin} (1977)' if i == 0 else "")
    bar2 = plt.bar(indices[i] + bar_width/2, pop_2015[i], width=bar_width, color=color, alpha=0.3, label=f'{origin} (2015)' if i == 0 else "")
    
    # Annotate the bars with the population numbers
    if pop_1977[i] < 50:
        plt.text(indices[i] - bar_width/2, pop_1977[i] + 1, str(pop_1977[i]), ha='center', va='bottom', fontsize=9)
    else:
        plt.text(indices[i] - bar_width/2, pop_1977[i] + 10, str(pop_1977[i]), ha='center', va='bottom', fontsize=9)
    
    if pop_2015[i] < 50:
        plt.text(indices[i] + bar_width/2, pop_2015[i] + 1, str(pop_2015[i]), ha='center', va='bottom', fontsize=9)
    else:
        plt.text(indices[i] + bar_width/2, pop_2015[i] + 10, str(pop_2015[i]), ha='center', va='bottom', fontsize=9)

# Add labels and title
plt.title('Observed Population of Bird Species in Hawaii 1977 vs 2015')
plt.xlabel('Bird Species')
plt.ylabel('Observed Population')

# Set x-ticks to bird names and rotate them
plt.xticks(indices, names, rotation=60, ha='right')

# Set logarithmic scale for y-axis to spread out the smaller values
plt.yscale('log')

# Create a custom legend
handles = []
for origin, color in origin_colors.items():
    handles.append(plt.Line2D([0], [0], color=color, lw=4, alpha=0.6, label=f'{origin} (1977)'))
    handles.append(plt.Line2D([0], [0], color=color, lw=4, alpha=0.3, label=f'{origin} (2015)'))
plt.legend(title='Origin & Year', handles=handles, loc='upper left', bbox_to_anchor=(.965, 1))

# Adjust layout to fit everything
plt.tight_layout()

# Show the plot
plt.show()

```

