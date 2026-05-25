# Anthropic Academy Practice

Anthropic Academy 공식 코스를 수강하며 연습 문제를 풀이한 코드 저장소입니다.

감사(Audit) 도메인에 AI를 실전 적용하기 위한 기반기를 쌓는 과정이며,
각 코스는 아래 순서대로 수강합니다.

최종 목표는 Claude API로 감사 업무중 일부를 자동화하고,
MCP를 통해 Excel,사내 시스템과 연동되는 실전 수준의 AI 감사 도구를 만드는 것입니다.(별도정산표 및 기타 회계자료를 참고하여 자동적으로 감사조서를 작성하는 등)
네 개의 코스는 이 목표를 향한 단계별 빌드업으로 구성했습니다.

---

## 풀이 방식

- 강의의 실습 문제는 원본이 영어로 제공되나, **실습문제 풀이는 감사(Audit) 업무와 연관된 질문과 시나리오로 대체**하여 실전 맥락에서 학습하였습니다.
- 평가 도구(PromptEvaluator) 등 코드 인프라는 원본 그대로 활용하되, **프롬프트와 데이터셋을 감사 시나리오로 구성**하는 데 집중하였습니다.
- 예시: 별도정산표 이상계정 분석, 감사절차 추천, 기말감사 인터뷰 질문 생성, 차입금 약정 위반 시 유동/비유동 분류 판단 등

---

## 수강 코스 및 선택 이유

### 1. Claude 101 — 모델 이해
- 링크: https://anthropic.skilljar.com/claude-101/383389
- Claude의 기본 구조와 동작 원리를 이해하기 위한 출발점.
  도구를 다루기 전에 도구의 특성과 한계를 먼저 파악해야 한다고 판단했습니다.
- Claude의 사용법, 프롬프트 작성 원칙 등 간략하게 구성되어 있고 연습문제는 포함되어 있지 않습니다.
  
### 2. Building with the Claude API — 핵심 개발 역량
- 링크: https://anthropic.skilljar.com/claude-with-the-anthropic-api/287818
- API 호출, 프롬프트 엔지니어링, Tool Use, RAG, 에이전트 워크플로우까지
  실제 시스템을 만들기 위한 핵심 역량을 다루는 메인 코스입니다.
  조서 자동화 프로젝트의 기술적 토대가 되는 강의입니다.
- **학습 현황**: Prompt Evaluation, Prompt Engineering Techniques 섹션 완료.
  Tool Use with Claude 섹션 완료 — Tool functions, Multi-turn conversations with tools,
  Implementing multiple turns, Using multiple tools, Fine-grained tool calling,
  Text editor tool, Web search 까지 실습 완료.
  RAG and Agentic Search 섹션 완료 — 텍스트 청킹, 임베딩, RAG 흐름 구현,
  BM25 어휘 검색, 멀티 인덱스 하이브리드 파이프라인 실습 완료.

### 3. Introduction to MCP — 외부 시스템 연동
- 링크: 
- Model Context Protocol을 통해 Claude를 외부 시스템과 연결하는 방법을 학습합니다.
  감사 업무에서 Excel, 사내 DB 등과의 연동이 필수적이기에 선택했습니다.

### 4. MCP: Advanced Topics — 실전 통합
- 링크: 
- MCP 심화 과정으로, 복잡한 도구 체인과 실전 수준의 통합을 다룹니다.
  앞선 세 코스를 하나의 시스템으로 엮어내는 마지막 단계입니다.

---

## 폴더 구조

2026-05-11 기준으로 강의 목차 순서에 맞춰 파일을 재분류했다.
그동안 실습 파일이 `Building with the Claude API/` 한 폴더에 쌓이면서
어느 파일이 어느 강의 챕터에 해당하는지 커밋 이력을 뒤져야만 파악할 수 있는 상태였다.
Building with the Claude API 공식 목차를 기준으로 챕터별 폴더를 만들어 파일을 이동했다.

앞으로는 새 실습 파일을 만들 때마다 해당 챕터 폴더에 바로 넣고,
파일명도 강의 챕터 번호와 매칭되게 짓는다.
학습 진도 추적과 포트폴리오 가시성 양면에서 이 구조를 유지하는 것이 낫다고 판단했다.

실습 파일명 규칙:
실습파일은 해당 챕터 안에서의 실습 순번을 먼저 매기고,
그 뒤에 챕터 약칭 → 챕터 내 강의 번호 → 강의 제목을 붙이는 방식으로 구성한다.

예) `실습002_tools_007_Multi-turn_conversations_with_tools.ipynb`
→ Tool use with Claude 챕터의 2번째 실습 파일이며,
  해당 챕터의 7번째 강의이고, 강의 제목은 Multi-turn conversations with tools.

```
Building with the Claude API/
├── 001. Accessing Claude with the API/     ← API 기초, 시스템 프롬프트, 온도 제어, 실습 #1~3
│   ├── 실습_System prompts.ipynb
│   ├── 실습_Temperature.ipynb
│   ├── 실습문제#1_chat exercise.ipynb
│   ├── 실습문제#2_system prompts exercise.ipynb
│   └── 실습문제#3_structured data exercise.ipynb
├── 002. Prompt evaluation/                 ← 프롬프트 평가 파이프라인, 실습 #4
│   ├── 001_prompt_evals_학습자료_다운로드.ipynb  (외 강의자료 3종)
│   ├── 실습_Model based grading.ipynb
│   ├── 실습_Model based grading and code based grading.ipynb
│   ├── 실습_Running the eval.ipynb
│   └── 실습문제#4_exercise on prompt evals.ipynb
├── 003. Prompt engineering techniques/     ← 프롬프팅 기법, 실습 #5
│   ├── 002_prompting_예시_학습자료_다운로드.ipynb
│   ├── 실습_prompting.ipynb
│   └── 실습문제#5_exercise on prompting.ipynb
├── 004. Tool use with Claude/              ← 도구 정의·schema·tool use 루프, 멀티 툴, 스트리밍, 빌트인 도구(텍스트 편집/웹 검색) (실습 #1~7)
│   ├── 실습001_tools_tool_functions.ipynb
│   ├── 실습002_tools_007_Multi-turn_conversations_with_tools.ipynb
│   ├── 실습003_tools_008_implementing_multiple_turns.ipynb
│   ├── 실습004_tools_009_Using_multiple_tools.ipynb
│   ├── 실습005_tool_streaming_010_Fine_grained_tool_calling.ipynb
│   ├── 실습006_tools_010_text_editor_tool.ipynb
│   ├── 실습007_tools_12_web_search.ipynb
│   └── 실습007_tools_12_web_search_예제.ipynb
└── 005. RAG and Agentic Search/            ← 청킹·임베딩·벡터DB·BM25·하이브리드 검색 (실습 #1~6)
    ├── 실습001_chunking_Text chunking strategies_002.ipynb
    ├── 실습002_embeddings_Text embeddings_003.ipynb
    ├── 실습003_vectordb_implementing the RAG flow_005.ipynb
    ├── 실습004_bm25_BM25 lexical search_006.ipynb
    └── 실습006_hybrid_A Multi-IndexRAGpipeline_007.ipynb
```
