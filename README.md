# 📦 Skill Prompts

LLM 분석 프레임워크 모음.
Claude 전용 스킬(.skill)과 범용 프롬프트(.md) 두 가지 형태로 관리합니다.

---

## 📁 스킬 목록

| 스킬 | 설명 | 트리거 |
|---|---|---|
| [service-analysis](./service-analysis/) | 서비스·플랫폼 종합 분석 | "○○ 분석해줘", "○○ 서비스 어때?" |

---

## 🚀 사용 방법

### Claude (스킬 설치)
1. `SKILL.md` 파일을 다운로드
2. Claude 설정 → Skills → 설치

### ChatGPT / Codex / Gemini (범용)
대화 시작 시 `service-analysis-prompt.md` 파일 첨부
또는 아래 Raw URL을 복사해서 붙여넣기:

```
https://raw.githubusercontent.com/webn77/skill-prompts/main/service-analysis/service-analysis-prompt.md
```

### GPT Builder (Custom GPT)
GPT Builder → Configure → Instructions에 `service-analysis-prompt.md` 내용 붙여넣기

### API (System Prompt)
```python
import requests

url = "https://raw.githubusercontent.com/webn77/skill-prompts/main/service-analysis/service-analysis-prompt.md"
system_prompt = requests.get(url).text

# OpenAI
response = client.chat.completions.create(
    model="gpt-4o",
    messages=[
        {"role": "system", "content": system_prompt},
        {"role": "user", "content": "토스 분석해줘"}
    ]
)

# Anthropic
response = client.messages.create(
    model="claude-sonnet-4-6",
    system=system_prompt,
    messages=[{"role": "user", "content": "토스 분석해줘"}]
)
```

---

## 📝 업데이트 방법

```bash
# 스킬 수정 후
git add .
git commit -m "feat: 스킬명 - 변경 내용"
git push origin main
```

범용 `.md` 파일은 push 즉시 Raw URL에 반영됩니다.
Claude `.skill` 파일은 재다운로드 후 재설치 필요.

---

## 🗂️ 파일 구조

```
skill-prompts/
├── README.md
└── service-analysis/
    ├── SKILL.md                     ← Claude 전용 스킬 파일
    └── service-analysis-prompt.md   ← 범용 LLM 프롬프트
```

---

## 버전 히스토리

| 버전 | 날짜 | 변경 내용 |
|---|---|---|
| v1.0 | 2026.03 | service-analysis 초기 버전 |

