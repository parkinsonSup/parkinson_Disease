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

## 🔥 최종 분석

- ✅ **KNN 모델이 가장 높은 정확도와 F1 스코어를 기록함**
- ✅ **Assemble 모델(Voting)도 전체적으로 안정적이고 고른 성능을 보임**
- ✅ **항상 1만 찍는 Base Model은 다른 모델보다 성능이 확연히 낮음**

---

## 📢 프로젝트 요약

> "음성 데이터 기반 파킨슨병 예측에서, KNN 모델이 최고의 성능을 보였고, 다수결 앙상블 모델 또한 높은 안정성과 정확도를 보여주었다."

---
