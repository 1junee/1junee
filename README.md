<img src="https://capsule-render.vercel.app/api?type=wave&color=0:3a7bd5,100:00b4db&height=240&section=header&text=1junee&fontSize=64&fontColor=FFFFFF&fontAlignY=36&desc=AI%20%C2%B7%20Multimodal%20Retrieval&descSize=20&descAlignY=56" width="100%" alt="1junee" />

서울시립대학교 수학과에서 컴퓨터과학부를 복수전공하고 있습니다.
AI Agent의 도구 중간 결과와 최종 답변을 비교해 **오류가 어느 단계에서 생겼는지** 추적하고, 판단 근거를 확인할 수 있는 AI 서비스를 만듭니다.
작은 실험으로 가설을 검증하며 답을 좁혀갑니다.

## Featured Work

### SoccerNet Challenge 2026 – VQA · 2025.10 – 2026.04
축구 경기 이미지·영상에 대한 자연어 질문에 답하는 국제 VQA 챌린지에서, 오픈소스 SoccerAgent의 실행 과정을 분석해 도구를 개선·개발했습니다.

- **역할**: 개인 프로젝트
- **내가 한 일**: 실행 계획과 도구별 중간 결과를 최종 답변과 대조해 반복 오답을 유형·처리 단계별로 분류하고, 14개 질문 유형 중 3개 도구를 재설계
  - **Replay Grounding**: VLM이 선택지에 없는 답을 출력 → 리플레이·후보 영상 임베딩의 코사인 유사도로 재정의
  - **Grounding Count**: 인원 누락·역할 혼동 → 장면 정보 추출, 조건 매칭, 대상 탐지·집계 단계로 나눈 신규 Tool 개발
  - **Camera Detection**: 선택지 밖 답변 → 현재 선택지 라벨만 Few-shot 예시로 주고 출력 범위 제한
- **결과** (검증셋 정답률):

  | 도구 | 문항 | 기존 → 개선 |
  |---|---|---|
  | Replay Grounding | 160 | 31.9% → 75.6% (+43.7%p) |
  | Grounding Count | 100 | 44.0% → 76.0% (+32.0%p) |
  | Camera Detection | 160 | 40.6% → 64.4% (+23.8%p), 선택지 밖 답변 68건 → 0건 |

- **대회 성적**: 최종 12위 · 정확도 86.0%, 공식 결과 논문에 제안 방법 수록(공동저자)
- **링크**: [저장소](https://github.com/1junee/SoccerAgent_Submission) · [공식 결과 논문](https://arxiv.org/abs/2607.07320)
- **Stack**: Python · PyTorch · VLM · AI Agent · Multimodal Embedding

### F1T · VLM 기반 사용자 의도 추론 패션 상품 검색 · 2026.03 – 2026.06
자연어 요청과 참고 이미지로 적합한 패션 상품을 찾고 추천 근거를 함께 보여주는 검색 시스템입니다.

- **역할**: 4인 팀 프로젝트 · 팀장. 검색용 상품 설명문 생성, 최종 검색·순위화, 추천 근거 생성과 비교 평가 담당
- **검색 시스템 구현**
  - 요청과 참고 이미지에서 유지·변경할 특징을 합친 목표 상품 설명문(Target Description) 생성
  - 이미지 유사도와 소재 유사도를 분리 계산해 `0.8 × 이미지 + 0.2 × 소재`(휴리스틱 가중치)로 Top-10 순위화
  - 조건이 있으면 SQL로 후보를 좁히고, 없으면 pgvector HNSW 인덱스로 탐색
  - 1차 검색의 과도한 속성 추론으로 후보가 0개가 되는 문제를 SQL 조건 비교로 분석하고 팀원과 필터 조정
- **평가**: 19,833개 상품 · 102개 질의의 Top-1을 기존 검색(상품 설명문–이미지 유사도)과 사람 평가로 비교

  | 항목 | 기존 | 개선 |
  |---|---|---|
  | 요청 조건 완전 충족 | 75건 | 80건 (78.4%) |
  | 실패 | 10건 | 5건 |
  | 평균 후보 수 | 19,833개 | 2,707개 (-86.35%) |
  | 평균 결과 생성 시간 | 6.47초 | 7.14초 (+0.67초) |

- **팀 성과**: 캡스톤디자인 우수작품상
- **링크**: [저장소](https://github.com/cs-f1t/f1t_clean)
- **Stack**: Python · FastAPI · VLM · Multimodal Embedding · Supabase(PostgreSQL) · pgvector · HNSW

## Experience

| 기간 | 활동 | 내용 |
|---|---|---|
| 2023.03 – 2027.02 (예정) | 서울시립대학교 수학과 | 컴퓨터과학부 복수전공 · 학점 4.19/4.5 |
| 2026.07 | 캡스톤디자인 우수작품상 | 서울시립대학교 공학교육혁신센터 |
| 2026.01 | 딥러닝 부트캠프 경진대회 공과대학장상 | 서울시립대학교 공과대학 |
| 2025.02 | IBM AI 해커톤 대상 | 경기과학기술대학교 빅데이터혁신융합대학 |
| 2024.08 | 빅데이터 캠프 경진대회 최우수상 | 경기과학기술대학교 빅데이터혁신융합대학 |

**Certification**: ADsP (2026.06) · SQLD (2026.03)

## Study & Practice

| 주제 | 내용 | 저장소 |
|---|---|---|
| Reasoning Segmentation (2026.01, 4인 팀) | VLM의 역할을 후보 Box 생성과 조건 검증으로 나누고, 실패 시 2×2·3×3 분할 재탐색. mIoU 범용 0.384 → 0.501, 해양 쓰레기 0.258 → 0.751 | [deepfive](https://github.com/AICOSS-DeepFive/deepfive) |

## Tech Stack

- **Language**: Python, C++
- **AI/ML**: PyTorch, Vision-Language Model, Multimodal Retrieval
- **Backend**: FastAPI
- **Database**: PostgreSQL, Supabase, pgvector

## Contact

heo1jun8640@gmail.com · [LinkedIn](https://www.linkedin.com/in/wonjun-heo/)
