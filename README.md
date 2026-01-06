# Machine Learning: Group 19 - Balkan Brothers
# Court Dynamics
Team Members:
Yigit Doyranli      ID 314811
Luka Burmazevic     ID 314571
Cinar Yildiz        ID 320721

## Section 1 Introduction

The objective of this project is to analyze how NBA players’ performance evolves over time and how different statistical profiles relate to player roles within a team.

Rather than focusing on prediction or classification, this project adopts an exploratory and interpretative approach. Using historical player statistics from multiple seasons, we aim to uncover underlying performance patterns and group players based on similarities in their playing style and contribution.

The analysis is based on the basketball.db dataset, which contains player-level and team-level statistics such as scoring efficiency, assists, defensive indicators, and season information.  
This project aligns with the Court Dynamics perspective, where understanding player development, role differentiation, and performance trajectories is more important than maximizing predictive accuracy.

## Section 2 Methods

### Data Sources and Environment

The dataset is stored in a relational database basketball.db.  
We used Python for data manipulation, visualization, and machine learning analysis.

Main libraries used:
- Python 3.11
- pandas
- numpy
- scikit-learn
- matplotlib

## Data Integration and Cleaning

The raw data is distributed across multiple tables, including player statistics, team information, and draft data.  
We merged these tables to create a unified player-season dataset.

Throughout this procedure:
The draft table's inconsistencies have been fixed.
Columns that are unnecessary are eliminated.
Every observation is guaranteed to reflect a distinct player-season.

This step is necessary to obtain a clean and consistent dataset suitable for further analysis.

### Feature Selection and Preprocessing

Since clustering algorithms rely on distance measures, we focus exclusively on numerical performance features.

To prepare the dataset:
- Player identifiers, names, years, and positions are among the metadata that are eliminated.
-The only numerical features that are kept are those that have no missing values.
-To guarantee that variables on various scales contribute equally, all features are standardized.

These choices help avoid distortions in distance calculations and improve the interpretability of the resulting clusters.

## Problem Formulation

The project is formulated as a clustering problem.

There are no true labels or a target variable.  
The goals are to find natural player groupings using statistical profiles and examine these groups in terms of basketball roles and performance trends.
## Clustering Algorithms

We experiment with multiple clustering techniques to explore the structure of the data:

- **K-Means Clustering**  
  Chosen for its simplicity and interpretability allowing us to identify compact and separated player groups.

- **Hierarchical (Agglomerative) Clustering**  
  Used to analyze hierarchical relationships between players and observe how groups form at different similarity levels.

- **Gaussian Mixture Model (GMM)**
 We used a Gaussian Mixture Model because it can handle flexible and overlapping clusters. This is useful for player data, where roles are not always clearly separated and can change gradually

(Used more than one clustering method because it allows us to compare results and assess the strength of the discovered patterns).

### Model Evaluation

Since clustering does not rely on labeled data, we used an internal evaluation metric which is :

**Silhouette Score**

This metric measures how well each player fits within its assigned cluster compared to other clusters.  
It provides a balance between cluster cohesion and separation and allows fair comparison across different clustering configurations.

## Section 3 Experimental Design

### Purpose of the Experiments

The purpose of the experiments is to evaluate whether clustering techniques can meaningfully group NBA players based on performance metrics and whether these groups are interpretable in a basketball context.

Each experiment explores the impact of different algorithms and cluster numbers on the quality of the resulting groupings.

### Baselines

As a baseline, we used K-Means clustering with default hyperparameters.

This baseline provides a simple reference point to assess whether more refined clustering choices improve structure and interpretability.
### Experimental Procedure

For each clustering method:
The algorithm is applied to the standardized dataset.
Different numbers of clusters are tested.
The Silhouette Score is computed for each configuration.
Cluster distributions are visually inspected to support interpretability.

Conclusions are based on data and consistent across experiments (thanks to this methodical process).
### Evaluation Metrics

The primary evaluation metric used in all experiments is the Silhouette Score.

It is chosen because:
-it does not require labeled data
-it provides an intuitive measure of clustering quality
-and it allows comparison across different clustering methods and parameters.

## Section 4 Results

### Main Findings

Our clustering analysis reveals clear and meaningful groupings of NBA players based on their statistical performance profiles.

Using the Silhouette Score, we observe that both K-Means and hierarchical Clustering are able to identify structured clusters, but K-Means generally provides more compact and well-separated groups. This suggests that players can be grouped into distinct performance-based roles using numerical features alone.

The resulting clusters reflect different types of players, such as:
- high-usage offensive players,
- more balanced all-around contributors,
- and players with lower statistical impact.

These results support the idea that clustering can capture underlying role patterns without relying on predefined labels or positions.

---

### Placeholder Figure

**Figure 1: Silhouette Score for Different Numbers of Clusters (K-Means and Agglomerative Clustering)**  

(This figure is generated from the code and shows how clustering quality changes as the number of clusters varies.)



### Placeholder Table

**Table 1: Average Feature Values per Cluster (K-Means)**  

(This table summarizes the main statistical characteristics of each cluster, helping to interpret the identified player groups.)


## Section 5 Conclusions

### Take-away Message

In this project, we applied clustering techniques to NBA player statistics to explore performance patterns and role dynamics.  
Our findings show that unsupervised learning methods can effectively group players based on similar performance characteristics, offering an interpretable view of player roles and development without relying on explicit labels.

This approach aligns well with the Court Dynamics perspective, where understanding structure and evolution is more important than prediction.



### Limitations and Future Work

Even though the clustering results are instructive, there are still some unanswered questions.  
Only numerical characteristics are used in the analysis, and contextual elements like team tactics, coaching choices, or injuries are not specifically taken into consideration.

Future work could include:
- Using temporal analysis to monitor players movements between clusters over time,Including advanced or contextual metrics,
- Investigating different clustering methods to confirm the patterns found.

These extensions could provide deeper insights into player evolution and long-term performance dynamics.

End of the report...



