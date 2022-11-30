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
<p align="center"> <참고 인용 문헌 : KISTI 미래기술 위크시그널 성장예측보고서> </p>
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

> ```KISTI 위크시그널 자동탐지 프로세스```
<p align="center">
<img src="/img/KISTI_process.png" width="100%" height="100%" title="px(픽셀) 크기 설정" alt="kisti" align="center"></img>
</p>
</br>
</br>

> ```KIPI 위크시그널 자동탐지 프로세스```
<p align="center">
<img src="/img/KIPI_process2.png" width="100%" height="100%" title="px(픽셀) 크기 설정" alt="kipi" align="center"></img>
</p>

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

#### 1.2.2 CPC 집합 추출

> ```CPC Subgroup 별 모든 문서의 대표 벡터 추출```

- 문서 기준 : 4,661,158건
- subgroup 기준 : 128,395개 (주분류)

<p align="center">
<img src="/img/cpc_group_extract1.png" width="50%" height="50%" title="px(픽셀) 크기 설정" alt="taget" align="center"></img>
</p>
<p align="center"> <위크시그널을 위한 연도별 특허 문헌 수></p>
</br>
<p align="center">
<img src="/img/cpc_group_extract2.png" width="100%" height="100%" title="px(픽셀) 크기 설정" alt="taget" align="center"></img>
</p>
<p align="center"> <위크시그널을 위한 섹션 별 특허 문헌 수와 서브그룹> </p>
</br>

#### 1.2.3 CPC 활동성 측정

> ```CPC 규모성, 활동성 측정```

> 기존 KISTI 논문에서의 비중과 같은 비중으로 적용하여 규모성과 활동성 기준을 정하였습니다. KISTI에서는 1636만 논문 중 규모성 적용 시 210만건으로 13%가 해당되고, 특허문헌도 21만 건> 중 규모성 적용 시 2만 5천건으로 약 13%에 해당하였고 활동성에서 빈도수가 5년 내 최근 1년 기준으로 하였을 때 기존 KISTI 논문의 비중과 동일하게 됨을 알 수 있습니다. 이런 이유로 규
> 모성과 활동성의 기준은 조건3, 조건4의 아래 내용과 같습니다. 

- 조건3. 규모성 = 빈도수(최근1년) >= 1
- 조건4. 활동성 = 빈도수(최근1년)/빈도수(5년) >= 0.5

#### 1.2.4 Poping CPC 추출

> ```CPC 기술그룹 자동 생성```

> CPC 규모성, 활동성을 측정하여 적용 시 466만건 특허 중에서 20만건의 팝핑 문헌이 나오고, 이 문헌의 주분류를 확인해보면 9만 7천여개의 기술이 있슴을 알 수 있습니다. 팝핑 서브그룹은 > 섹션 별로 A섹션은 1만3천건, B섹션은 2만3천건, C섹션은 1만3천건, D섹션은 2천건, E섹션은 4천6백건, F섹션은 1만1천건, G섹션은 1만3천건, H섹션은 1만5천건이 나왔습니다. 주목할 점은 > H섹션의 경우 111만건의 문헌에서 1만5천개 기술밖에 안나온것을 알 수 있습니다. 규모성, 활동성의 조건에 해당하는 문헌 수가 생각보다 적게 나왔고 팝핑 기술이라고 생각되는 기술 또한 
> 적게 나왔기 때문인 것으로 보입니다.

<p align="center">
<img src="/img/cpc_group_extract3.png" width="100%" height="100%" title="px(픽셀) 크기 설정" alt="taget" align="center"></img>
</p>
<p align="center"> <위크시그널을 위한 섹션 별 특허 팝핑 문헌 수와 팝핑 서브그룹> </p>

#### 1.2.5 CPC 기술그룹 자동생성

> ```CPC 기술그룹 자동생성```

> CPC 기술그룹을 형성하는 것은 기술을 CPC subgroup으로 연결된 그래프 형식으로 표현하는 작업이 됩니다. 아래 예시 첫번째 그림을 보면 'H01L 39/2461'과 H01L 39/2454, H01L 39/2441, 
> H01L 39/2464 기술들이 벡터 유사도 거리가 0.25이내로 의미적으로 가까운 기술로 볼 수 있어 그래프로 표현된 하나의 기술로 다시 볼 수 있습니다. 두번째 그림을 보면, E섹션으로 표현된 
> 그래프 기술그룹이 생성된 것을 볼 수 있습니다.


<p align="center">
<img src="/img/cpc_auto_group1.png" width="30%" height="30%" title="px(픽셀) 크기 설정" alt="taget" align="center"></img>
</p>
<p align="center"> < CPC subgroup으로 연결된 기술그룹 그래프 예시> </p>
</br>

<p align="center">
<img src="/img/cpc_auto_group2.png" width="100%" height="100%" title="px(픽셀) 크기 설정" alt="taget" align="center"></img>
</p>
<p align="center"> < E섹션 내 CPC subgroup으로 연결된 기술그룹 그래프 예시> </p>

#### 1.2.6 CPC 기술그룹 통계

> ```CPC 기술그룹 통계```

> 466만건 특허 문헌은 subgroup 주분류 기준 12만 8천개 기술을 표현할 수 있고, 여기서 20만개 팝핑 문헌이 나오게 되고 팝핑 문헌 속 기술은 9만7천개가 나오게 됩니다. 9만 7천개 서브그
> 룹에서 기술그룹을 자동화 그래프 그룹핑하게되면 2만7천개의 기술들이 3,838개 그래프로 위크시그널을 보내게 됩니다. 아래 통계가 문헌 수와 서브그룹 기술 수 및 비중으로 표현되어 있습니> 다.

<p align="center">
<img src="/img/cpc_auto_group4.png" width="30%" height="30%" title="px(픽셀) 크기 설정" alt="taget" align="center"></img>
</p>
<p align="center"> <위크시그널을 위한 섹션 별 weak signal 서브그룹 수> </p>
</br>

<p align="center">
<img src="/img/cpc_auto_group5.png" width="100%" height="100%" title="px(픽셀) 크기 설정" alt="taget" align="center"></img>
</p>
<p align="center"> <위크시그널을 위한 섹션 별 weak signal 서브그룹 비중> </p>


#### 1.2.7 CPC 기술그룹 시각화

> ```CPC 기술그룹 시각화```

> CPC 기술그룹을 형성하여 전체 섹션으로 보게 되면 문헌 기준 20만건의 팝핑 특허 문헌이 생기고 CPC subgroup 기준 9만 7천여개의 팝핑기술이 생기는 것을 알 수 있습니다. 또한 이 팝핑 기> 술들이 그래프로 그룹화 되어 3,838개 팝핑 기술 그룹(그래프)이 생성됩니다. 이로써 미래 기술로 3,838개 위크시그널이 발견되었습니다.




#### 1.2.4 CPC 위크시그널 해석

> ```CPC 위크시그널 해석```

> ```KSIC 산업분류를 활용한 CPC 위크시그널 해석```

## 2. CPC 코드 활용 위크시그널 성장예측모델

### 2.1 학습모델: Graph Convolutional Neural Network

### 2.2 학습데이터: 기준데이터, 성장데이터, 데이터 증강

### 2.3 학습모델 성능 및 2022 위크시그널에 대한 성장성 예측결과

# Chaper 2. 위크시그널 126 : 10년 후 고성장이 예측된 126개 위크시그널
