# weather-climate-ai-tutorials

1. WeatherBench 2 ERA5 데이터 탐색 (2.wb2_eda.ipynb)
전 지구 기상 재분석 데이터인 ERA5를 xarray를 활용해 다루는 기초적인 방법을 학습합니다.

데이터 출처: Google Cloud Storage (gs://weatherbench2/datasets/era5/)

대표 GitHub 저장소: google-research/weatherbench2 (Google Research 공식 저장소)

주요 학습 내용:

클라우드 데이터 연동: GCS에 공개된 대용량 Zarr 데이터를 Dask Lazy Loading을 통해 효율적으로 불러오기

시공간 필터링: 특정 관심 지역(예: 서울 좌표) 및 기간(2020년 1년)을 기준으로 데이터 슬라이싱

시계열 분석 및 시각화: 월별 총 강수량 바 차트, 6시간 간격 강수량 시계열 및 7일 이동평균 플롯 시각화

2. SEVIR (Storm EVent ImageRy) 데이터셋 심층 분석 (3.sevir_eda.ipynb)
극한 기상 이벤트 예측(Nowcasting) 딥러닝 모델 학습에 자주 사용되는 고해상도 멀티모달 데이터셋인 SEVIR을 깊이 있게 분석합니다.

데이터 출처: AWS S3 (s3://sevir/)

대표 GitHub 저장소: MIT-AI-Accelerator/eie-sevir (MIT & 미 공군 공식 튜토리얼 저장소)

주요 학습 내용:

메모리 스트리밍: s3fs와 h5py를 이용해 수십 GB에 달하는 HDF5 파일을 로컬에 다운로드하지 않고 S3에서 직접 읽어오기

멀티모달 데이터 시각화: 5개 관측 채널(VIL: 레이더, VIS: 가시광선, IR069/IR107: 적외선, LGHT: 낙뢰)의 특성 확인 및 동시 시각화

생애 주기 분석: 폭풍 이벤트의 생성, 발달, 소멸에 이르는 4시간(49개 프레임) 시계열 변화 추적

딥러닝 전처리 가이드: 채널별 픽셀 값 분포 및 통계를 기반으로 정규화(Normalization), 결측치 확인, 클래스 불균형 등 모델 학습을 위한 데이터 품질 점검
