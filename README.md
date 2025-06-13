# 🧪 딥러닝 텀 프로젝트: BERT vs SBERT 기반 뉴스 분류

## 🗂️ 프로젝트 개요 | Project Overview

본 프로젝트는 AG News 및 Microsoft MIND 데이터셋을 활용하여 BERT 및 SBERT 기반 뉴스 분류 모델을 구현하고 성능을 비교합니다.

This project implements and compares news classification models using BERT and SBERT on AG News and Microsoft MIND datasets.

## 📁 폴더 구조 | Directory Structure

```
DL-Term-Project/
├── agnews_bert/       # BERT + AG News 실험 노트북 및 README
├── agnews_sbert/      # SBERT + AG News 실험 노트북 및 README
├── mind_bert/         # BERT + MIND 실험 노트북 및 README
├── mind_sbert/        # SBERT + MIND 실험 노트북 및 README
└── README.md          # 메인 프로젝트 설명 파일
```

## 🔬 실험 구성 | Experiment Setup

총 6개의 실험을 구성하여 모델 성능을 비교하였습니다:

- **AG News (2종류 입력)**

  - 전체 본문 (Full Text)
  - 헤드라인 (Headline Only)

- **MIND (1종류 입력)**

  - 뉴스 제목 + 요약 (Rich Context)

각 입력 유형에 대해 BERT와 SBERT 모델을 각각 적용하였습니다.

## 📊 주요 결과 요약 | Key Findings

| Dataset      | Model | Input Type       | Accuracy (Val / Test) |
| ------------ | ----- | ---------------- | --------------------- |
| AG News      | BERT  | Full Text        | - / **94.8%**         |
| AG News      | SBERT | Full Text        | - / **94.3%**         |
| AG News      | BERT  | Headline Only    | - / **92.5%**         |
| AG News      | SBERT | Headline Only    | - / **83.3%**         |
| MIND (Large) | BERT  | Title + Abstract | **92.9% / 90.0%**     |
| MIND (Large) | SBERT | Title + Abstract | **93.3% / 90.3%**     |

## ⚙️ 개발 환경 및 기술 스택 | Tech Stack

- **개발 환경**: Elice Cloud (Linux + GPU)
- **언어 및 프레임워크**: Python, PyTorch, HuggingFace Transformers
- **핵심 라이브러리**:
  - `transformers`
  - `sentence-transformers`
  - `datasets`
  - `scikit-learn`, `pandas`, `tqdm`

## 📦 데이터셋 정보 | Dataset Info

### AG News

- 자동 다운로드 (`datasets.load_dataset("ag_news")`)
- 사전 토크나이징 및 라벨 구성 포함

### Microsoft MIND (Large)

- 직접 다운로드 필요: [https://msnews.github.io/](https://msnews.github.io/)
- 사용 파일: `news.tsv`
- 파일 위치 예시:
  - `/home/elicer/MINDlarge_train/news.tsv`
  - `/home/elicer/MINDlarge_dev/news.tsv`
  - `/home/elicer/MINDlarge_test/news.tsv`

## ✍️ 사용 방법 | How to Use

```bash
# clone
$ git clone https://github.com/YourID/20251R0136COSE47400.git
$ cd DL-Term-Project/

# 노트북 실행 전 필수 라이브러리 설치
$ pip install transformers sentence-transformers scikit-learn datasets pandas
```

각 폴더별 README와 `.ipynb`를 확인해 주세요.

