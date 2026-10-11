# 기계학습 미니프로젝트#1
# 2026-2 강남대학교 기계학습 강의
# 작성자 세대 추측 NLP 모델

- 조원 
김시울, 홍민기

- 데이터 출처
(1) 국립국어원 모두의 말뭉치 (https://corpus.korean.go.kr)
사용 데이터: 신문 말뭉치, 문학(소설) 말뭉치, 메신저/웹 말뭉치

(2) AI Hub (https://aihub.or.kr)
사용 데이터: 감성 대화 말뭉치, 한국어 멀티세션 대화

- NLP모델 출처(Hugging Face Hub)
(1) klue/roberta-base
(2) monologg/koelectra-base-v3-discriminator
(3) beomi/KcELECTRA-base-v2022

- 저장소 구조

[Git 제외]: 저작권&용량 문제로 깃허브 저장소에 업로드 불가능

MachineLearning/
├── README.md                            # 프로젝트 메인 안내 문서
└── MiniPrj#1/
    ├── .gitignore                       # Git 추적 제외 설정 파일
    ├── requirements.txt                 # 필요 패키지 목록
    ├── preprocess.py                    # 원본 데이터 정제 및 라벨링 스크립트
    ├── train.py                         # 모델 학습 및 파인튜닝 실행 스크립트
    ├── main.py                          # 추론 및 테스트 실행 스크립트
    ├── data/
    │   ├── README.md                    # 데이터 관련 상세 안내 문서
    │   ├── sample/
    │   │   └── sample_data.csv          # 데이터 형식 확인용 샘플 파일
    │   ├── lexicon/
    │   │   ├── common_words.txt         # 세대 무관 대중적 공통 어휘 사전
    │   │   ├── age_keywords.json        # 세대별 특징 어휘 사전
    │   │   └── year_keywords.json       # 연도별 유행어 및 시대 특징 어휘 사전
    │   ├── raw/                         # [Git 제외] 다운로드한 원본 데이터셋 보관 폴더
    │   └── processed/                   # [Git 제외] 전처리 완료된 데이터셋 저장 폴더 
    |       ├── train.csv                # [Git 제외] 학습 데이터셋 
    |       ├── val.csv                  # [Git 제외] 검증 데이터셋 
    |       └── test.csv                 # [Git 제외] 테스트 데이터셋 
    └── models/
        ├── README.md                    # 모델 아키텍처 및 가중치 안내 문서
        ├── pipeline.py                  # 텍스트 유형 판별 및 모델 분기 추론 모듈
        ├── scoring.py                   # 어휘 가중치 계산 및 점수 보정 모듈
        └── checkpoints/                 # [Git 제외] 파인튜닝 완료된 모델 가중치 저장 폴더
            ├── type_classifier/         # [Git 제외] KLUE-RoBERTa 가중치
            ├── clean_predictor/         # [Git 제외] KoELECTRA 가중치
            └── noisy_predictor/         # [Git 제외] KcELECTRA 가중치
