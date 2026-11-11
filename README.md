# 사진 한 장, 스레드 한 편

사진을 올리면 AI가 사진을 분석해서, 사람들이 공감할 Threads(스레드) 글을 **짧게 / 중간 / 길게** 3가지 버전으로 써주는 모바일 우선 웹앱입니다.

## 사용하기
- 웹 주소(GitHub Pages): https://myungkook96.github.io/Photo-Upload-Thread/
  - 설정 → "AI 연결 (API 키)"에 Anthropic API 키를 한 번 넣으면 이 주소에서 바로 글을 만듭니다.
  - 키는 그 기기 브라우저에만 저장되고 Anthropic API로만 전송됩니다. 요금은 키 주인 계정에 청구됩니다.
- 실행 링크(Claude 아티팩트): https://claude.ai/artifact/FTyenxc4iWyRYK7mcPH9GF
- claude.ai에 로그인한 상태에서 열어야 AI 기능이 동작합니다.

## 동작 방식
- **Claude 아티팩트 안**: 내장 "Claude에게 질문하기"(`sample` 기능, `images: true`)로 동작합니다. API 키가 필요 없고 여는 사람의 Claude 계정 사용량을 씁니다.
- **웹 주소(GitHub Pages)**: 사용자가 넣은 Anthropic API 키로 공식 SDK(`@anthropic-ai/sdk` 1.3.0, `anthropic-sdk.js`로 번들)를 써서 `claude-opus-5-5`를 직접 호출합니다. 구조화 출력(JSON 스키마)으로 응답 형식을 보장하고, 안전 거절 시 서버 측 대체 모델(`fallbacks: "default"`)을 씁니다.
- 의존성 없는 단일 HTML 파일입니다. 글꼴(Pretendard, 상용 한글 2,350자 서브셋)은 파일 안에 내장되어 있습니다.

## 주요 기능
- 사진 입력: 갤러리 · 카메라 · 끌어다 놓기 · 붙여넣기, 최대 4장, 긴 변 1568px JPEG 리사이즈
- 상황 14종, 말투 · 대상 독자 · 시점 · 이모지 · 추가 메모 옵션
- 결과: AI가 본 사진 요약 + 3가지 버전 (글자 수, 복사, 이 버전만 다시 쓰기, 직접 수정, Threads 열기, 공유, 토픽 태그)
- 보관함(브라우저 저장, 최근 30개, 즐겨찾기), 글씨 크게 모드, 다크모드

## 수정 후 다시 게시하기
`index.html`을 고친 뒤 Claude Code에서 아티팩트로 같은 URL에 다시 게시하면 됩니다.
