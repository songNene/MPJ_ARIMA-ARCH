# Mini Project: ARIMA & ARCH

시계열 데이터를 활용하여 예측 모델을 구성하고, ARIMA 및 ARCH(GARCH 포함) 모델을 적용해 모델링한 프로젝트입니다.

---

## 프로젝트 개요

| 항목          | 내용                                                                 |
|---------------|----------------------------------------------------------------------|
| 데이터셋       | AirPassengers                                                        |
| 분석 대상      | 월별 항공 여객 수 (1949~1960)                                        |
| 사용한 모델    | ARIMA(4,1,2), GARCH(1,1)                                             |
| 주요 기법      | 로그 변환, 차분, auto_arima, 조건부 이분산성 분석, 모델 평가 지표 확인 |

---

## 모델별 분석 요약

### 1. ARIMA 모델

| 항목                  | 내용                                                                 |
|-----------------------|----------------------------------------------------------------------|
| 데이터 변환            | 로그 변환 후 차분 적용 (비정상성 제거 및 분산 안정화)                |
| 모델 선택 방식         | `auto_arima`를 통한 자동 모델 선택 (계절성 고려)                      |
| 최적 모델              | ARIMA(4,1,2)                                                         |
| 예측값 (`preds`)       | 총 29개 시점의 예측 결과 (Series 형태)                               |
| 신뢰 구간 (`conf_int`) | 각 예측값에 대한 95% 신뢰구간 제공 (numpy array, shape = (29,2))      |
| 시각화 분석            | 예측값과 신뢰구간을 함께 시각화하여 추세 반영 및 안정성 확인            |
| 최종 해석              | 모델이 로그 변환된 시계열 데이터를 비교적 안정적으로 예측함             |

---

### 2. ARCH / GARCH 모델

| 항목                  | 내용                                                                 |
|-----------------------|----------------------------------------------------------------------|
| 적용 배경              | 잔차에서 조건부 이분산성(Conditional Heteroskedasticity) 발견            |
| 모델 설정              | GARCH(1,1) 모델 적용                                                 |
| 평가 지표              | AIC / BIC / p-value / 로그우도 등                                     |
| 해석 요약              | GARCH(1,1) 모델이 유의미하며, 변동성 포착에 적합                        |
| 시각화 결과            | 조건부 분산(Volatility)과 잔차를 비교하여 모델 적합도 시각적으로 검토     |

---

## 핵심 결과 정리

| 항목               | 결과 요약                                                                 |
|--------------------|--------------------------------------------------------------------------|
| ARIMA 성능 평가     | 예측값이 대부분 신뢰 구간 내에 포함되며, 추세를 잘 반영함                  |
| GARCH 성능 평가     | 시계열 데이터의 분산 구조를 잘 포착하며, 예측 잔차가 안정적으로 분포함       |
| 모델 결론           | 시계열 예측에서는 ARIMA가, 분산 예측에서는 GARCH(1,1)가 각각 적합함         |

---

## 사용 라이브러리

- `pmdarima` - auto_arima
- `arch` - ARCH, GARCH 모델
- `matplotlib`, `seaborn` - 시각화
- `pandas`, `numpy` - 데이터 처리

---

## 파일 구성

| 파일명                          | 설명                                                   |
|--------------------------------|----------------------------------------------------------|
| `MiniProject_ARIMA,ARCH.ipynb` | 전체 실험과 분석이 포함된 Jupyter Notebook               |
| `AirPassengers.csv`            | 분석에 사용된 월별 항공 여객 수 시계열 데이터 (1949~1960) |

