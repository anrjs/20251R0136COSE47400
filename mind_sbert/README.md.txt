# 🧠 MIND Dataset + SBERT-style BERT 실험

## 📌 실험 목적

이 실험은 Microsoft의 MIND 뉴스 데이터셋을 활용하여  
**SBERT-style BERT 분류기**를 학습하고, 뉴스 기사 카테고리를 분류하는 모델 성능을 평가하는 것이 목적입니다.

- 입력: 뉴스 제목(`title`)과 요약문(`abstract`)을 연결한 rich context 문장
- 라벨: 뉴스 카테고리(`category`)를 정수 인덱스로 매핑
- 목표: 문맥이 풍부한 입력에 대해 SBERT-style 구조의 효과를 분석하고,  
  동일한 입력을 사용한 BERT baseline 모델과 성능을 비교

---

## 📦 데이터셋 정보

- 데이터 출처: [Microsoft MIND Dataset (MINDlarge)](https://msnews.github.io/)
- 사용 파일: `news.tsv` (뉴스 ID, 제목, 요약, 카테고리 포함)
- 데이터 위치 (Elice Cloud 기준): 
/home/elicer/MINDlarge_train/news.tsv
/home/elicer/MINDlarge_dev/news.tsv
/home/elicer/MINDlarge_test/news.tsv

- **GitHub에는 데이터 용량 문제로 포함되어 있지 않음**

### 다운로드 방법:

1. 위 링크에서 MIND Dataset(MINDlarge)을 다운로드
2. 압축 해제 후, `news.tsv` 파일을 위 경로에 배치

---

## 🔧 전처리 방식

- 입력 문장은 `title`과 `abstract` 컬럼을 공백 `" "` 으로 이어붙여 구성  
예: `"title" + " " + "abstract"`
- 이어붙인 문장을 SBERT-style 구조에서 사용할 수 있도록 `bert-base-uncased`로 토큰화
- `category` 컬럼을 정수 라벨로 매핑  
예: `{ 'b': 0, 'e': 1, 'm': 2, 't': 3, ... }`
- **훈련 데이터 기준으로 클래스별 샘플 수가 100개 미만인 카테고리는 제거**하여  
클래스 불균형 문제를 완화함

---

## ⚙️ 실행 환경 및 의존성

- 실험 환경: Elice Cloud (GPU 사용)
- 모델: `bert-base-uncased` + Mean Pooling (SBERT-style)
- 주요 라이브러리:
- `transformers`
- `torch`
- `datasets`
- `pandas`
- `scikit-learn`

### 설치 명령어 예시

```bash
pip install transformers torch datasets pandas scikit-learn
