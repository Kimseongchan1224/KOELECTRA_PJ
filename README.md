# <div align=center>🍀네이버 쇼핑몰 리뷰 감성 분석🍀</div>

![naver_shop_logo](https://github.com/Kimseongchan1224/KOELECTRA_PJ/assets/79899868/92899dc1-9bcd-458c-be78-2cd2a964e02e)

<div align=center>네이버 쇼핑은 네이버 이용자와 네이버 쇼핑에 입점한 쇼핑몰 및 스마트스토어 간의 편리한 연결을 위해 상품 검색, 카테고리 분류, 가격비교, 쇼핑 컨텐츠 등을 제공하는 쇼핑포털 서비스이다.</div>

>[출처:로고](https://www.interad.com/insights/naver-shopping-search-update)&nbsp;/&nbsp;[출처:설명](https://m.searchad.naver.com/faq/view/374?from) 

<hr>

## 1.개요
이번 프로젝트에서는 한국어 자연어 처리 모델인 KOELECTRA를 활용하여 네이버 쇼핑몰 리뷰의 긍부정 예측을 하고자 한다.

### 1-1. 문제정의
온라인 상권의 활성화로 온라인 쇼핑몰의 거래가 활발해지고 있는 가운데 소비자의 선택의 있어 이용후기가 크게 영향을 미치고 있는 것으로 나타났다. 다른 이용자들의 반응과 경험이 소비자 선택에 중요한 역할을 함에 따라 이용후기의 영향력이 증가하면서 인한 문제점도 늘어나고 있는데 이용후기를 조작 및 소비자가 올린 이용후기를 삭제하는 등 소비자피해도 발생하고 있다. 여기서 발생하는 문제를 해결하고자 KOELECTRA를 활용하여 리뷰를 분류하는 시스템을 만들고자한다.

>[출처:소비자경제](https://www.dailycnc.com/news/articleView.html?idxno=209683)

## 1.2 데이터 및 모델 개요

>[출처:git/KiimKii](https://github.com/KiimKii/nsrd)

## 1.3 감성분석 순서

![count](https://github.com/Kimseongchan1224/KOELECTRA_PJ/assets/79899868/904b9fad-aa94-47a7-8156-0912e1efe9a2)

1. 분석할 네이버 쇼핑몰 리뷰데이터를 깃허브에서 확보한다.
2. 파이참에서 인식할수 있게 텍스트화 작업을 한다.
3. python을 활용하여 텍스트 데이터를 학습시키는 작업한다.
4. 학습이 된 프로그램을 작동시켜 긍정과 부정으로 분류하는지 확인을 한다.

>[출처:로고](https://blog.naver.com/hn03055/222730453539)&nbsp;/&nbsp;[출처:로고](http://wiki.hash.kr/index.php/%ED%8C%8C%EC%9D%B4%EC%B0%B8)

## 2. 데이터

### 2.1 데이터 소스
| ratings | reviews | label |
|----------|---|---|
| 5 | 배공빠르고 굿 | 1 |   
| 2 | 택배가 엉망이네용 저희집 밑에층에 말도없이 놔두고가고 | 0 |   
| 5 | 아주좋아요 바지 정말 좋아서2개 더 구매했어요 이....  | 1 |  
| 2 | 선물용으로 빨리 받아서 전달했어야 하는 상품이 였.... | 0 |  
| 5 | 민트색상 예뻐요. 옆 손잡이는 거는 용도로도 사용되네요 ㅎㅎ | 1 |    
| 2 | 비추합니다 계란 뒤집을 때 완전 불편해요 ㅠㅠ 코팅도.... | 0 |   
| 1 | 주문을 11월6에 시켰는데 11월16일에 배송이 왔네요 .... | 0 |  
| 2 | 넉넉한 길이로 주문했는데도 안 맞네요 별로예요 | 0 |  
| 별점 | 고객이 남긴 텍스트 리뷰 | 부정(0), 긍정(1) | 
### 2.2 탐색적 데이터 분석

### 2.3 데이터 전처리

## 3. 결과

### 3.1 계발환경
<img src="https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=Python&logoColor=white"/></a>
<img src="https://img.shields.io/badge/PyTorch-E34F26?style=flatsquare&logo=PyTorch&logoColor=white"/></a>
<img src="https://img.shields.io/badge/PyCharm-000000?style=flat-square&logo=PyCharm&logoColor=white"/></a>


