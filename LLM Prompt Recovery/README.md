# Overview

LLM은 보통 글을 다시 쓰거나 텍스트 스타일에 관한 변화를 만드는 데 쓰이곤 한다. 이 대회의 목적은 주어진 텍스트를 변형하는 데에 사용된 LLM 프롬프트를 복원하는 것이다.

## Description

NLP 워크플로우에서는 텍스트를 다시 작성하는 것이 점점 더 많이 포함되지만, LLM에 효과적으로 프롬프트 하는 법에 대해서는 여전히 배울 점이 많다. 이 머신 러닝 대회는 이 문제에 대해 더 깊이 탐구할 수 있는 새로운 방식으로 설계되었다.

과제: 주어진 텍스트를 다시 작성하는 데에 사용된 LLM 프롬프트를 복원해라. 너는 1300+ 개의 원문 텍스트 데이터셋을 테스트할 것이다. 각 텍스트는 구글의 새로운 open model인 Gemma로 재작성된 텍스트와 짝지어져 있다.

## Evaluation

### Evaluation Metric

제출 파일에서의 각 행과 그 정답에 대해, sentence-t5-base 모델이 해당하는 임베딩 벡터를 계산하는 데에 사용되었다. 예측된 / 기대되는 프롬프트 쌍에 대한 점수는 지수 값으로 3을 사용한 Sharpened Cosine Similarity(SCS)를 사용하여 계산한다. SCS는 잘못된 답변에 대해 임베딩 벡터가 지나치게 높은 점수를 부여하는 현상을 완화한다. rewrite_prompt 값을 null로 두면 에러가 발생할 수 있다.

# Data

## Dataset Description

이 대회의 데이터셋은 Gemma 7b-it LLM이 비공개 프롬프트를 사용해 재작성한 텍스트 문단으로 구성된다.

이 대회의 목표는 어떤 프롬프트가 사용됐는지 추론하는 것이다.

### Files

**\[train/test\].csv**

- `id` - 행 식별자
- `original_text` - 원문 프롬프트
- `rewrite_prompt` - 정답 열. Gemma에게 제공된 프롬프트
- `rewritten_text` - Gemma의 출력

**\[sample_submission.csv\]**

- `id`
- `rewrite_prompt`
