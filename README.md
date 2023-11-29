![image](https://github.com/seokjaehong/paper-pv-transformer-augment/assets/34717277/b0f44e00-0f74-460a-a664-c23840782281)# paper-pv-transformer-augment

- Transformer 기반 모델과 데이터 증강을 활용한 태양광 발전량 예측 최적화 연구



## 실행방법
1. python 3.8 에서 실행합니다. 아래 명령어로 포함된 라이브러리를 설치합니다.
    ```pip install -r requirements.txt```
2. 데이터 세팅
- 데이터에 대한 전처리 및 추출은 jupyter notebook으로 수행합니다.
- [0] Preprocess Dataset 추출.ipynb
    - 데이터 중 시계열정보에 해당하는 정보를 datetime 형태로 바꾸고, 데이터에 대한 속성을 파악
    - 실험1     
        - 일부 상수값, Null, 컬럼을 제외한 속성을 기준으로 CNN,LSTM,XGBOOST, TRANSFORMER, INFORMER, AUTOFORMER에 대한 실험을 진행 
    - 실험2
        - 학습/테스트 데이터를 각 기간대로 분할
        - MEAN, MEDIAN에 대한 집계 코드 하여 - 각 시나리오에 해당하는 데이터세트를 csv파일로 export
    - 실험3
        - Data Augment 에 대한 코드 작성 하여 csv 파일로 export 
    - 기타 예정중인 추가실험 : Time Dual Embedding / PCA 
3. CNN,LSTM,XGBOOST에 대한 실험 코드
    - CNN : learning_cnn.ipynb
    - lstm  : learning_lstm.ipynb
    - xgb : learning_xgb.ipynb

4. Tranformer 기반 모델 실행 방법
scripts/long_term_forcast 경로에 위치한 Autoformer.sh , Informer.sh, Transformer.sh 파일 내에 각각 위치한 python 명령어를 실행합니다.명령어에 포함되는 parameter를 변경해 나가면서 모델을 실행합니다.

- <주요 parameter> 
- root_path : data folder path 
- data_path : file name
- model : model_name( Transformer , Informer, Autoformer) 
- seq_len : input sequence length (default : 24)
- label_len : start token length (default : 12 )
- pred_len : prediction sequence length (default : 24)
- data : dataset type (custom)
- feature : forecasting type ( M: Multivariate predict multivariate) 
- e_layer : number of encoder layers
- d_layer : number of decoder layers 
- factor : attention factor 
- enc_in : encoder input size ( data column count)
- decc_in : decoder input size ( data column count)
- c_out : output size ( data column count)
- des :  description 
- train_epochs : train epochs

- 


 
# 데이터는 용량이 큰 관계로 구글드라이브에 등록되어있습니다.
https://drive.google.com/drive/folders/1l89uy8DHKoaN10Ih8nbMyg1fe4RVnSuD

[s2설명]
case1은 mean
case2는 max
case3은 median

[s3 설명]
시나리오번호 4 는 실험2의 시나리오 번호1에서 시작 
시나리오번호 5 는 실험2의 시나리오 번호2에서 시작 
시나리오번호 6 는 실험2의 시나리오 번호3에서 시작 

1 aug :2 sigma : 0.01
2 aug :2 sigma : 0.05
3 aug :2 sigma : 0.1
4 aug :4 sigma : 0.01
5 aug :4 sigma : 0.05
6 aug :4 sigma : 0.1
7 aug :8 sigma : 0.01
8 aug :8 sigma : 0.05
9 aug :8 sigma : 0.1
