# <img src="/img/kipi_logo.png" width="5%" height="3%" title="px(픽셀) 크기 설정" alt="kipi" align="left">KIPI DATA INSIGHT 제2호</img>

특허 DATA를 활용한 미래 기술 위크시그널 성장예측 분석
======================

> 이 글은 '[**KISTI DATA INSIGHT 제19호 : 미래기술 위크시그널 성장예측보고서**](https://www.kisti.re.kr/post/data-insight?t=1668036309836)'와 
> '[**KISTI DATA INSIGHT 제15호 : 미래기술 위크시그널**](https://www.kisti.re.kr/post/data-insight?t=1668036309836)'의 내용을 많은 부분 참고하였고 인용하였습니다.
> 아래 설명하는 실험들은 특허데이터만을 적용한 내용입니다.
> 또한 KISTI 미래기술 위크시그널 분석 방법이나 데이터에서 차이가 있음을 미리 알려드립니다. 


</br>
</br>
<p align="center">
<img src="/img/weaksignal_cover_19.png" width="40%" height="30%" title="px(픽셀) 크기 설정" alt="cover19" align="center"></img>
</p>
<p align="center"> 참고 인용 문헌 : KISTI 미래기술 위크시그널 성장예측보고서 </p>
</br>
</br>

# Chaper 1. 미래 기술 위크시그널 - CPC코드 활용편
## 1. CPC코드 활용

> ```왜 CPC 코드를 활용할까?```

> 위에 기술된 위크 시그널의 기술 탐지는 결국 키워드 단위로 이용되는 것이고, 미래 기술을 키워드의 집합으로 탐지하게 됩니다. 그러나 특허에서는 전세계적으로 잘 활용하는 기술체계가 있습
> 니다. CPC(Cooperative Patent Code)로 기술을 최대 약 27만여개로 분류하는 코드가 이에 해당합니다. 마침 한국특허정보원에서는 CPC 자동분류 예측 인공지능 모델을 구축하였고 성능도 뛰
> 어나기 때문에 이를 활용해서 위크시그널에 적용해 보려고 합니다. 또한 단순히 키워드 단위로 기술을 표현하게되면 보통 우리가 겪게되는 키워드의 한계를 가지게 될 수 있습니다. 동음이의어
> 나 이음동의어로 생기는 의미 표현의 한계를 넘을 수 없기에 CPC 기술 단위로 위크시그널을 탐지하는데 큰 의미가 있다고 판단합니다.

### 1.1 CPC 코드 활용 위크시그널 자동탐지 프로세스

### 1.2 위크시그널 자동탐지 현황

#### 1.2.1 실험 데이터

- 2001년 ~ 2019년 
- 특허 공개공보 데이터 
- 전체 CPC(Cooperative Patent Classification)의 Subgroup 대상
- Subgroup 기준 주분류 128,395개
- 전체 특허 4,661,158건
- 대상 필드는 발명의 명칭, 요약, 배경기술, 기술분야, 청구항으로 적용

<p align="center">
<img src="/img/target_patent_docs2.png" width="100%" height="100%" title="px(픽셀) 크기 설정" alt="taget" align="center"></img>
</p>
</br>

#### 1.2.2 CPC 벡터 추출

> ```Subgroup 별 모든 문서의 대표 벡터 추출```

#### 1.2.3 CPC 활동성 측정

> ```CPC 규모성, 활동성 측정```

#### 1.2.4 Poping CPC 추출

> ```CPC 기술그룹 자동 생성```

#### 1.2.4 Poping CPC 시각화 

> ```CPC 기술그룹 시각화```

#### 1.2.4 CPC 위크시그널 해석

> ```CPC 위크시그널 해석```

> ```KSIC 산업분류를 활용한 CPC 위크시그널 해석```

## 2. CPC 코드 활용 위크시그널 성장예측모델

### 2.1 학습모델: Graph Convolutional Neural Network

### 2.2 학습데이터: 기준데이터, 성장데이터, 데이터 증강

### 2.3 학습모델 성능 및 2022 위크시그널에 대한 성장성 예측결과

# Chaper 2. 위크시그널 126 : 10년 후 고성장이 예측된 126개 위크시그널
