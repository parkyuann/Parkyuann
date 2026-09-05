# 박유안 | AI · Data Engineer

> **좋아 보이는 결과에 먼저 만족하기보다, 왜 그런 결과가 나왔는지 확인하고 재현 가능한 방식으로 문제를 해결합니다.**

데이터와 AI 시스템은 결과가 그럴듯하다는 이유만으로 신뢰할 수 없다고 생각합니다. 지표와 출력 뒤에 숨은 데이터 누수, 검증 분포의 차이, 모호한 근거, 운영 환경의 제약을 먼저 살피고, 원인을 좁힌 뒤 해결책이 실제로 효과가 있는지 다시 검증하는 개발을 지향합니다.

## How I work

1. **문제를 관찰 가능한 단위로 나눕니다.** 평균 점수 하나가 아니라 오류 유형, 고오차 구간, 후보 충돌, 데이터·환경 경계를 함께 확인합니다.
2. **가설보다 근거를 우선합니다.** 로컬 성능과 실제 리더보드, 검색 결과와 공식 근거, 오프라인 실험과 서비스 동작을 구분합니다.
3. **원인을 고친 뒤 다시 검증합니다.** 과적합 징후가 있으면 피처·검증 구조를 조정하고, 근거가 유일하지 않으면 추측으로 답하지 않도록 시스템의 실패 경계를 설계합니다.

## Projects

### [KOSIS API 기반 RAG 뉴스 수치 사실검증 시스템](https://github.com/parkyuann/likelion5)

`Python` `FastAPI` `BGE-M3` `Qdrant` `BM25` `RRF` `React` `Docker`

뉴스 문장의 수치 주장을 구조화한 뒤 KOSIS 공식 통계와 대조하는 사실검증 시스템입니다. 검색 결과를 답으로 간주하지 않고, release-pinned 메타데이터로 항목·차원·기간·단위를 하나의 좌표로 결박한 뒤 공식 셀 조회와 결정론적 비교를 수행하도록 설계했습니다. 후보가 충돌하거나 근거가 부족하면 그럴듯한 판정을 만들지 않고 clarification 또는 `UNVERIFIABLE`로 종료합니다.

### [문맥 기반 문장 순서 예측 · DACON](https://github.com/parkyuann/dacon-sentence-order-prediction)

`Python` `PyTorch` `Hugging Face Transformers` `scikit-learn`

섞인 한국어 문장 4개의 순서를 맞히는 24개 순열 완전일치 과제입니다. 규칙 기반 기준선에서 pairwise·listwise 모델을 비교하고, 5-fold OOF 평가로 선택 편향을 줄였습니다. 성과가 실제 적용 분포에서 재현되지 않은 재랭킹 시도는 채택하지 않았습니다. **Public 0.8247, 241명 중 34위(상위 14.1%)**를 기록했습니다.

### [K-League 최종 패스 좌표 예측 · DACON](https://github.com/parkyuann/kleague-pass-prediction)

`Python` `LightGBM` `XGBoost` `CatBoost` `PyTorch`

공격 전개 이벤트 시퀀스에서 마지막 패스의 도착 좌표를 예측했습니다. 트리 앙상블과 시퀀스 멀티태스크 모델을 병행하고, 분포 이동·과적합 위험이 큰 피처와 Y-flip 증강을 제거한 뒤 정규화와 다중 시드 K-fold를 강화했습니다. 평균 오차뿐 아니라 고오차 구간을 시각화해 긴 패스의 과소예측과 특정 시작 지역의 난점을 분리 분석했습니다. **DACON 937팀 중 290위(상위 30%)**입니다.

### [SAC on Screen 데이터 기반 전국 배급 전략](https://github.com/parkyuann/sac-on-screen-strategy)

`Python` `pandas` `scikit-learn` `Folium`

예술의전당 예매 **511만 건**과 인구·문예회관·상영 실적을 결합해 상영지, 상영 횟수, 콘텐츠를 함께 설계한 공모전 프로젝트입니다. 229개 시군구를 단위로 수요·접근성·인프라를 분석해 거점 38곳과 순회상영지 44곳을 도출했습니다. 지표가 목표와 반대 방향을 가리킨 후보는 검증 후 기각하고, 데이터 프록시와 가정의 한계를 보고서와 운영 대시보드에 명시했습니다.

### [VOD 하이브리드 추천 시스템](https://github.com/parkyuann/Recommendation)

`Python` `ALS` `FastAPI` `React`

사용자 시청 로그의 협업 필터링, 콘텐츠 신호, 인기도를 결합한 추천 서비스입니다. 오프라인 실험 계층과 온라인 서빙 계층을 분리하고, 기존 사용자와 신규 사용자의 추천 경로를 달리해 콜드스타트에 대응했습니다. 1차 후보군을 만든 뒤 다양성을 반영해 재정렬했으며, 소규모 사용자 테스트에서는 하이브리드 방식이 평균 **4.6/8**을 기록했습니다. 다만 이 결과를 일반 성능으로 확대 해석하지 않고, 이후 로그 기반 평가로 보완할 과제로 남겼습니다.

## Tech

`Python` · `PyTorch` · `scikit-learn` · `FastAPI` · `React` · `Docker` · `PostgreSQL` · `Qdrant` · `OpenSearch`

## Contact

[![Gmail](https://img.shields.io/badge/Email-D14836?style=flat-square&logo=gmail&logoColor=white)](mailto:leo9911234@gmail.com)

---

결과를 내는 데서 멈추지 않고, **그 결과가 어떤 조건에서 성립하는지와 어디에서 실패하는지까지 설명할 수 있는 AI 시스템**을 만들고자 합니다.
