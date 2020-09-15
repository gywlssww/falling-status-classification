# falling-status-classification
### Data Preprocessing Results
  - 5 classes : 걷기 보통, 무게중심 우/전/좌/후
  - 5 data sets per 1 person (Each set consists of 233 timestamps) 
  
  
## 01. Normal/Abnormal status classification 
  1. Training + Test Data split 
    
    - Training(80%) : Test(20%)
    - classify data into 2 classes 
      - normal : 걷기 보통
      - abnormal : others
      
  2. Experiment Settings
    
    - 10명의 data 통합
    - Evaluation metric: recall, precision, F1 measure
    
  3. Modelling
    
    - Classifier : RNN-based
    
  4. Results
  
    - Accuracy : 79.01%

## 02. 5 classes Classification
  1. Training + Test Data split 
    
    - Training(80%) : Test(20%)
    - classify data into 5 classes (label : 0-4)
      - normal : 걷기 보통 (0)
      - abnormal_l,abnormal_r,abnormal_f,abnormal_b, : 무게 중심 좌측/우측/전방/후방 (1,2,3,4)
      
  2. Experiment Settings
    
    - 10명의 data 통합
    - Evaluation metric: recall, precision, F1 measure
    
  3. Modelling
    
    - Classifier : RNN-based
    
  4. Results
  
    - Accuracy : TBD
   
  5. 5 classes clssification f1_score
  
| Dimension | Logist Regression | Linear SVM  | RBF SVM  | Poly SVM | XGBoost  |
|:---:|:---:|:---:|:---:|:---:|:---:|
| 20  | TBD  | TBD  |TBD  |TBD  |-  |
| 50  | TBD  | TBD  |TBD  |TBD  |-  |
| 100  | TBD  | TBD  |TBD  |TBD  |-  |
| 200  | TBD  | TBD  |TBD  |TBD  |-  |
| 300  | TBD  | TBD  |TBD  |TBD  |-  |


 
## 03. Rule-based Classification

  1. Baseline rule
  
    - features
    - thresholds
    
    
    
  
