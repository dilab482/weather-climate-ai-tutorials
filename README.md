# weather-climate-ai-tutorials

# 기상 데이터 탐색

## 1. WeatherBench 2 ERA5 데이터 탐색 (2.wb2_eda.ipynb)

전 지구 기상 재분석 데이터인 **ERA5**를 `xarray`를 활용해 다루는 기초적인 방법을 학습합니다.

### 데이터 출처
- **Google Cloud Storage:** `gs://weatherbench2/datasets/era5/`
- **대표 GitHub 저장소:**  
  https://github.com/google-research/weatherbench2  
  (Google Research 공식 저장소)

### 주요 학습 내용

#### 1) 클라우드 데이터 연동
- Google Cloud Storage(GCS)에 공개된 **대용량 Zarr 데이터셋** 활용
- `xarray` + `Dask`를 이용한 **Lazy Loading**
- 로컬 저장 없이 클라우드 데이터를 효율적으로 처리

#### 2) 시공간 필터링
- 특정 **관심 지역 좌표(예: 서울)** 기준 데이터 추출
- **2020년 1년 기간** 기준 데이터 슬라이싱
- `xarray.sel()`을 활용한 시간 및 공간 필터링

#### 3) 시계열 분석 및 시각화
- **월별 총 강수량** 바 차트 시각화
- **6시간 간격 강수량 시계열 분석**
- **7일 이동평균(7-day Moving Average)**을 적용한 추세 분석


---

## 2. SEVIR (Storm Event ImageRy) 데이터셋 분석 (3.sevir_eda.ipynb)

극한 기상 이벤트 예측(**Nowcasting**) 딥러닝 모델 학습에 자주 사용되는 **고해상도 멀티모달 데이터셋 SEVIR**을 분석합니다.

### 데이터 출처
- **AWS S3:** `s3://sevir/`

### 대표 GitHub 저장소
https://github.com/MIT-AI-Accelerator/eie-sevir  
(MIT AI Accelerator & 미 공군 공식 튜토리얼 저장소)

### 주요 학습 내용

#### 1) 메모리 스트리밍 기반 데이터 접근
- `s3fs` + `h5py`를 활용
- 수십 GB 규모의 **HDF5 파일을 로컬 다운로드 없이 직접 스트리밍**
- 클라우드 기반 대용량 데이터 처리 방법 학습

#### 2) 멀티모달 데이터 시각화

SEVIR 데이터는 다음 **5개 관측 채널**로 구성됩니다.

| 채널 | 설명 |
|-----|-----|
| VIL | 레이더 기반 수직 적분 액체 수분량 |
| VIS | 가시광선 위성 영상 |
| IR069 | 적외선 채널 (6.9µm) |
| IR107 | 적외선 채널 (10.7µm) |
| LGHT | 낙뢰 데이터 |

각 채널의 특징을 확인하고 **동시에 시각화하여 비교 분석**합니다.

#### 3) 폭풍 이벤트 생애주기 분석
- 한 폭풍 이벤트의 **4시간 관측 데이터 분석**
- 총 **49개 프레임 시계열**
- 폭풍의 **생성 → 발달 → 소멸** 과정 추적

#### 4) 딥러닝 학습을 위한 데이터 전처리 가이드
- 채널별 **픽셀 값 분포 분석**
- **Normalization 전략 수립**
- **결측치 확인**
- **클래스 불균형(Class Imbalance) 점검**

이를 통해 **딥러닝 기반 Nowcasting 모델 학습에 적합한 데이터 품질을 검증**합니다.
