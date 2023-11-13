# <div align=center>🍀네이버 쇼핑몰 리뷰 감성 분석🍀</div>

![naver_shop_logo](https://github.com/Kimseongchan1224/KOELECTRA_PJ/assets/79899868/92899dc1-9bcd-458c-be78-2cd2a964e02e)

<div align=center>네이버 쇼핑은 네이버 이용자와 네이버 쇼핑에 입점한 쇼핑몰 및 스마트스토어 간의 편리한 연결을 위해 상품 검색, 카테고리 분류, 가격비교, 쇼핑 컨텐츠 등을 제공하는 쇼핑포털 서비스이다.</div>

>[출처:로고](https://www.interad.com/insights/naver-shopping-search-update)&nbsp;/&nbsp;[출처:설명](https://m.searchad.naver.com/faq/view/374?from) 

<hr>

## 1.개요
이번 프로젝트에서는 한국어 자연어 처리 모델인 KOELECTRA를 활용하여 네이버 쇼핑몰 리뷰의 긍부정 예측을 하고자 한다.

### 1-1. 문제정의
온라인 상권의 활성화로 온라인 쇼핑몰의 거래가 활발해지고 있는 가운데 소비자의 선택의 있어 이용후기가 크게 영향을 미치고 있는 것으로 나타났다. 다른 이용자들의 반응과 경험이 소비자 선택에 중요한 역할을 함에 따라 이용후기의 영향력이 증가하면서 인한 문제점도 늘어나고 있는데 이용후기를 조작 및 소비자가 올린 이용후기를 삭제하는 등 소비자피해도 발생하고 있다. 여기서 발생하는 문제를 해결하고자 KOELECTRA를 활용하여 리뷰를 분류하는 시스템을 만들고자한다. <br>
또한 2019년 온라인 리뷰 주요 통계를 보면 "10명 중 6명은 Google My Business에서 로컬 비즈니스의 리뷰를 찾아본다.", "거의 10명 중 9명은 구매 이전에 로컬 비즈니스에 대한 리뷰를 읽어 본다.", "잠재 고객들은 평균적으로 10갱의 온라인 리뷰를 읽어본후에 로컬비즈니스에 대해 신뢰를 하게된다.", "잠재 고객 중 절반은 리뷰를 읽어본 후에 웹사이트를 방문하다." 라고 통계가 보여주듯이 리뷰의 중요성이 점차 강요되고 있다.

>[출처:소비자경제](https://www.dailycnc.com/news/articleView.html?idxno=209683)&nbsp;/&nbsp;[출처:인텔리시스템](https://blog.kr.intelisystems.com/2019%EB%85%84%EB%8F%84-%EC%98%A8%EB%9D%BC%EC%9D%B8-%EB%A6%AC%EB%B7%B0-%EC%A3%BC%EC%9A%94-%ED%86%B5%EA%B3%84-top-25/)

### 1.2 데이터 및 모델 개요
| 데이터셋 | 개수 | 특징 |
|----------|---|---|
| 네이버 쇼핑몰 후기 | 200,000 | 의류, 잡화, 미용, 가전, 식품 등 다양한 분야 물건 포함.<br>물건 품질, 배송 속도, 실물과 온라인 간의 괴리 등 |

- 언어 : 한국어
- 출처 : 네이버 쇼핑
- 수집기간 : 2020-06 ~ 2020-07
- 점수 : 5점만점

#### 데이터 미리보기
```
5	배공빠르고 굿
2	택배가 엉망이네용 저희집 밑에층에 말도없이 놔두고가고
5	아주좋아요 바지 정말 좋아서2개 더 구매했어요 이가격에 대박입니다. 바느질이 조금 엉성하긴 하지만 편하고 가성비 최고예요.
2	선물용으로 빨리 받아서 전달했어야 하는 상품이었는데 머그컵만 와서 당황했습니다. 전화했더니 바로주신다했지만 배송도 누락되어있었네요.. 확인안하고 바로 선물했으면 큰일날뻔했네요..이렇게 배송이 오래걸렸으면 사는거 다시 생각했을거같아요 아쉽네요..
5	민트색상 예뻐요. 옆 손잡이는 거는 용도로도 사용되네요 ㅎㅎ
2	비추합니다 계란 뒤집을 때 완전 불편해요 ㅠㅠ 코팅도 묻어나고 보기엔 예쁘고 실용적으로 보였는데 생각보다 진짜 별로입니다.
```

>[출처:git/KiimKii](https://github.com/KiimKii/nsrd)

### 1.3 감성분석 순서

![count](https://github.com/Kimseongchan1224/KOELECTRA_PJ/assets/79899868/904b9fad-aa94-47a7-8156-0912e1efe9a2)

1. 분석할 네이버 쇼핑몰 리뷰데이터를 깃허브에서 확보한다.
2. 파이참에서 인식할수 있게 텍스트화 작업을 한다.
3. python을 활용하여 텍스트 데이터를 학습시키는 작업한다.
4. 학습이 된 프로그램을 작동시켜 긍정과 부정으로 분류하는지 확인을 한다.

>[출처:로고](https://blog.naver.com/hn03055/222730453539)&nbsp;/&nbsp;[출처:로고](http://wiki.hash.kr/index.php/%ED%8C%8C%EC%9D%B4%EC%B0%B8)

## 2. 데이터

### 2.1 데이터 소스

#### 원시데이터
| num | ratings | reviews | label |
|---|----------|---|---|
| 1 | 5 | 배공빠르고 굿 | 1 |   
| 2 | 2 | 택배가 엉망이네용 저희집 밑에층에 말도없이 놔두고가고 | 0 |   
| 3 | 5 | 아주좋아요 바지 정말 좋아서2개 더 구매했어요 이....  | 1 |  
| 4 | 2 | 선물용으로 빨리 받아서 전달했어야 하는 상품이 였.... | 0 |
|...|...|...|...|
| 199997 | 5 | 다이슨 케이스 구매했어요 다이슨 슈퍼소닉 드라이...| 1 |    
| 199998 | 5 | 로드샾에서 사는것보다 세배 저렴하네요 ㅜㅜ 자주...| 1 |   
| 199999 | 5 | 넘이쁘고 쎄련되보이네요~| 1 |  
| 200000 | 5 | 아직 사용해보지도않았고 다른 제품을 써본적이없.... | 1 |  
| 번호 | 별점 | 고객이 남긴 텍스트 리뷰 | 부정(0), 긍정(1) | 

#### 데이터 분포
<table>
  <tr><th></th><th>별점</th><th>건수</th></tr>
  <tr><th rowspan='2'>긍정 (99,963)</th><th>5</th><td>81,177</td></tr>
  <tr><th>4</th><td>18,786</td></tr>
  <tr><th rowspan='2'>부정 (100,037)</th><th>2</th><td>63,989</td></tr>
  <tr><th>1</th><td>36,048</td></tr>
  <tr><th colspan='2'>계</th><td>200,000</td></tr>
</table>

네이버 쇼핑에서 제품별 후기를 별점과 함께 수집한 것이다. 데이터는 탭으로 분리되어 있으며, 첫번째 필드에는 별점(1 ~ 5), 두번째 필드에는 텍스트가 위치한다. 긍/부정으로 분류하기 애매한 3점에 해당하는 텍스트들은 제외하였고, 긍정(4 ~ 5점)과 부정(1 ~ 2점)의 비율이 1:1에 가깝도록 샘플링을 했다.

### 2.2 탐색적 데이터 분석
#### 분포확인
```
total_data = pd.read_table('ratings_total.txt', names=['ratings', 'reviews'])
print('전체 리뷰 개수 :',len(total_data)) # 전체 리뷰 개수 출력
```
```
전체 리뷰 개수 : 200000
```
총 20만개의 데이터 샘플이 존재한다.
```
total_data['label'].value_counts().plot(kind = 'bar')
```
![cap1](https://github.com/Kimseongchan1224/KOELECTRA_PJ/assets/79899868/f3176b37-a696-4328-a023-edfcf15f1ebd)
```
print(total_data.groupby('label').size().reset_index(name = 'count'))
```
```
   label   count
0      0  100037
1      1   99963
```
0과 1 모두 약 1만개의 데이터로 50:50 비율을 가지고 있다.
```
total_data['ratings'].value_counts().plot(kind = 'bar')
```
![cap2](https://github.com/Kimseongchan1224/KOELECTRA_PJ/assets/79899868/235e7f15-1367-457e-9800-8e512ef7c2d8)
```
print(total_data.groupby('ratings').size().reset_index(name = 'count'))
```

```
ratings  count
0        1  36048
1        2  63989
2        4  18786
3        5  81177
```
고객이 남긴 별점 데이터의 수는 <u>5</u>점이 81177개, <u>2</u>점이 63989개, <u>1</u>점이 36048개, <u>4</u>점이 18786개의 데이터를 보유하고 있다.
#### 
### 2.3 데이터 전처리
#### 중복 리뷰데이터 
```
print("서로 다른 데이터의 수 :" , data['reviews'].nunique())
data.drop_duplicates(subset=['reviews'], inplace=True)
print("데이터 개수 (중복제거) : ", len(data))
```
```
서로 다른 데이터의 수 : 199904
데이터 개수 (중복제거) :  199904
1    99952
0    99952
```
텍스트 리뷰가 중복인 데이터를 96개를 제거하였다.
#### 결측치 제거
```
print(data.isnull().values.any()) #결측치(Null, NaN)가 있다면 True
data = data.dropna(how='any')
data['reviews'] = data['reviews'].str.replace("[^ㄱ-ㅎㅏ-ㅣ가-힣]","")
print(data[:5])
```
```
   ratings                                            reviews                                                 label
0        5                                             배공빠르고굿                                             1
1        2                           택배가엉망이네용저희집밑에층에말도없이놔두고가고                              0
2        5  아주좋아요바지정말좋아서개더구매했어요이가격에대박입니다바느질이조금엉성하긴하지만편하고가성...            1
3        2  선물용으로빨리받아서전달했어야하는상품이었는데머그컵만와서당황했습니다전화했더니바로주신다했...            0
4        5                          민트색상예뻐요옆손잡이는거는용도로도사용되네요ㅎㅎ                             1
```
결측치인 Null, NaN의 값과 띄어쓰기가 제거 되었다.
## 3. 재학습 결과

### 3.1 계발환경
<img src="https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=Python&logoColor=white"/></a>
<img src="https://img.shields.io/badge/PyTorch-E34F26?style=flatsquare&logo=PyTorch&logoColor=white"/></a>
<img src="https://img.shields.io/badge/PyCharm-000000?style=flat-square&logo=PyCharm&logoColor=white"/></a>
<img src="https://img.shields.io/badge/Jupyter-F37626?style=flat-square&logo=Jupyter&logoColor=white"/></a>

### 3.2  KOELECTRA fine-tuning
```
import pandas as pd
import numpy as np
from transformers import ElectraTokenizer, ElectraForSequenceClassification
from transformers import get_linear_schedule_with_warmup, logging
from sklearn.model_selection import train_test_split
import torch
from torch.utils.data import TensorDataset, DataLoader, RandomSampler, SequentialSampler
import time
import datetime

train_data_path = "review30000.txt"

dataset = pd.read_csv(train_data_path, sep="\t").dropna(axis=0)
text = list(dataset['reviews'].values)
label = dataset['label'].values

# 데이터 확인
num_to_print = 3
print("\n\n*** 데이터 ***")
for j in range(num_to_print):
    print(f'reviews: {text[j][:20]}, label : {label[j]}')
print(f'\t * 학습 데이터의 수 : {len(text)}')
print(f'\t * 부정 리뷰 수 : {list(label).count(0)}')
print(f'\t * 긍정 리뷰 수 : {list(label).count(1)}')

# 토큰화
tokenizer = ElectraTokenizer.from_pretrained("koelectra-small-v3-discriminator")
inputs = tokenizer(text, truncation=True, max_length=256, add_special_tokens=True, padding="max_length")
input_ids = inputs['input_ids']
attention_mask = inputs['attention_mask']
print("\n\n*** 토큰화 ***")
for j in range(num_to_print):
    print(f'\n{j+1}번째 데이터')
    print("** 토큰 **")
    print(input_ids[j])
    print("** 어텐션 마스크 **")
    print(attention_mask[j])

train, validation, train_y, validation_y = train_test_split(input_ids, label, test_size=0.2, random_state=2023)
train_masks, validation_masks, _, _ = train_test_split(attention_mask, label, test_size=0.2, random_state=2023)

print("\n\n*** 데이터 분리 ***")
print(f"학습 데이터 수 : {len(train)}")
print(f"검증 데이터 수 : {len(validation)}")

batch_size = 32
train_inputs = torch.tensor(train)
train_labels = torch.tensor(train_y)
train_masks  = torch.tensor(train_masks)
train_data   = TensorDataset(train_inputs, train_masks, train_labels)
train_sampler = RandomSampler(train_data)
train_dataloader = DataLoader(train_data, sampler=train_sampler, batch_size=batch_size)

validation_inputs = torch.tensor(validation)
validation_labels = torch.tensor(validation_y)
validation_masks  = torch.tensor(validation_masks)
validation_data   = TensorDataset(validation_inputs, validation_masks, validation_labels)
validation_sampler = RandomSampler(validation_data)
validation_dataloader = DataLoader(validation_data, sampler=validation_sampler, batch_size=batch_size)

model = ElectraForSequenceClassification.from_pretrained('koelectra-small-v3-discriminator', num_labels=2)

#optimizer = torch.optim.AdamW(model.parameters(), lr=5e-06)
optimizer = torch.optim.Adam(model.parameters(),lr=3e-04, eps=1e-06, betas=(0.9, 0.999))

epoch = 4
scheduler = get_linear_schedule_with_warmup(optimizer,
                                            num_warmup_steps=0,
                                            num_training_steps=len(train_dataloader)*epoch)

for e in range(0, epoch):
    print(f'\n\nEpoch {e+1} of {epoch}')
    print(f'** 학습 **')
    t0 = time.time()
    total_loss = 0
    model.train()
    for step, batch in enumerate(train_dataloader):
        if step % 50 == 0 and not step == 0:
            elapsed_rounded = int(round(time.time() - t0))
            elapsed = str(datetime.timedelta(seconds=elapsed_rounded))
            print(f'Batch {step} of {len(train_dataloader)}, 걸린 시간 : {elapsed}')

        batch_ids, batch_mask, batch_labels = tuple(t for t in batch)

        model.zero_grad()

        outputs = model(batch_ids, token_type_ids=None, attention_mask=batch_mask, labels=batch_labels)
        loss = outputs.loss
        total_loss += loss.item()

        if step % 10 == 0 and not step == 0:
            print(f'step : {step}, loss : {loss.item()}')

        loss.backward()
        torch.nn.utils.clip_grad_norm(model.parameters(), 1.0)
        optimizer.step()
        scheduler.step()

    avg_train_loss = total_loss / len(train_dataloader)
    print(f"평균 학습 오차(loss) : {avg_train_loss}")
    epoch_elapsed_time = int(round(time.time() - t0))
    print(f"학습에 걸린 시간 : {str(datetime.timedelta(seconds=epoch_elapsed_time))}")

    print('\n\n** 검증 **')
    t0 = time.time()
    model.eval()
    eval_loss, eval_accuracy, eval_steps, eval_example = 0, 0, 0, 0
    for batch in validation_dataloader:
        batch_ids, batch_mask, batch_labels = tuple(t for t in batch)

        with torch.no_grad():
            outputs = model(batch_ids, token_type_ids=None, attention_mask=batch_mask)

        logits = outputs[0]
        logits = logits.numpy()
        label_ids = batch_labels.numpy()

        pred_flat = np.argmax(logits, axis=1).flatten()
        labels_flat = label_ids.flatten()
        eval_accuracy_temp = np.sum(pred_flat == labels_flat) / len(labels_flat)
        eval_accuracy += eval_accuracy_temp
        eval_steps += 1
    print(f"검증 정확도 : {eval_accuracy / eval_steps}")
    val_elapsed_time = int(round(time.time() - t0))
    print(f"검증에 걸린 시간 : {str(datetime.timedelta(seconds=val_elapsed_time))}")

print("\n\n** 모델 저장 **")
save_path = 'koelectra_small'
model.save_pretrained(save_path + ".pt")
print("\n** 끝 **")
```


