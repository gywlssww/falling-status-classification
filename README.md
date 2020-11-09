# falling-status-classification
### Data Preprocessing Results
  - 5 classes : 걷기 보통, 무게중심 우/전/좌/후
  - 5 data set files per 1 person (Each file consists of 234 timestamps) 
  
  
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
    
    - Training(4 files for each subject, 46805) : Test(1 file for each subject, 11700)
    - classify data into 5 classes (label : 0-4)
      - normal : 걷기 보통 (0)
      - abnormal_l,abnormal_r,abnormal_f,abnormal_b, : 무게 중심 좌측/우측/전방/후방 (1,2,3,4)
      
  2. Experiment Settings
    
    - 10명의 data 통합
    - Evaluation metric: recall, precision, F1 measure
    
  3. Modelling
    
    - Classifier : RNN-based
    
  4. Results (Baseline Model)
  
    - Accuracy : 40.5% ( epochs=20, batch_size=64,)
   
  5. Hyperparameters Optimization Results
  - timestamp-step = 234 - 234
  

|               |LSTM     | | Bi-LSTM |      |GRU |      |      
|:-------------:|:------:|:------:|:------:|:------:|:------:|:------:|
| # of Epoches  |train   | test   |train   | test   |train   | test   |
| 500           | 44.50  | 40.00  |TBD     |TBD     |TBD     |TBD     |
| 1000           | 92.00  | 51.00  |98.77   |51.78   |TBD     |TBD     |
| 1500          | 92.50  | 34.60  |99.87  |54.70 |TBD     |TBD     |
|# of batches   |        |        |        |        |        |        |
| 117            | TBD   | TBD   |100.00    |62.63   |TBD     |TBD     |
| 234            | 91.80  | 40.70  |100.00   |63.64  |TBD     |TBD     |
| 468          | 91.80  | 44.00  |98.00   |61.62   |TBD     |TBD     |
| 729          | TBD   | TBD   |94.75     |58.59    |TBD     |TBD     |
 
 - timestamp - step = 234 -117
 
|               |Bi-LSTM     | |GRU |      |Bi-GRU |      |    
|:-------------:|:------:|:------:|:------:|:------:|:------:|:------:|
|# of batches    |train   | test   |train   | test   |train   | test   |
| 117           |TBD     |TBD    |98.49   |74.49  |TBD     |TBD    |
| 234           |97.20   |52.80  |74.43   |54.08    |TBD     |TBD    |
| 468         |92.50   |49.00   |90.97    |60.20   |TBD     |TBD    |
| 972           |TBD     |TBD    |90.23     |61.22    |TBD     |TBD    |

 - timestamp - step = 117 -117
 
|               |Bi-LSTM     | |GRU |      |  Bi-GRU |      |      
|:-------------:|:------:|:------:|:------:|:------:|:------:|:------:|
|# of batches    |train   | test   |train   | test   |train   | test   |
| 117           |TBD     |TBD    |99.75    |72.727   |TBD     |TBD    |
| 234           |97.20   |52.80  |97.00    |71.43    |TBD     |TBD    |
| 468         |92.50   |49.00   |95.75    |64.64    |TBD     |TBD    |
| 972           |TBD     |TBD    |90.23     |61.22    |TBD     |TBD    |

## 03. Rule-based Classification

  1. Baseline rule
  
    - features
    - thresholds
    
    
    
  
