# body-fat-percentage-predictor
Body FAt percentage predictor using linear regression gradient descent with feature engineering.
This is a revision of my last academic project I did in university. The previous project (not uploaded to github, will do soon) used a lasso regression gradient descent to train the models and reduce the number of features. This revision uses a linear regression gradient descent instead and I reduced the features via feature engineering. Both projects did not utilize libraries for machine learning. I built them from scratch.

## Data cleaning and preprocessing
- visualized each features
- removed outliers with winsorization in varying percentiles. as much as possible, i did not want to drop data since there are only ~250 data

### Age has no outliers
![image](https://github.com/arceldizon28/body-fat-percentage-predictor/assets/148745972/374dda18-361e-4d7a-8c8b-721be186e2cf)
### Weight has outliers
![image](https://github.com/arceldizon28/body-fat-percentage-predictor/assets/148745972/7e144507-232a-4d67-84e9-594c36e8f3e5)
![image](https://github.com/arceldizon28/body-fat-percentage-predictor/assets/148745972/9ad21a46-74e1-40c5-b2dd-78323aa7b253)
### Height has no outliers
![image](https://github.com/arceldizon28/body-fat-percentage-predictor/assets/148745972/d2eea896-7585-4cd0-8aad-05142f93d5d4)
### Neck has outliers
![image](https://github.com/arceldizon28/body-fat-percentage-predictor/assets/148745972/dcd01ec4-97e3-4a95-b0da-2112f7c2402b)
![image](https://github.com/arceldizon28/body-fat-percentage-predictor/assets/148745972/1573a8f3-22e3-4c94-bf41-773e0b7484b9)
### Chest has outliers
![image](https://github.com/arceldizon28/body-fat-percentage-predictor/assets/148745972/8d0d7cb0-0363-43ef-be24-8e9038cab651)
![image](https://github.com/arceldizon28/body-fat-percentage-predictor/assets/148745972/bd732536-3e22-4358-b1df-74e9bc678d06)
### Abdomen has outliers
![image](https://github.com/arceldizon28/body-fat-percentage-predictor/assets/148745972/adfe1921-048d-4367-a08e-a97372707cd2)
![image](https://github.com/arceldizon28/body-fat-percentage-predictor/assets/148745972/fdf4b7ec-aefc-4c66-b58e-6f6bb59ddf25)
### Hip has outliers
![image](https://github.com/arceldizon28/body-fat-percentage-predictor/assets/148745972/63b75f6e-74a2-4a6d-8afc-2eedc0c4c421)
![image](https://github.com/arceldizon28/body-fat-percentage-predictor/assets/148745972/9168e0fe-2b3e-4764-9b05-16f4f9a334d5)
### Thigh has outliers
![image](https://github.com/arceldizon28/body-fat-percentage-predictor/assets/148745972/02e9d17d-4464-45b5-9256-e4c3a1b611bb)
![image](https://github.com/arceldizon28/body-fat-percentage-predictor/assets/148745972/a708ff64-7ab5-48ed-b86b-5b8daee82c1f)
### Knee has outliers
![image](https://github.com/arceldizon28/body-fat-percentage-predictor/assets/148745972/2d3d3a55-51c6-40a8-b4c3-834dd955948c)
![image](https://github.com/arceldizon28/body-fat-percentage-predictor/assets/148745972/7dd992cb-d3ef-49ee-aa67-63c2ba1104e7)
### Ankle has outliers
![image](https://github.com/arceldizon28/body-fat-percentage-predictor/assets/148745972/4e44aa22-fcdb-45f7-a687-184d9d8fe3a9)
![image](https://github.com/arceldizon28/body-fat-percentage-predictor/assets/148745972/ffd4661a-8e9d-4b1f-a4c1-84f63a888503)
### Biceps has outliers
![image](https://github.com/arceldizon28/body-fat-percentage-predictor/assets/148745972/ad36f92e-255f-436b-8499-cf3fbc8c9110)
![image](https://github.com/arceldizon28/body-fat-percentage-predictor/assets/148745972/bf3b4b90-ad6f-42ea-a99f-73d00022951e)
### Forearm has outliers
![image](https://github.com/arceldizon28/body-fat-percentage-predictor/assets/148745972/284bbefe-739c-4986-9956-42aa87b28fe1)
![image](https://github.com/arceldizon28/body-fat-percentage-predictor/assets/148745972/30b2cc70-de5f-4bbd-83e8-c7a9439fed3a)
### Wrist has outliers
![image](https://github.com/arceldizon28/body-fat-percentage-predictor/assets/148745972/ed4d7a45-fa2b-4ff4-b2c9-62a8012e4c3d)
![image](https://github.com/arceldizon28/body-fat-percentage-predictor/assets/148745972/4305733f-4443-4cc7-8d29-5bed7e70c67f)


  
- checked for multicollinearity using correlation analysis
- feature engineering:
  - feature engineered features that have 0.7 or higher correlations to each other
  - created BMI using the height and weight features
  - combined features: Chest-Abdomen, Hip-Thigh, Neck-Wrist, Knee-Ankle, Biceps-Forearm (ratio)
  - Age is left unengineered
 
## Model training
- used linear regression gradient descent to train the model.
- did hyperparameter value experimentations with varying learning rates and epochs
- added an early-stop function to prevent overshooting and avoid wasting training time
- best model: m(8.56120965, 9.40495377, 7.21295553, 11.16557975, 13.408664, 10.32275786, 9.17106151), b = -18.468214630944036.

## Model testing
- best model has an MSE of 80.99 and RMSE of 8.99
- This is a massive difference since ~10 units of body fat percentage can already be the difference between a shredded athlete and an average person.
