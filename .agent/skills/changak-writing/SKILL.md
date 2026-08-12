---
name: changak-writing
description: 창각 크한(Hugo-Bear+Obsidian) 개인 블로그 글쓰기. seapy 스타일(미니멀·무장식·자기 생각 기록)로 포스트를 쓰고 발행하는 워크플로우. orca-cli/lekiwi/quant/DGX Spark 같은 데서 느낀 것, 철학·공간·AI 단상 작성 시 사용.
license: MIT
---
# 창각 (창현생각) — 글쓰기 스킬

## 이 블로그는 무엇인가

**창각** = 창현생각. 개인 생각의 짐을 벗는 최소한의 공간.
**꾸밈 없는 미니멀 블로그.**

- 장식·카테고리·태그·겉멋 전부 없음.
- 문장 하나 + 날짜 하나만으로 사는 글.
- "개인 생각을 적는 공간입니다" 수준의 겸손함.
- 짧을수록 좋음. 길어야 3~5문단.

**기술 스택:** 이 repo = Hugo (`hugo-bearblog` 테마) + Obsidian 볼트(`content/`에 내장) + GitHub Actions(`.github/workflows/hugo.yaml`) → **GitHub Pages** 자동 배포. (Cloudflare 아님)

---

## 포스트 위치 &amp; 발행 워크플로우

글은 `**content/blog/**` 에 마크다운으로 넣는다. `content/` 자체가 Obsidian vault 이므로,
Obsidian에서 `content/` 폴더를 vault로 열어서 쓰면 그대로 Hugo 포스트가 된다.

### 1. 새 글 작성 (Obsidian: `content/blog/제목.md`)

```markdown
+++
title= "제목"
date= YYYY-MM-DD
tags= ["post"]
draft= true
+++
```

- `draft= true` 로 시작 → 미리보기에만 보임 (배포에는 안 실림).
- 다 쓰면 `draft= false` 로 바꿔야 "발행"이 됨.

### 2. 로컬 확인

```bash
hugo server -D
# http://localhost:1313
```

### 3. 발행

```bash
git add -A
git commit -m "publish: <제목>"
git push origin master
```

가본은 브랜치가 `master`다. push되면 GitHub Actions(`hugo.yaml`)가 Hugo를 빌드한 뒤 GitHub Pages에 자동 배포한다. 반영까지 1~2분.

---

## 스타일 작성 원칙

1. **하나의 통찰만.** 글 하나 = 관찰 하나. 사족 없이 그 통찰을 명료하게 빼낸다.
2. **무장식.** hashtag, 이모지 도배, 큰 제목 난발 금지. 평문이 최고의 장식.
3. **솔직하게, 직접적으로.** 이론을 늘어놓지 말고 "내가 실제로 겪은 것"에서 시작.
4. **짧게.** 발상(원인) → 어떤 생각이 들었는가 → 왜 중요한가. 남은 건 버린다.
5. **기록이 아닌 사유.** 사실 나열이 아니라, 그 사실이 *자기 안에서 뭘 흔들었는지*.

### 주제의 씨앗

- **일상 작업에서**: orca-cli로 핸드오프하며 느낀 것, lekiwi, 퀀트(quant) 설정·실패·깨달음, DGX Spark로 뭘 돌려보며 풀었던 문제, 커맨드 라인/에이전트 워크플로우.
- **철학·공간·AI 단상** (사람이 많을 것): 존재론적 거주, 감정은 시간·이성은 공간, "아는 것은 모르는 것의 넓이", LLM이 가진/잃은 공간적 로고스, 지능의 탈중심화(Smarter-than-us), 언어 이전의 것.

---

## 예시 (톤 기준)

> 오늘 orca-cli, claude로 무한 루프에 빠졌다. 되는 것도 많아졌지만 그만큼
> "왜 그렇게 했냐"고 되묻는 일이 드물어졌다. 도구가 할 말을 대신 하기 시작하면
> 내가 생각한 걸 쓰는 게 아니라, 도구가 쓰기 좋은 생각을 하게 된다.
> 글도 똑같다. 결국 남는 건 내가 *굳이* 남긴 문장뿐이다.

---

## 주의

- `date=` 가 있어야 Hugo가 목록에 정렬한다.
- `tags= ["post"]` 유지 (테마 permalink 규칙 때문). 불필요한 태그는 안 붙인다.
- `content/` 안의 `.obsidian/` 파일은 커밋돼도 무해하지만, 찍히기 싫으면 `.gitignore` 처리.

