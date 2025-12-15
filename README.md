# 대전시 대중교통 통행수요 예측 프로젝트

## 프로젝트 개요

본 프로젝트는 **한남대학교 스마트SW인재양성사업단·빅데이터응용학과**에서 진행한 **'제1회 지역사회 문제해결형 빅데이터 AI 활용공모전'**의 일환으로 수행되었습니다.

대전시의 대중교통 통행수요를 예측하는 것을 목표로 하며, AutoGluon을 활용한 자동화 머신러닝 기법을 적용했습니다.

## 프로젝트 구조

```
Team_티머니_토마스/
├── code/                          # 분석 및 모델링 코드
│   ├── Autogluon.ipynb           # AutoGluon 모델 학습
│   ├── data_gener.ipynb          # 데이터 전처리 및 생성
│   ├── Machine_Learnig_visualization_EDA.ipynb  # EDA 및 시각화
│   ├── MS_tomas.ipynb            # 추가 분석
│   └── pkl_model.ipynb           # 모델 로드 및 예측
├── data/                          # 데이터 파일
│   ├── merged_data.csv           # 학습 데이터
│   ├── merged_test.csv           # 테스트 데이터
│   └── ...                       # 기타 데이터 파일
├── AutogluonModels_pkl/          # 학습된 모델 파일
├── model_explanation/            # 모델 설명 문서
├── visualization/                # 시각화 결과물
└── README.md                     # 프로젝트 설명 문서
```

## 주요 특징

- **AutoGluon 활용**: 다양한 머신러닝 모델을 자동으로 앙상블하여 최적의 성능 도출
- **회귀 문제**: 통행수요(RIDE_DEMAND) 예측
- **평가 지표**: MAE (Mean Absolute Error)
- **다양한 모델 앙상블**: CatBoost, LightGBM, XGBoost, RandomForest, Neural Networks 등

## 사용 기술 스택

- **Python 3.10+**
- **AutoGluon 0.8.2**: 자동화 머신러닝 프레임워크
- **Pandas**: 데이터 처리
- **NumPy**: 수치 연산
- **Scikit-learn**: 머신러닝 유틸리티
- **Jupyter Notebook**: 분석 환경

## 설치 방법

1. 저장소 클론
```bash
git clone <repository-url>
cd Team_티머니_토마스
```

2. 가상환경 생성 및 활성화 (권장)
```bash
python -m venv venv
source venv/bin/activate  # Windows: venv\Scripts\activate
```

3. 필수 패키지 설치
```bash
pip install -r requirements.txt
```

## 데이터 파일

> **참고**: 대용량 데이터 파일(100MB 이상)은 GitHub 파일 크기 제한으로 인해 저장소에 포함되어 있지 않습니다. 
> 
> 프로젝트를 실행하려면 `data/` 디렉토리에 다음 데이터 파일들을 준비해야 합니다:
> - `merged_data.csv`: 학습 데이터
> - `merged_test.csv`: 테스트 데이터
> - 기타 필요한 데이터 파일들

## 사용 방법

### 1. 데이터 준비
- `data/` 디렉토리에 학습 및 테스트 데이터를 준비하세요

### 2. 모델 학습
`code/Autogluon.ipynb` 노트북을 실행하여 모델을 학습합니다.

```python
from autogluon.tabular import TabularPredictor
import pandas as pd

train = pd.read_csv('data/merged_data.csv')

predictor = TabularPredictor(
    label='RIDE_DEMAND', 
    problem_type='regression', 
    eval_metric='mae'
).fit(train)
```

### 3. 예측 수행
`code/pkl_model.ipynb` 노트북을 실행하여 예측을 수행합니다.

```python
test = pd.read_csv('data/merged_test.csv')
predictions = predictor.predict(test)
```

## 모델 성능

학습 데이터에 대한 MAE: **2.27**

## 팀 정보

- 팀명: 티머니 토마스
- 주최: 한남대학교 스마트SW인재양성사업단·빅데이터응용학과
- 대회: 제1회 지역사회 문제해결형 빅데이터 AI 활용공모전

## 라이선스

본 프로젝트는 교육 및 연구 목적으로 개발되었습니다.

## 참고사항

- 모델 파일(.pkl)과 대용량 데이터 파일은 .gitignore에 포함되어 있습니다.
- 필요시 Git LFS를 사용하여 대용량 파일을 관리할 수 있습니다.

