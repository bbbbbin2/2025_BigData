# 🚗 🚦 교통사고 통계 분석 및 향후 사고 건수 예측

---

## 📌 프로젝트 개요

본 프로젝트는 **최근 10년간(2015~2024) 교통사고 통계 데이터**를 기반으로
교통사고 발생 추세와 구조적 위험 요인을 다각도로 분석하고,

> **“교통사고는 실제로 줄어들고 있는가?”**
> **“어떤 집단과 조건에서 사고 위험이 집중되는가?”**
> **“현재 추세가 유지된다면 향후 사고 건수는 어떻게 변화할 것인가?”**

를 데이터 기반으로 검증·예측하는 것을 목표로 합니다.

단순 통계 요약에 그치지 않고,
**연령·지역·위반 유형·사고 유형·기상 상태·시간 흐름**을 종합적으로 분석하였으며,
**Prophet / LSTM 기반 시계열 모델**을 활용하여 **향후 5년간 교통사고 추세를 예측**했습니다.

---

## 📁 프로젝트 폴더 구성

```
2025_BigData/
├─ data/
│   ├─ 교통사고통계(연도별).xlsx
│   ├─ 교통사고통계(월별).xlsx
│   ├─ 교통사고통계(기상상태별).xlsx
│   ├─ 사고유형별_교통사고.xls
│   ├─ 위반유형별_교통사고.xls
│   ├─ 연령대별_교통사고.xls
│   ├─ 지역별_교통사고.xls
│   ├─ 음주운전(지역)교통사고통계.xlsx
│   ├─ 교통사고통계(음주 3년간).xlsx
│   └─ 화물차.csv
│
├─ notebook/
│   ├─ 전처리.ipynb
│   ├─ 교통사고_통계_및_예측_시각화.ipynb
│   ├─ 음주교통사고_시각화.ipynb
│   └─ 화물차_교통사고_시각화.ipynb
│
├─ README.md
└─ 빅데이터_예측_이혜빈_202344100.pdf
```

---

## 📦 사용 데이터

| 구분       | 설명                   |
| -------- | -------------------- |
| 연도별 교통사고 | 사고·사망자·부상자 연도별 추이    |
| 월별 교통사고  | 계절성 및 월별 사고 패턴       |
| 사고 유형별   | 차대차, 차대사람 등          |
| 위반 유형별   | 안전운전의무위반, 신호위반, 과속 등 |
| 연령대별     | 10대~65세 이상 사고 분포     |
| 지역별      | 시·도별 사고 집중도          |
| 기상 상태별   | 맑음·비·눈·안개            |
| 음주운전     | 연령·지역·시간대별 음주사고      |
| 화물차 사고   | 사고 다발 지역 분석          |

---

## 🔧 기술 스택

* **Python**
* **Pandas / NumPy** : 데이터 처리 및 전처리
* **Matplotlib / Seaborn / Folium** : 시각화
* **Prophet** : 단기 시계열 예측
* **LSTM (TensorFlow / Keras)** : 장기 추세 예측
* **scikit-learn**
* **MySQL / CSV** (저장 및 관리)

---

## 🔍 분석 절차 요약

### 1️⃣ 데이터 전처리

* 병합 셀(Merged Cells)로 인한 `Unnamed` 컬럼 제거
* 다중 헤더 정규화
* 결측치(NaN) 제거
* 문자형 숫자 → 정수형 변환
* 합계/알 수 없음 행 제거
* 지역명 불일치 통합 (예: 서울특별시 → 서울)
* Wide → Long 형태 변환(Unpivot)
* 공통 전처리 함수화 적용

---

### 2️⃣ 주요 시각화 항목

#### 최근 10년 교통사고 사망자·부상자 추이
<img width="1565" height="547" alt="image" src="https://github.com/user-attachments/assets/414980d5-5d97-4856-9787-1b622c382edd" />

#### 최근 5년 월별 평균 사고 건수
<img width="1266" height="466" alt="image" src="https://github.com/user-attachments/assets/0a10b36f-116a-4ef5-8170-0014c685ebde" />

#### 월별 교통사고 치명도 Top 3
<img width="1166" height="466" alt="image" src="https://github.com/user-attachments/assets/3dc2a883-abb7-4a59-804a-b89d93acae4f" />

# 기상 상태별 사고 비중 및 치명도
<img width="1336" height="419" alt="image" src="https://github.com/user-attachments/assets/e5a4eebe-5c0c-40fa-bc42-8c81aad642a1" />


# 연령대 사고 집중도
  <img width="966" height="766" alt="image" src="https://github.com/user-attachments/assets/53bb2aca-1c5e-4d0e-ba66-a51fd970c225" />

