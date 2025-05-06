<h4 align='center'> Structured Data Analysis – Advanced League </h4>

<h1 align='center'> 11th Big Contest 2023  </h1>

<h3 align='center'> Optimizing Classical Concert Pricing at Seoul Arts Center </h3>

<h3 align='center'> 🎻 </h3>

<div align='center'>

<table>
    <thead>
        <tr>
            <th colspan="4"> Miraclassic de BOAZ </th>
        </tr>
    </thead>
    <tbody>
        <tr>
          <tr>
            <td align='center'><a href="https://github.com/jwshin0908"><img src="https://avatars.githubusercontent.com/u/59306720?v=4" width="100" height="100"></td>
            <td align='center'><a href="https://github.com/yeoniiii"><img src="https://avatars.githubusercontent.com/u/76769871?v=4" width="100" height="100"></td>
            <td align='center'><a href="https://github.com/noooey"><img src="https://avatars.githubusercontent.com/u/66217855?v=4" width="100" height="100"></td>
            <td align='center'><a href="https://github.com/youjin0450"><img src="https://avatars.githubusercontent.com/u/66248758?v=4" width="100" height="100"></td>
          </tr>
          <tr>
            <td align='center'>Jaewook Shin</td>
            <td align='center'>Hyeyeon Kim</td>
            <td align='center'>Kyuyeon Park</td>
            <td align='center'>Yujin Choi</td>
          </tr>
        </tr>
    </tbody>
</table>

</div>

&nbsp;  

<h3 align='center'> <a href="https://n.news.naver.com/mnews/article/025/0003328491?sid=103"> 🏆Grand Prize🏆 </a> </h3>  
<h3 align='center'> (Minister of Science and ICT Award) </h3>

<div align='center'>



</div>

&nbsp;  
&nbsp;  

## 🎯 Project Goal
1. **Design a pricing model that accommodates a diverse range of audience needs**,  
   - Addressing the limitations of the current pricing system, which overlooks varying interests and preferences  
   - Proposing new seat grouping standards based on audience profiles and concert characteristics  
   - Enhancing accessibility and enjoyment for all concertgoers

2. **Ensure transparency in pricing decisions through data-driven justification**,  
   - Providing logical, evidence-based pricing grounds  
   - Making the pricing strategy more open and trustworthy  
   - Empowering audiences with clear and reliable pricing information

## 🧠 Summary
- Data preprocessing & EDA
- Audience Seat Preference Patterns by Genre
- Demand Prediction Modeling
- Price Modeling

### 1️⃣ Audience Seat Preference Patterns by Genre
We hypothesized that seat preferences would vary by genre, so we split the data by genre and performed K-Means clustering on seat-level data within each group.  
> ![f3fa27f3abd635f7](https://github.com/jwshin0908/BigContest_2023/assets/66217855/6b9df07c-0106-4154-924a-168759b4fa35)
> To determine the optimal number of clusters, we analyzed the Elbow Curve along with the average and distribution of silhouette coefficients.
- **Left (Symphony):** Preference for Block D over Block B (left side), possibly due to the orchestra layout where soloists face the conductor’s left
- **Middle (Classical):** Slight preference for central seating compared to symphony; extreme side seats may distort balance between instruments
- **Right (Choral):** Strong preference for broad central zones, offering balanced audio from diverse vocal sections

### 2️⃣ Demand Prediction Modeling
We performed two separate regression tasks:

1. **R: General reservation rate**  
2. **M: Membership conversion rate**

#### 🎯 Input Features:
- Performance start time  
- Pre-sale status  
- Genre  
- International artist (yes/no)  
- Running time  
- Day of week  
- Month

#### ⚙️ Model Training:
- Data split: 80% train / 20% test  
- Cross-validation: 5-fold CV during GridSearch  
- Evaluation metrics: MSE, MLSE

#### 📊 Model Performance Comparison:
> ![image](https://github.com/user-attachments/assets/064e664a-2fd4-4c04-8de2-4f4c732e7e83)
> CatBoost showed the lowest MSE, so it was selected as the final model for predicting general reservation rate (R).

> ![image](https://github.com/user-attachments/assets/a85bfe9f-29b9-44b3-85ca-e549e0967907)
> Although MLP achieved the lowest MSE for membership conversion rate (M), CatBoost was chosen for its better interpretability.

*Comparison of MSE and MLSE scores across 6 regression models.*  

SHAP value analysis was conducted after model training to extract feature-level insights.

### 3️⃣ Price Modeling
#### 1. Cluster performances based on characteristics
> ![image](https://github.com/user-attachments/assets/e04fc794-f107-4a55-8872-655047529679)
> K-Means clustering on performance features resulted in 6 clusters, validated through silhouette score analysis.
#### 2. Set base price using the average price within each cluster
> ![image](https://github.com/user-attachments/assets/a3adc242-3bba-4580-9ba7-92be3b1c1ce7)
> The base prices for the highest and lowest seat grades were set using the average of the highest and lowest prices within each assigned cluster.
#### 3. Adjust base price using predicted reservation rate and membership conversion rate
> ![4ac25935457368bf](https://github.com/jwshin0908/BigContest_2023/assets/66217855/4918bf14-c6be-451c-814a-df43c1976d6e)
> The base prices were adjusted using a weighted function.
#### 4. Distribute final prices across seat grades within the [min–max] range

## 🏁 Conclusion
### ✅ Practical Applications
- Automated seat grouping and price estimation for new performances based on input characteristics
- Enhanced seat selection interface that displays additional insights, such as how many customers with certain profiles previously reserved a given seat grade
  
- Transparent pricing rationale, helping to build audience trust
- Data-driven guidance to support more informed purchase decisions
    
### ✅ Expected Benefits by Stakeholder
#### 🎭 Seoul Arts Center (Venue Operator)
- Enables optimal pricing by adjusting prices based on predicted demand, maximizing both attendance and revenue
- Improves customer satisfaction through reasonable pricing and clearer seat categorization, encouraging repeat visits and revitalizing interest in classical concerts

#### 👥 Audience
- Provides a clear guideline for selecting appropriate seats based on individual interest in classical performances
- Helps maximize consumer utility within each individual's willingness to pay

## 🔧 Tools & Techniques
- Python (pandas, sklearn, matplotlib)
- Linear Regression, KMeans Clustering
## 📁 Included
- `/bigcontest_2023_pitch.pdf` – Full presentation slides


---

Copyright 2023. `Miraclassic de BOAZ` All rights reserved.
