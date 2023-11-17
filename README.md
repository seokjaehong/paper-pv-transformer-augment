# paper-pv-transformer-augment

- Transformer 기반 모델과 데이터 증강을 활용한 태양광 발전량 예측 최적화 연구

## 실행방법
1. python 3.8 에서 실행합니다. 아래 명령어로 포함된 라이브러리를 설치합니다.
    ```pip install -r requirements.txt```
2. 데이터 세팅
   데이터에 대한 전처리는 jupyter notebook으로 수행합니다.
   [0] clean data.ipynb
   - 데이터 중 시계열정보에 해당하는 정보를 datetime 형태로 바꾸고, 데이터에 대한 속성을 파악
   [1] Data PreProcess with Augment.ipynb
   - 트레이닝/테스트 세트를 실험별로 분할
   - Data Augment 에 대한 코드 및 데이터 분포 확인
   [2] Final clean dataset.ipynb
   - 각 시나리오에 해당하는 데이터세트를 csv파일로 export
   - 추가실험 : Time Dual Embedding / PCA 

3. 모델 실행 방법
scripts/long_term_forcast 경로에 위치한 Autoformer.sh , Informer.sh, Transformer.sh 파일 내에 
각각 위치한 python 명령어를 실행합니다.
명령어에 포함되는 parameter를 변경해 나가면서 모델을 실행합니다.

<주요 parameter> 
root_path : data folder path 
data_path : file name  
model : model_name( Transformer , Informer, Autoformer) 
seq_len : input sequence length (default : 24)
label_len : start token length (default : 12 )
pred_len : prediction sequence length (default : 24)
data : dataset type (custom)
feature : forecasting type ( M: Multivariate predict multivariate) 
e_layer : number of encoder layers
d_layer : number of decoder layers 
factor : attention factor 
enc_in : encoder input size ( data column count)
decc_in : decoder input size ( data column count)
c_out : output size ( data column count)
dex :  description 
train_epochs : train epochs


 