# 연령대별 치사율 및 65세 이상 운전자 연도별 교통사고 증가율 
<img width="1517" height="456" alt="image" src="https://github.com/user-attachments/assets/df90f077-88b4-4ecf-b4b7-ce9d74f1651f" />

# 지역별 사고 집중도
  <img width="966" height="765" alt="image" src="https://github.com/user-attachments/assets/d9b8f59a-bebd-455c-bece-6780ac67efc6" />

# 사고 유형별 / 위반 유형별 통계
<img width="1498" height="585" alt="image" src="https://github.com/user-attachments/assets/8dbf016f-557a-4b74-a0f6-d4f33cfcac13" />


# 음주운전 사고 시간대·연령대 분석
<img width="1490" height="534" alt="image" src="https://github.com/user-attachments/assets/fd0542c5-7b49-47a6-b9e0-b62f8eb5eacd" />
<img width="1328" height="537" alt="image" src="https://github.com/user-attachments/assets/82464e80-f113-4681-93e2-a3d0ad76fc60" />




* 화물차 사고 다발 지역 지도 시각화
<img width="992" height="623" alt="image" src="https://github.com/user-attachments/assets/ad1903e2-1908-43e5-8e12-9b55de7786a3" />




---

## 📊 주요 분석 결과

### 🔹 1) 연령대별 사고 특징
<img width="1517" height="456" alt="image" src="https://github.com/user-attachments/assets/df90f077-88b4-4ecf-b4b7-ce9d74f1651f" />
* **65세 이상**에서 사고 비중이 높음
* 고령 운전자(65세 이상)는 **최근 5년간 사고 증가율이 지속 상승**

---

### 🔹 2) 위반 유형별 영향
<img width="966" height="766" alt="image" src="https://github.com/user-attachments/assets/ac7c164b-644f-4f33-b02a-42b4536df497" />

* 모든 연령대에서 **안전운전의무 불이행**이 가장 큰 사고 원인
* 20~40대는 **신호위반·중앙선 침범** 등 복합 위반 비중이 큼

---

### 🔹 3) 기상 상태 영향
<img width="849" height="636" alt="image" src="https://github.com/user-attachments/assets/6a9fd1f6-610e-4f13-a3c9-feb2ad7ed09f" />

* 사고 발생 비중: **비·흐림 날씨**에서 사고 다수 발생
* 사고 치명도: **눈길 사고**는 발생 빈도는 낮지만 치명도 최고

---

### 🔹 4) 지역별 사고 집중
<img width="966" height="765" alt="image" src="https://github.com/user-attachments/assets/c98995e5-39cd-476a-b1a7-40d3753ac835" />

* 최근 5년간 사고의 **절반 이상이 수도권(경기·서울)** 집중
* 교통량·도시 구조와 밀접한 상관관계 확인

---

## 🔮 예측 모델 설계

### 📈 예측 모델 ① — Prophet 기반 시계열 예측
<img width="1365" height="566" alt="image" src="https://github.com/user-attachments/assets/5a35dfca-28ab-43d5-a524-c2c9a6b3528b" />

* **Input**: 연도별 사고 건수
* **Output**: 향후 5년 사고 발생량
* **결과**

  * 사고 건수·사망자 수 모두 **완만한 감소 추세 지속**
  * 급격한 반등 가능성은 낮음

---

### 📈 예측 모델 ② — LSTM 기반 장기 예측
<img width="1166" height="465" alt="image" src="https://github.com/user-attachments/assets/1e417316-e55e-4d62-a3a7-54466e1dd81c" />

* 비선형 구조 학습
* 정책·고령화·교통 환경 변화 반영 가능
* **장기적으로 구조적 감소 흐름 유지** 시사

---

## 🧪 프로젝트 의미 및 시사점

* 교통사고는 **단일 요인이 아닌 복합적 구조 문제**
* 고위험군(연령·시간대·위반 유형) 중심 정책 필요
* 기상 조건을 고려한 **사전 경고·예방 시스템** 활용 가능
* 데이터 기반 사고 예측은 **지자체 교통 정책 수립에 실질적 기여 가능**

---

## 📁 산출물

* 전처리 및 분석 노트북 (`.ipynb`)
* 정제된 교통사고 통계 데이터
* 시각화 결과 이미지
* 프로젝트 발표 자료 (PDF)

---

## 🔚 종합 결론

교통사고는 전반적으로 감소 추세에 있으나,
**특정 연령대·시간대·기상 조건·사고 유형에 집중되는 구조적 특성**을 보입니다.

따라서 향후 교통안전 정책은
단순 사고 건수 감소를 넘어,

* 고위험군 맞춤형 관리
* 보행자 보호 중심 도시 교통 환경 개선
* 데이터 기반 예측·선제 대응

으로 확장될 필요가 있습니다.

---

