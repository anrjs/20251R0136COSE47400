# 🧠 MIND Dataset + BERT 실험

## 📌 실험 목적

이 실험은 Microsoft의 MIND 뉴스 데이터셋을 활용하여  
BERT 기반 뉴스 카테고리 분류 모델을 학습하는 것을 목표로 합니다.

- 입력: 뉴스 제목(`title`)과 요약문(`abstract`)을 연결하여 문맥이 풍부한 입력 구성
- 라벨: 뉴스 카테고리 (`category`)
- 목적: rich context에서의 BERT 분류 성능 측정 및 short text 대비 비교


## 📦 데이터셋 정보

- 데이터 출처: [Microsoft MIND Dataset (MINDlarge)](https://msnews.github.io/)
- 사용 파일: `news.tsv` (뉴스 ID, 제목, 요약, 카테고리 등이 포함)
- 데이터 위치: 
/home/elicer/MINDlarge_train/news.tsv
/home/elicer/MINDlarge_dev/news.tsv
/home/elicer/MINDlarge_test/news.tsv

- **GitHub에는 데이터 용량 문제로 포함되지 않음**

### 다운로드 방법:

1. 위 링크에서 MIND 데이터셋(MINDlarge)을 다운로드
2. 압축 해제 후, `MINDlarge_train/news.tsv` 파일을 위 경로에 저장

---

## 🔧 전처리 방식

- 입력 문장은 `title`과 `abstract` 컬럼을 **공백 `" "`** 으로 이어붙여 구성  
  예: `"title" + " " + "abstract"`
- 이어붙인 텍스트는 BERT tokenizer로 토큰화되어 모델에 입력됨
- `category` 컬럼은 정수 인덱스로 매핑하여 레이블을 구성  
  예: `{ 'b': 0, 'e': 1, 'm': 2, 't': 3, ... }`  
- 데이터 전처리 과정 중, **훈련 세트에서 최소 샘플 수가 100개 미만인 카테고리는 제거**하여  
  클래스 불균형 문제를 완화함

## ⚙️ 실행 환경 및 의존성

- 실험 환경: Elice Cloud (GPU 사용)
- 필요한 주요 라이브러리:
- `transformers`
- `torch`
- `datasets` (선택)

### 설치 명령어 예시

```bash
pip install transformers torch
