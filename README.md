# Stop Slop KO

한국어 콘텐츠에서 억지 대구·비교, 번역투, 내부 기획의도와 제작 메모의 노출을 줄이는 글쓰기 스킬입니다.

**Codex · Claude Code · Claude 호환 | v1.1.0 | MIT**

블로그, SNS, 고객 안내, 제안서, 슬라이드 문구를 만들거나 다듬을 때 씁니다. 실제 비교 정보와 원문의 사실, 작성자의 관점을 보존합니다.

기존 원고에는 **원문 → 수정 제안 → 이유**를 기본으로 보여줍니다. 원본을 유지하면서 앞뒤 문맥에 맞는 대체문장을 제안합니다. 삭제가 적절한 경우에는 삭제 제안임을 밝히고 이유를 설명합니다.

## Codex에서 설치하기

Codex에 아래 요청을 붙여 넣으세요.

```text
$skill-installer https://github.com/hslee-byte/stop-slop-ko 저장소의 스킬을 설치해줘.
스킬은 저장소 루트에 있고 이름은 stop-slop-ko야.
```

설치 후 다음 턴에서 `$stop-slop-ko`로 호출합니다. 이미 설치되어 있으면 중복 설치하지 않고 현재 설치 경로와 버전을 확인하세요.

터미널에서 직접 설치하려면 다음 명령을 사용합니다. 설치 대상 폴더가 아직 없을 때 실행하세요.

```bash
mkdir -p ~/.agents/skills
git clone https://github.com/hslee-byte/stop-slop-ko.git ~/.agents/skills/stop-slop-ko
```

Codex용 `SKILL.md`와 UI 메타데이터 `agents/openai.yaml`을 포함합니다. 별도 프로그램이나 API 키는 필요하지 않습니다. 설치 방식에 따라 개인 스킬 경로는 `~/.agents/skills/` 또는 `~/.codex/skills/`가 될 수 있습니다. 같은 이름을 두 경로에 중복 설치하지 마세요. [OpenAI 스킬 안내](https://learn.chatgpt.com/ko-KR/docs/build-skills)

## Codex 사용 예시

```text
$stop-slop-ko 아래 원고를 고객용으로 다듬어줘.
사실과 말투는 유지해줘.
```

이 요청에는 원문·수정 제안·이유를 보여주며 원본을 직접 수정하지 않습니다.

```text
$stop-slop-ko 이 자료로 링크드인 글을 써줘.
내 관점과 말투를 살리고, 기획 메모는 본문에 넣지 마.
```

```text
$stop-slop-ko 수정은 내가 할게.
억지 대비와 내부 기획 메모가 섞인 부분의 대체문장을 제안해줘.
```

완성된 글을 바로 받으려면 “완성본만 줘”, 기존 파일에 적용하려면 “이 제안대로 파일에 반영해줘”라고 요청하세요. 새 글 작성에는 완성본을 제공합니다. 이미 반영을 요청했다면 재확인 절차를 추가하지 않습니다.

한국어 콘텐츠 작성·수정 요청에 자동으로 선택될 수도 있습니다. 적용 기준을 분명히 하려면 스킬 이름을 명시하세요.

## 어떤 문장을 고치나요?

| 원문 | 수정 제안 | 이유 |
|---|---|---|
| 단순한 회의록이 아닙니다. 다음 주 할 일을 정리한 문서입니다. | 다음 주 할 일을 정리한 문서입니다. | 불필요한 부정 문장의 삭제 제안입니다. 문서가 담은 내용은 유지합니다. |
| 신청 절차의 간소화를 통해 이용 편의성의 개선을 도모합니다. 신청 항목을 8개에서 4개로 줄였습니다. | 신청하기 편하도록 입력 항목을 8개에서 4개로 줄였습니다. | 명사 중심 문장을 풀어 쓰고, 목적과 변경 수치를 한 문장에 연결합니다. |
| 전문성을 부각하기 위해 절차와 예상 소요 시간을 안내합니다. | 절차와 예상 소요 시간을 안내합니다. | 내부 기획 목적을 빼는 제안입니다. 독자에게 제공하는 정보는 남깁니다. |

위 문장과 숫자는 가상 예시입니다. [14개 수정 전후 사례](references/examples.md)에서 실제 비교, 불확실성, 작성자 말투를 보존하는 경우도 확인할 수 있습니다.

## 다른 도구에서 설치하기

### Claude Code

```bash
mkdir -p ~/.claude/skills
git clone https://github.com/hslee-byte/stop-slop-ko.git ~/.claude/skills/stop-slop-ko
```

`/stop-slop-ko`로 호출합니다. 팀 저장소 안에서만 쓰려면 프로젝트의 `.claude/skills/`에 스킬 폴더를 넣습니다. [Claude Code 공식 안내](https://code.claude.com/docs/en/skills)

### Claude 웹·데스크톱

1. [최신 릴리스](https://github.com/hslee-byte/stop-slop-ko/releases/latest)에서 `stop-slop-ko-v1.1.0.zip`을 받습니다.
2. `Customize → Skills → + → Create skill → Upload a skill`에서 ZIP을 올리고 스킬을 켭니다.
3. “stop-slop-ko를 사용해서 아래 글을 다듬어줘”라고 요청합니다.

GitHub가 자동 생성하는 Source code ZIP 대신 위 이름의 릴리스 첨부파일을 사용하세요. 첨부파일은 최상위 폴더가 `stop-slop-ko/`인 스킬 업로드 형식입니다. [Claude 공식 안내](https://support.claude.com/en/articles/12512180-use-skills-in-claude)

### 파일을 첨부하는 일반 채팅

`SKILL.md`와 `references/examples.md`를 첨부하고 “첨부한 규칙과 사례를 이번 글의 편집 기준으로 적용해줘”라고 요청합니다. 해당 대화에 규칙을 전달하는 방법입니다.

## 구성과 개선

- [SKILL.md](SKILL.md): AI가 읽는 핵심 작성·검수 규칙
- [references/examples.md](references/examples.md): 가상 사례 14개와 적용 점검 요청
- [agents/openai.yaml](agents/openai.yaml): Codex 표시 이름·설명·기본 요청문
- [LICENSE](LICENSE): MIT 라이선스

이 저장소에서 원본을 관리하고, 버전별 ZIP은 Releases에 제공합니다. 반복되는 문제는 개인정보를 지운 원문과 원하는 수정문을 [이슈](https://github.com/hslee-byte/stop-slop-ko/issues)에 남겨 주세요.

문서 형식·설치·압축 검증과 실제 문체 개선은 별도로 확인합니다. 사용 중인 모델의 결과를 사례 파일의 적용 점검 요청과 팀 원고로 비교해 보세요.

## 출처

[Hardik Pandya의 stop-slop](https://github.com/hardikpandya/stop-slop)에서 군더더기와 상투적인 문장 구조를 줄이는 방향을 참고했습니다. 한국어 어법, 억지 대비의 판단 기준, 내부 기획의도 노출 방지, 의미 보존 규칙과 가상 사례를 새로 작성한 변형입니다. 원본의 공식 번역판은 아닙니다. MIT 라이선스 고지를 함께 배포합니다.
