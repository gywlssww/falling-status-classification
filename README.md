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
    - Evaluation metric: accuracy
    
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
| 1500          | 92.50  | 34.60  |99.87  |66.32 |TBD     |TBD     |
|# of batches   |        |        |        |        |        |        |
| 117            | TBD   | TBD   |100.00    |62.63   |TBD     |TBD     |
| 234            | 91.80  | 40.70  |100.00   |63.64  |TBD     |TBD     |
| 468          | 91.80  | 44.00  |98.00   |61.62   |TBD     |TBD     |
| 729          | TBD   | TBD   |94.75     |58.59    |TBD     |TBD     |
 
 - timestamp - step = 234 -117
 
|               |Bi-LSTM     | |GRU |      |Bi-GRU |      |    
|:-------------:|:------:|:------:|:------:|:------:|:------:|:------:|
|# of batches    |train   | test   |train   | test   |train   | test   |
| 39           |100.00    |68.37    |100.00   |76.53 |100.00     |71. 43  |
| 117           |100.00     |73.47    |99.49   |77.49  |99.25     |56.12  |
| 234           |100.00   |71.43  |86.46   |59.18    |100.00     |56.12    |
| 468         |98.24   |59.18 |99.24   |75.51  |100.00    |63.27   |
| 972           |100.00   |69.39   |94.73     |65.30    |100.00    |54.08    |

 - timestamp - step = 117 -117
 
|               |Bi-LSTM     | |GRU |      |  Bi-GRU |      |      
|:-------------:|:------:|:------:|:------:|:------:|:------:|:------:|
|# of batches    |train   | test   |train   | test   |train   | test   |
| 117           |TBD     |TBD    |99.75    |72.727   |TBD     |TBD    |
| 234           |97.20   |52.80  |97.00    |71.43    |TBD     |TBD    |
| 468         |92.50   |49.00   |95.75    |64.64    |TBD     |TBD    |
| 972           |TBD     |TBD    |90.23     |61.22    |TBD     |TBD    |


### Discussion

1. Bi-LSTM > LSTM
```
- 양방향 : 주기 데이터에 적합
- some additional features associated with data that might be
captured by BiLSTM but unidirectional LSTM models are not
capable of exposing them, since the training is only one way
```
(S. Siami-Namini, N. Tavakoli and A. S. Namin, "The Performance of LSTM and BiLSTM in Forecasting Time Series," 2019 IEEE International Conference on Big Data (Big Data), Los Angeles, CA, USA, 2019, pp. 3285-3292.
doi: 10.1109/BigData47090.2019.9005997)



2. GRU > LSTM
```
- GRU는 3개 gate (forget, input, output)로 이뤄진 LSTM의 simplified 버전으로 2개 gate로 구성. (update, reset)
- For tasks with a few data
- 적은 파라미터를 가진 경우 LSTM 보다 좋은 결과를 얻는 것으로 알려짐.
```
(Jiang, Zheng & Hu, Meng-Han & Fan, Lei & Pan, Yaling & Tang, Wei & Zhai, Guangtao & Lu, Yong-Zai. (2020). Combining Visible Light and Infrared Imaging for Efficient Detection of Respiratory Infections such as COVID-19 on Portable Device. )

> baseline model은 9개 features 가진 HAR data
> 실험 데이터는 x,y,z 축 가속도 3개 features의 상대적으로 단순한 data로 보다 간소한 network에서 성능이 우수함을 확인


## 03. Rule-based Classification

  1. Baseline rule
  
    - features
    - thresholds
    
    
    
  
