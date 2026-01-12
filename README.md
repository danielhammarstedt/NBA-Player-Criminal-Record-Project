# NBA Crime Library: Building a dataset + exploratory analysis (Scripting Languages project)

## Goal
In this project, I build a structured dataset by combining two sources:
1) a web-scraped dataset from the **NBA Crime Library**, and  
2) an external **NBA player database** used for augmentation and further analysis.

---

## Dataset 1: NBA Crime Library (scraped dataset)
The NBA Crime Library is a curated website that documents arrests involving NBA players. The site is organized as **one webpage per player**, but a single player page can include **multiple arrest events** (different dates, charges, or incidents across years).

To reflect this structure correctly, I convert the site into a tabular dataset where **each row represents one arrest record** (not one player). This avoids collapsing multiple incidents into a single row and makes it possible to study time trends and repeat offenders.

For each arrest record, I extract fields such as:
- Player name  
- Arrest date  
- Charge(s)  
- Crime category (based on “Reason for arrest” tags on the website)  
- Additional information when available (e.g., franchise, age, narrative details, and the original post URL)

---

## Dataset 2: Kaggle NBA Player Database (augmentation dataset)
To go beyond the information available on the NBA Crime Library site, I augment the scraped arrest records with the Kaggle **“NBA Players Database”** (`PlayerIndex_nba_stats.csv`). This dataset includes:
- Player profile information (position, height, weight, college, country)
- Draft information (draft year/round/number)
- Basic performance indicators (PTS/REB/AST)
- Team-related fields (team city, team ID, roster status)

Because the two datasets do not share a unique identifier, I link them using **player names** (after cleaning and normalizing names to maximize matching accuracy). After matching, each arrest record can include additional player variables, enabling descriptive comparisons such as whether certain crime categories are more common among particular position groups, draft tiers, or performance profiles.

---

## Research questions
1. **Crime types:** Which crime categories occur most frequently in the NBA Crime Library dataset?
2. **Augmentation:** Can these arrest records be enriched with basic player information (e.g., position, heigh
