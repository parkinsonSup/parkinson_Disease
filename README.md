
# 🧠 Parkinson's Disease Voice Analysis

## 📋 프로젝트 소개
본 프로젝트는 **음성 데이터를 활용하여 파킨슨병(Parkinson's Disease)** 을 조기에 진단하고 예측하는 것을 목표로 합니다.  
음성의 특징적인 변화를 분석하여 머신러닝/딥러닝 기반 모델로 질병 여부를 판별합니다.

## 🎯 목표
- 파킨슨병 환자와 정상인의 음성 데이터를 수집 및 분석
- 주요 음성 특성(feature) 추출 및 전처리
- 다양한 머신러닝 알고리즘을 적용하여 질병 예측 모델 개발

## 🗂️ 데이터셋 설명

| 항목 | 내용 |
|:----|:-----|
| 샘플 수 | **195개** (31명 × 6회) |
| 참가자 | 31명 (23명 환자, 8명 정상인) |
| 발성 방식 | 모음 **/a/** 를 길게 지속하여 발성 (sustained phonation of /a/) |
| 마이크 조건 | 텔레모니터링 목적, 고정 마이크 사용 |
| 추출 피처 | Jitter, Shimmer, HNR, RPDE, DFA, PPE 등 총 22개 |

## 🧬 Feature 목록

| Feature Name | 설명 |
|:-------------|:-----|
| name | 샘플을 식별하는 문자열 (이름) |
| MDVP:Fo(Hz) | 기본 주파수 (Fundamental frequency) |
| MDVP:Fhi(Hz) | 최대 주파수 (Maximum frequency) |
| MDVP:Flo(Hz) | 최소 주파수 (Minimum frequency) |
| MDVP:Jitter(%) | 주파수 변동성 비율 |
| MDVP:Jitter(Abs) | 주파수 변동성 절댓값 |
| MDVP:RAP | RAP (Relative Average Perturbation) |
| MDVP:PPQ | PPQ (five-point Period Perturbation Quotient) |
| Jitter:DDP | DDP (Derivative of Difference of Periods) |
| MDVP:Shimmer | 진폭 변동성 비율 |
| MDVP:Shimmer(dB) | 진폭 변동성 (in dB) |
| Shimmer:APQ3 | 3-point Amplitude Perturbation Quotient |
| Shimmer:APQ5 | 5-point Amplitude Perturbation Quotient |
| MDVP:APQ | MDVP-based Amplitude Perturbation Quotient |
| Shimmer:DDA | DDA (Derivative of Difference of Amplitude) |
| NHR | 잡음 대 조화 성분 비율 (Noise-to-Harmonics Ratio) |
| HNR | 조화 대 잡음 성분 비율 (Harmonics-to-Noise Ratio) |
| RPDE | 비선형 동적 복잡도 (Recurrence Period Density Entropy) |
| DFA | 신호의 자기유사성 지수 (Detrended Fluctuation Analysis) |
| spread1 | 제1 스펙트럼 퍼짐 |
| spread2 | 제2 스펙트럼 퍼짐 |
| D2 | 프랙탈 차원 (Correlation Dimension) |
| PPE | 주파수 변동성 척도 (Pitch Period Entropy) |
| status | 0 = 정상, 1 = 파킨슨 환자 (종속 변수) |

## 📚 참고 문헌 및 비교

| No. | 제목 | 연도 | 분석 모델 | 데이터셋 | 독립변수 | 종속변수 | 정확도 | 비고 |
|:---|:----|:---|:--------|:--------|:--------|:--------|:--------|:----|
| 1 | Parkinson’s Disease Prediction Using Artificial Neural Network | 2022 | ANN (JNN 툴) | UCI (195개) | 22개 음성 피처 | status (0/1) | 100% | 과적합 가능성 있음, 툴 기반 단일 분할 실험 |
| 2 | Evaluating Speech Analysis Techniques for Parkinson’s Disease Detection: A Comparison of Machine Learning and Deep Learning Algorithms | 2024 | ANN, SVM, RF 등 7종 | UCI (195개) | 22개 음성 피처 | status (0/1) | 97.44% (ANN 기준) | 전 모델 비교, 정량지표 다양 (F1 등) |
| 3 | Parkinson’s disease detection based on features refinement through L1 regularized SVM and deep neural network | 2024 | L1 SVM + DNN | UCI + Sakar (2종) | 22~26개 피처 (L1 선택 포함) | status (0/1) | 100% (UCI), 96.4% (Sakar) | LOSO + 10-fold 모두 사용, 최적화된 구조 |

## ✨ 공통사항 요약
- 대부분 UCI의 `parkinsons.data`를 기반으로 분석
- 종속변수는 거의 모두 `status` (이진 분류)
- 주요 피처로 Jitter, Shimmer, HNR, RPDE, PPE, DFA 등이 반복 사용됨
- 최근 논문일수록 과적합 방지 및 일반화 성능 강조 (LOSO, L1 정규화, Dropout 등 활용)
- 평가지표는 Accuracy 외에 F1-score, Recall, Kappa 등으로 다양화됨

## 🛠️ 사용 기술
- Python 3.x
- Pandas, NumPy
- Scikit-learn
- Matplotlib, Seaborn

## 🌟 향후 계획
- 음성 데이터 추가 확보
- 다양한 머신러닝 및 딥러닝 알고리즘 적용
- 실시간 음성 진단 웹앱 구축
