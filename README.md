# comparision_preprocessing

## 데이터

- NSMC(Naver  Sentiment Movie Corpus) 사용
- 한국어 영화 리뷰 데이터
- 말뭉치 크기 : 20만 문장(Train : 15만 // Test : 5만)

### 비교 방법

- 모델(LSTM / CNN / LSTM + CNN) 성능차이 비교
- 토큰단위에 따른 모델 성능차 비교
- 모델의 전처리 방법에 따른 성능 비교

### 토큰 단위(Tokenizing)

- 토큰화 정의 : 문장 처리의 최소 단위를 정의 하는 것
- 토큰화 기준
  - 어절
  - 형태소(Twitter 형태소 분석기 사용)
  - 음절
  - 음소

### 전처리 방법

- 전처리 : 문장 데이터를 사용에 적합하도록 모델의 입력전 수행하는 모든 행위
- 전처리 방법 기준
  - [블로그](https://bab2min.tistory.com/544)정의 불용어
  - 조사 제거
  - 특수문자 및 한자 제거
  - 명사만 추출
  - NSMC 말뭉치 가운데 최다 빈도 형태소 제거

### 결과 

1. 토큰단위에 따른 성능 비교

   | 모델 - 성능           | 어절  | 형태소 | 음절  | 음소  |
   | --------------------- | ----- | ------ | ----- | ----- |
   | LSTM - Loss           | 0.13  | 0.335  | 0.301 | 0.36  |
   | LSTM - Acc            | 0.778 | 0.852  | 0.84  | 0.802 |
   | LSTM - F1_score       | 0.783 | 0.854  | 0.838 | 0.809 |
   | CNN - Loss            | 0.158 | 0.241  | 0.278 | 0.411 |
   | CNN - Acc             | 0.785 | 0.855  | 0.846 | 0.794 |
   | CNN - F1_score        | 0.79  | 0.856  | 0.846 | 0.785 |
   | LSTM + CNN - Loss     | 0.143 | 0.383  | 0.403 | 0.29  |
   | LSTM + CNN - Acc      | 0.772 | 0.856  | 0.843 | 0.838 |
   | LSTM + CNN - F1_score | 0.766 | 0.856  | 0.842 | 0.838 |

2. 불용어 기준에 따른 성능 비교

   |                       | 블로그<br />불용어 | 조사 제거 | 특수문자 및 한자 | 명사 추출 | NSMC불용어 |
   | --------------------- | ------------------ | --------- | ---------------- | --------- | ---------- |
   | LSTM - Loss           | 0.242              | 0.24      | 0.242            | 0.415     | 0.242      |
   | LSTM - Acc            | 0.85               | 0.85      | 0.849            | 0.766     | 0.849      |
   | LSTM - F1_score       | 0.851              | 0.853     | 0.85             | 0.77      | 0.85       |
   | CNN - Loss            | 0.245              | 0.239     | 0.224            | 0.405     | 0.224      |
   | CNN - Acc             | 0.852              | 0.854     | 0.853            | 0.769     | 0.853      |
   | CNN - F1_score        | 0.853              | 0.854     | 0.853            | 0.773     | 0.853      |
   | LSTM + CNN - Loss     | 0.231              | 0.239     | 0.234            | 0.389     | 0.234      |
   | LSTM + CNN - Acc      | 0.852              | 0.852     | 0.851            | 0.765     | 0.851      |
   | LSTM + CNN - F1_score | 0.852              | 0.852     | 0.851            | 0.775     | 0.851      |

   * 모든 실험은 5회 진행 후 평균을 냄

### 결론

모델이나 불용어 처리의 방법보다 토큰의 단위가 모델의 성능에 큰 영향을 끼침

### 논문 자료

- [KSC 2019](https:/https://www.cseric.or.kr/literature/ser_view.php?SnxGubun=INME&mode=total&searchCate=&more=Y&research=Y&re_q1=&gu=INME000F9&cmd=qryview&SnxIndxNum=214252&rownum=1&totalCnt=49&q1_t=WWVvbmctU2VvayBTZW8=&listUrl=L3NlYXJjaC9yZXN1bHQucGhwP1NueEd1YnVuPUlOTUUmbW9kZT10b3RhbCZzZWFyY2hDYXRlPSZxMT1ZZW9uZy1TZW9rJTIwU2VvJm1vcmU9WSZmMT0mcmVzZWFyY2g9WSZyZV9xMT0=&q1=Yeong-Seok+Seo)

