<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:0D0221,50:3D155F,100:A855F7&height=220&section=header&text=Netflix%20Data%20Analysis&fontSize=42&fontColor=FFFFFF&animation=fadeIn&fontAlignY=35&desc=Exploratory%20Data%20Analysis%20on%20a%20Movie%20Metadata%20Dataset&descAlignY=55&descSize=18" width="100%" alt="header banner"/>

<img src="https://readme-typing-svg.demolab.com?font=Fira+Code&weight=500&size=20&duration=3000&pause=1000&color=A855F7&center=true&vCenter=true&width=600&lines=Cleaning+%2B+Exploring+9%2C800%2B+Movies+%F0%9F%8E%AC;Genre+Trends+%7C+Popularity+%7C+Ratings;Pandas+%2B+Seaborn+%2B+Matplotlib" alt="Typing SVG"/>

<br/>

<img src="https://img.shields.io/badge/Python-3.x-A855F7?style=for-the-badge&logo=python&logoColor=white&labelColor=0D0221" alt="Python"/>
<img src="https://img.shields.io/badge/Pandas-Data%20Wrangling-A855F7?style=for-the-badge&logo=pandas&logoColor=white&labelColor=0D0221" alt="Pandas"/>
<img src="https://img.shields.io/badge/NumPy-Numerical%20Ops-A855F7?style=for-the-badge&logo=numpy&logoColor=white&labelColor=0D0221" alt="NumPy"/>
<img src="https://img.shields.io/badge/Matplotlib-Visualization-A855F7?style=for-the-badge&labelColor=0D0221" alt="Matplotlib"/>
<img src="https://img.shields.io/badge/Seaborn-Statistical%20Plots-A855F7?style=for-the-badge&labelColor=0D0221" alt="Seaborn"/>
<img src="https://img.shields.io/badge/Jupyter-Notebook-A855F7?style=for-the-badge&logo=jupyter&logoColor=white&labelColor=0D0221" alt="Jupyter"/>
<img src="https://img.shields.io/badge/License-MIT-A855F7?style=for-the-badge&labelColor=0D0221" alt="License"/>

</div>

<br/>

## 📋 Table of Contents
- [Overview](#-overview)
- [Dataset](#-dataset)
- [Tech Stack](#-tech-stack)
- [Data Cleaning & Preprocessing](#-data-cleaning--preprocessing)
- [Key Insights](#-key-insights)
- [Visualizations](#-visualizations)
- [Project Structure](#-project-structure)
- [Getting Started](#-getting-started)
- [License](#-license)
- [Connect](#-connect)

---

## 🎬 Overview

An end-to-end **exploratory data analysis (EDA)** on a dataset of ~9,800 movie titles. The notebook walks through cleaning a messy real-world CSV, engineering a few analytical features, and visualizing what shows up in the data around a title's popularity, audience rating, genre mix, and release era.

Everything runs inside a single, self-contained Jupyter Notebook — `netflix_data_analysis.ipynb`.

## 📊 Dataset

The raw data lives in `mymoviedb.csv` — a TMDB-style movie metadata export.

| | Raw | After Cleaning |
|---|---|---|
| **Rows** | 9,837 | 25,792 *(one row per genre, after exploding multi-genre titles)* |
| **Columns** | 9 | 7 |

**Original columns:** `Release_Date`, `Title`, `Overview`, `Popularity`, `Vote_Count`, `Vote_Average`, `Original_Language`, `Genre`, `Poster_Url`

> 💡 The CSV itself isn't tracked in this repo (standard practice for raw data). Drop your own copy of `mymoviedb.csv` in the project root before running the notebook.

## 🧰 Tech Stack

| Purpose | Tools |
|---|---|
| Data wrangling | `pandas`, `numpy` |
| Visualization | `matplotlib`, `seaborn` |
| Environment | Jupyter Notebook |

## 🧹 Data Cleaning & Preprocessing

The notebook takes the raw CSV through seven steps before any analysis happens:

1. **Type correction** — `Vote_Average` and `Vote_Count` coerced from `object` to numeric
2. **Date parsing** — `Release_Date` parsed to `datetime`, then reduced to release **year**
3. **Column pruning** — dropped `Overview`, `Original_Language`, `Poster_Url` (not needed for this analysis)
4. **Genre explosion** — multi-genre strings like `"Action, Adventure"` are split and exploded into one row per genre
5. **Missing values** — remaining nulls dropped
6. **Rating binning** — `Vote_Average` bucketed into four quantile-based labels:

   ```python
   df['Vote_Average_Labels'] = pd.qcut(df['Vote_Average'], q=4, labels=False, duplicates='drop')
   # 0: below average · 1: average · 2: good · 3: very good
   ```

7. **Deduplication** — exact duplicate rows removed

**Result:** a tidy 25,792 × 7 frame, one genre per row, ready to plot.

## 🔍 Key Insights

| | Title | Popularity | Rating |
|---|---|---|---|
| 🔥 **Most popular** | Spider-Man: No Way Home (2021) | 5,083.95 | Very good |
| 🧊 **Least popular** *(tied)* | The United States vs. Billie Holiday (2021) · Threads (1984) | 13.35 | Good · Very good |

- **Genre mix** skews heavily toward **Drama, Comedy, and Action** — the three most-tagged genres by a clear margin — while Western and TV Movie are the rarest.
- **Ratings** are fairly evenly spread across the four quantile bands, with a slight lean toward the *below average* bucket.
- **Release years** are heavily right-skewed — the vast majority of titles are from the last two decades, with a sharp spike around 2020–2021, and only a thin tail of titles going back to the early 1900s.

## 📈 Visualizations

<div align="center">

**Genre Distribution**

<img src="assets/genre_distribution.png" width="500"/>

**Vote Average Distribution**

<img src="assets/vote_average_distribution.png" width="500"/>

**Release Year Distribution**

<img src="assets/release_year_distribution.png" width="500"/>

</div>

## 📁 Project Structure

```
netflix-data-analysis/
├── netflix_data_analysis.ipynb     # Main analysis notebook
├── mymoviedb.csv                   # Raw dataset (add your own copy)
├── assets/                         # Exported plots used in this README
│   ├── genre_distribution.png
│   ├── vote_average_distribution.png
│   └── release_year_distribution.png
├── requirements.txt
└── README.md
```

## 🚀 Getting Started

```bash
# Clone the repo
git clone https://github.com/Suman18-bit/netflix-data-analysis.git
cd netflix-data-analysis

# Install dependencies
pip install -r requirements.txt

# Launch the notebook
jupyter notebook netflix_data_analysis.ipynb
```

**`requirements.txt`**
```
pandas
numpy
matplotlib
seaborn
jupyter
```

## 📝 License

Released under the MIT License — feel free to use, modify, and build on this.

## 🤝 Connect

<div align="center">

<a href="https://github.com/Suman18-bit"><img src="https://img.shields.io/badge/GitHub-Suman18--bit-A855F7?style=for-the-badge&logo=github&logoColor=white&labelColor=0D0221"/></a>
<a href="https://linkedin.com/in/suman-seth-b05417324"><img src="https://img.shields.io/badge/LinkedIn-Suman%20Seth-A855F7?style=for-the-badge&logo=linkedin&logoColor=white&labelColor=0D0221"/></a>

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:A855F7,100:0D0221&height=100&section=footer" width="100%"/>

</div>
