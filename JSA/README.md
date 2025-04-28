# Parkinson's Disease Detection Project

## 📚 프로젝트 개요

- 목표: 음성 데이터 기반으로 파킨슨병 여부를 예측하는 분류 모델 개발
- 데이터셋: [Parkinson's Disease Dataset](https://www.kaggle.com/datasets/gauravduttakiit/parkinson-disease-detection)
- 주요 작업:
  - 데이터 전처리
  - 여러 머신러닝 모델 학습
  - 모델 성능 비교 및 앙상블 모델 구축

---

## 🛠 진행 과정 요약

### 1. 데이터 준비 및 전처리
- 불필요한 `name` 컬럼 제거
- 결측치 없음 확인
- 특성별 데이터 분포 시각화 (히스토그램)
- 상관관계 분석 (Heatmap)

### 2. Feature/Label 분리
- 입력 변수(X)와 타겟(y = `status`) 분리

### 3. 학습/테스트 데이터 분할
- `train_test_split(test_size=0.2, random_state=42)`

### 4. 데이터 스케일링
- `StandardScaler` 사용하여 표준화 처리

### 5. 베이스라인 모델 성능
- 가장 많은 클래스를 찍을 경우 정확도: 약 **82%**

### 6. 개별 모델 학습 및 평가
- **Logistic Regression**
- **Decision Tree**
- **K-Nearest Neighbors (KNN)**

### 7. 모델 해석
- Feature Importance 시각화 (Logistic Coefficients, Decision Tree Feature Importances)
- Decision Tree 구조 시각화

### 8. 앙상블 모델 (Majority Voting)
- Logistic, Decision Tree, KNN 모델 예측을 다수결 투표로 결합

### 9. 모델 성능 비교
- Accuracy, Precision, Recall, F1 Score, AUC 계산 및 막대 그래프 시각화

---

## 📈 주요 결과 요약

| 모델 | Accuracy | Precision | Recall | F1 Score | AUC |
|:---|:---|:---|:---|:---|:---|
| Logistic Regression | 0.90 | 0.89 | 0.90 | 0.89 | (약 0.77) |
| Decision Tree | 0.74 | (낮음) | (낮음) | (낮음) | (약 0.73) |
| KNN | 0.95 | 0.95 | 0.95 | 0.95 | (약 0.90) |
| Assemble Model (Voting) | 0.93 | 0.93 | 0.93 | 0.93 | (약 0.88) |
| Base Model Prediction | 0.82 | 낮음 | 낮음 | 낮음 | 0.5 수준 |


---

# 📋 모델별 분류 결과 요약

## Logistic Regression

| 클래스 | precision | recall | f1-score | support | 해석 |
|:------|:----------|:-------|:---------|:--------|:----|
| 정상 (0) | 1.00 | 0.43 | 0.60 | 7개 | "정상이라고 예측한 것은 정확하지만, 실제 정상 중 많은 수를 놓침" |
| 환자 (1) | 0.89 | 1.00 | 0.94 | 32개 | "환자를 매우 잘 탐지했음" |

- 전체 정확도: **90%**
- 특징: 환자 예측은 훌륭하지만 정상 예측 recall(43%)이 낮음
- 개선 포인트: 정상 탐지율 개선 필요

---

## K-Nearest Neighbors (KNN)

| 클래스 | precision | recall | f1-score | support | 해석 |
|:------|:----------|:-------|:---------|:--------|:----|
| 정상 (0) | 1.00 | 0.71 | 0.83 | 7개 | "정확성 완벽, 정상 중 71% 탐지" |
| 환자 (1) | 0.94 | 1.00 | 0.97 | 32개 | "환자 탐지는 완벽 수준" |

- 전체 정확도: **95%**
- 특징: 환자와 정상 모두 양호한 분류 성능
- 개선 포인트: 정상 recall 71% → 더 높일 여지는 있음

---

## Decision Tree

| 클래스 | precision | recall | f1-score | support | 해석 |
|:------|:----------|:-------|:---------|:--------|:----|
| 정상 (0) | 0.83 | 0.71 | 0.77 | 7개 | "정상 탐지 무난하나 완벽하진 않음" |
| 환자 (1) | 0.94 | 0.97 | 0.95 | 32개 | "환자 탐지는 매우 우수함" |

- 전체 정확도: **92%**
- 특징: 환자 분류 성능 매우 우수, 정상은 약간 부족
- 개선 포인트: 정상 클래스 분리 성능 추가 개선 가능성

---

# ✨ 전체 모델 비교

| 모델 | 전체 정확도 | 정상 (0) Recall | 환자 (1) Recall | 특징 |
|:-----|:-----------|:----------------|:---------------|:-----|
| Logistic Regression | 90% | 0.43 | 1.00 | 환자 탐지 완벽, 정상 탐지 약함 |
| K-Nearest Neighbors | 95% | 0.71 | 1.00 | 전체적으로 안정적이고 성능 높음 |
| Decision Tree | 92% | 0.71 | 0.97 | 환자 탐지 우수, 정상 탐지 무난 |

---

# 📚 최종 총평
- **환자(1)** 분류는 세 모델 모두 매우 우수 (특히 KNN, Logistic)
- **정상(0)** 분류는 KNN과 Decision Tree가 상대적으로 안정적
- **전체 정확도**는 KNN > Decision Tree > Logistic Regression 순
- **향후 개선 방향**: 정상(0) recall을 높이는 추가 데이터 확보 또는 하이퍼파라미터 튜닝 고려

---

## 🔥 최종 분석

- ✅ **KNN 모델이 가장 높은 정확도와 F1 스코어를 기록함**
- ✅ **Assemble 모델(Voting)도 전체적으로 안정적이고 고른 성능을 보임**
- ✅ **항상 1만 찍는 Base Model은 다른 모델보다 성능이 확연히 낮음**

---

## 📢 프로젝트 요약

> "음성 데이터 기반 파킨슨병 예측에서, KNN 모델이 최고의 성능을 보였고, 다수결 앙상블 모델 또한 높은 안정성과 정확도를 보여주었다."

---
