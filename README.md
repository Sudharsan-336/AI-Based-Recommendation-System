*COMPANY:* CODTECH IT SOLUTIONS

*NAME:* SUDHARSAN R

*INTERN ID:* CT06DY2993

*DOMAIN:* JAVA PROGRAMMMING

*DURATION:* 6 WEEKS

*MENTOR:* NEELA SANTHOSH


# AI-Based Recommendation System (Java + Apache Mahout)

This project implements an **AI-based recommendation system** using **Apache Mahout** — a powerful machine learning library for collaborative filtering.  
It analyzes user-item interactions and provides **personalized recommendations** based on user similarity and preferences.


## Features

- User-based collaborative filtering  
- Uses **Pearson Correlation Similarity** for user similarity  
- Reads input data from a CSV file  
- Generates **top-N recommendations** for each user  
- Estimates user-item preference scores  
- Built using **Maven** for easy dependency management  


## Tech Stack

| Category | Technologies |
|-----------|---------------|
| **Language** | Java (JDK 17) |
| **Framework / Build Tool** | Apache Maven |
| **Library** | Apache Mahout 0.9 |
| **Logging** | Commons Logging |
| **I/O Utility** | Apache Commons IO |
| **Dataset Format** | CSV (`userID, itemID, rating`) |


## Folder Structure
AI-Based-Recommendation-System/
│
├── data/
│ └── ratings.csv
│
├── src/
│ ├── main/
│ │ └── java/
│ │ └── codtech/
│ │ ├── SampleRecommender.java
│ │ └── App.java
│ └── test/
│ └── java/
│ └── codtech/
│ └── AppTest.java
│
├── pom.xml
└── README.md



