<p align="center">
  <a href="https://getartcraft.com/">
    <picture>
      <source media="(prefers-color-scheme: dark)" srcset="docs/brand/artcraft-logo-white.svg">
      <img alt="ArtCraft" src="docs/brand/artcraft-logo.svg" width="200">
    </picture>
  </a>
</p>

<h1 align="center">DeckCraft — 한국어 인터페이스 에디션 (Korean UI Edition)</h1>

<p align="center">
  <b>순수 Rust로 구현된 오픈소스 프레젠테이션·슬라이드 쇼 프로그램 DeckCraft의 한국어(Korean) 인터페이스 버전입니다.</b><br>
  Microsoft PowerPoint(<code>.pptx</code>) 파일 열기·편집·저장, PDF/이미지 내보내기, 전체 화면 발표, CLI 및 AI 에이전트(MCP) 제어를 지원합니다.
</p>

<p align="center">
  <a href="https://github.com/JaebeenAhn/deckcraft/releases/tag/v0.11.1-ko.1"><img alt="Release: v0.11.1-ko.1" src="https://img.shields.io/badge/release-v0.11.1--ko.1-f26b1d?style=flat-square"></a>
  <img alt="Korean Localization: 100% (1,486 strings)" src="https://img.shields.io/badge/한국어%20번역-100%25%20(1%2C486%20항목)-2ea44f?style=flat-square">
  <img alt="License: MIT OR Apache-2.0" src="https://img.shields.io/badge/license-MIT%20OR%20Apache--2.0-blue?style=flat-square">
  <img alt="Written in Rust" src="https://img.shields.io/badge/written%20in-Rust-b7410e?style=flat-square">
  <img alt="Platforms" src="https://img.shields.io/badge/platforms-Windows%20·%20macOS%20·%20Linux%20·%20BSD%20·%20Web-555?style=flat-square">
</p>

<p align="center">
  <a href="https://github.com/JaebeenAhn/deckcraft/releases/download/v0.11.1-ko.1/deckcraft-0.11.1-ko-windows-x64-portable.zip"><b>📦 Windows x64 한국어 무설치 버전 바로 다운로드 (ZIP)</b></a> ·
  <a href="https://github.com/JaebeenAhn/deckcraft/releases/tag/v0.11.1-ko.1">릴리스 노트 (v0.11.1-ko.1)</a> ·
  <a href="https://github.com/storytold/deckcraft/pull/34#issuecomment-6432308306">Upstream PR #34 기여 내역</a>
</p>

---

## 한국어 인터페이스 미리보기 (Screenshots)

<p align="center">
  <img alt="DeckCraft 한국어 메인 편집기 화면" src="https://github.com/JaebeenAhn/deckcraft/releases/download/v0.11.1-ko.1/ko-editor.png" width="900"><br>
  <sub><b>메인 편집기 화면</b> — 리본 탭(홈, 삽입, 그리기, 디자인, 전환, 애니메이션, 슬라이드 쇼, 녹화, 검토, 보기) 및 슬라이드 캔버스 한국어 UI</sub>
</p>

<table>
  <tr>
    <td width="50%">
      <img alt="환경 설정 대화상자 (인터페이스 언어: 한국어)" src="https://github.com/JaebeenAhn/deckcraft/releases/download/v0.11.1-ko.1/ko-preferences.png"><br>
      <sub><b>환경 설정 (Preferences)</b> — 인터페이스 언어(시스템 기본값 / 한국어 / English) 실시간 전환</sub>
    </td>
    <td width="50%">
      <img alt="표 삽입 대화상자" src="https://github.com/JaebeenAhn/deckcraft/releases/download/v0.11.1-ko.1/ko-table.png"><br>
      <sub><b>표 삽입 대화상자</b> — 대화상자, 입력 필드 및 버튼 한국어 로컬라이제이션</sub>
    </td>
  </tr>
</table>

---

## 한국어 에디션 주요 변경 및 적용 사항

이 저장소는 공식 [`storytold/deckcraft`](https://github.com/storytold/deckcraft) 프로젝트와 다국어 아키텍처([PR #34](https://github.com/storytold/deckcraft/pull/34))를 기반으로 **한국어 인터페이스(`ko` / `ko-KR`)** 와 **한글 시스템 폰트 렌더링**을 추가한 버전입니다 ([Commit `b32a78ff`](https://github.com/JaebeenAhn/deckcraft/commit/b32a78ff10ee56c6197a6de27b34cd8b9aaa9d29)).

| 구분 | 수정 파일 | 상세 내용 |
|---|---|---|
| **한국어 번역 카탈로그** | [`crates/ui-egui/src/i18n/ko.tsv`](crates/ui-egui/src/i18n/ko.tsv) | 리본 메뉴, 명령 팔레트, 우클릭 컨텍스트 메뉴, 사이드 패널, 대화상자, 도형 150여 종, 표·차트, 전환·애니메이션, 발표자 보기, 단축키 안내 등 **총 1,486개 UI 문자열 100% 한국어 번역** |
| **로케일 엔진 및 수량 포맷** | [`crates/ui-egui/src/i18n.rs`](crates/ui-egui/src/i18n.rs) | `Language::Ko` (`한국어`, 코드 `ko`, 로케일 `ko` / `ko-KR` / `ko_KR.UTF-8`) 등록, OS 시스템 언어 자동 감지 및 한국어 수량 표기(`{count}개` 등) 지원 |
| **언어 선택 환경 설정** | [`crates/ui-egui/src/lib.rs`](crates/ui-egui/src/lib.rs), [`dialogs.rs`](crates/ui-egui/src/dialogs.rs) | `InterfaceLanguagePreference::Korean` 추가 및 **환경 설정 ▸ 인터페이스 언어** 드롭다운 연동 (`ui.json`에 설정 영구 저장) |
| **한글/CJK UI 폰트 폴백** | [`crates/ui-egui/src/theme.rs`](crates/ui-egui/src/theme.rs) | 기본 영문 폰트(`Inter`)에서 한글 음절(`U+AC00..U+D7A3`)이 네모(`□`)로 깨지는 현상을 방지하기 위해 Windows(`Pretendard`, `맑은 고딕`), macOS(`AppleGothic`), Linux(`나눔고딕`) 시스템 폰트 자동 로드 |
| **단위 테스트 검증** | `i18n::tests` (7종) | 키 중복·누락 검사, 자리표시자(`{name}`, `{count}`) 무결성 검사, 명령·메뉴·갤러리 전수 번역 검사 및 헤드리스 UI 렌더링 테스트 통과 |

---

## 다운로드 및 실행 방법 (Windows)

1. **[Releases 페이지 (`v0.11.1-ko.1`)](https://github.com/JaebeenAhn/deckcraft/releases/tag/v0.11.1-ko.1)** 에서 **`deckcraft-0.11.1-ko-windows-x64-portable.zip`** 파일을 내려받습니다.
2. 원하는 폴더에 압축을 해제한 뒤 **`deckcraft.exe`** 를 실행합니다.
3. 한국어 Windows 환경에서는 실행 즉시 **한국어 인터페이스**로 시작됩니다.
   - 수동으로 언어를 변경하려면 상단 좌측 **홈(집 모양) 아이콘 ▸ 환경 설정... ▸ 인터페이스 언어**에서 `한국어` 또는 `English`를 선택하세요.

---

## DeckCraft 주요 기능

- **슬라이드 제작**: 슬라이드 마스터 및 11가지 기본 레이아웃, 8종의 내장 테마(색상·글꼴 조합), 구역(Section) 관리, 슬라이드 노트, 메모(Comments), 머리글/바닥글, 사용자 지정 슬라이드 크기.
- **도형 및 드로잉**: 조절 핸들이 포함된 150개 이상의 기본 도형, 도형에 자석처럼 붙는 연결선(Connector), 자유형·곡선·자유 곡선 그리기, 도형 병합(결합, 조합, 조각, 교차, 빼기), 그라데이션·그림·패턴 채우기, 그림자·네온·부드러운 가장자리·반사 효과.
- **텍스트 및 서식**: 글꼴·단락 서식, 글머리 기호 및 번호 매기기, 다단(Columns) 편집, 텍스트 자동 맞춤(Autofit), 세로 텍스트, 날짜/슬라이드 번호 필드 및 하이퍼링크.
- **콘텐츠 삽입**: 그림 자르기 및 색 보정, 표 스타일, 차트, SmartArt 다이어그램, 오디오 및 비디오 재생(MP3, AAC, FLAC, Ogg, Opus, WAV, H.264, HEVC, VP9, AV1).
- **발표 및 애니메이션**: 모핑(Morph)을 포함한 슬라이드 전환 효과, 나타내기/강조/끝내기 및 이동 경로 애니메이션, 전체 화면 슬라이드 쇼, 발표자 보기(Presenter View), 레이저 포인터·펜 판서, 시간 예행연습.
- **파일 호환 및 내보내기**: Microsoft PowerPoint `.pptx` 파일 열기 및 저장, PDF 내보내기(슬라이드, 노트 페이지, 유인물), PNG/JPEG 고해상도 이미지 내보내기, 자동 복구(AutoRecover).
- **자동화 및 AI 연동 (CLI & MCP)**: 200개 이상의 모든 편집 명령을 명령줄(`deckcraft-cli`)과 JSON 제어 채널, AI 에이전트용 **MCP(Model Context Protocol)** 서버로 제어 가능.

---

## 소스 코드에서 직접 빌드하기 (Build from Source)

```bash
git clone -b i18n/korean https://github.com/JaebeenAhn/deckcraft.git
cd deckcraft

# 한국어 번역 카탈로그 단위 테스트 실행
cargo test -p deckcraft-ui-egui i18n::tests

# 릴리스 바이너리 빌드 (deckcraft GUI 및 deckcraft-cli)
cargo build --release -p deckcraft -p deckcraft-cli
```

---

<details>
<summary><b>🌐 Original English README (Upstream Overview)</b></summary>

<br>

## What works today

DeckCraft is in alpha, heading for beta (see the [roadmap](ROADMAP.md)).
Today it can:

- **Make decks**: slide masters and eleven layouts with placeholders that inherit position and
  formatting, eight original themes with colour and font schemes, sections, notes, comments,
  headers and footers, custom slide sizes.
- **Draw**: 150+ preset shapes with adjust handles, connectors that stay glued to shapes, freeform,
  curve and scribble tools, merge shapes (union, combine, fragment, intersect, subtract), gradient,
  picture and pattern fills, outlines with dashes and arrowheads, shadows, glow, soft edges and
  reflections.
- **Write**: in-place text editing with full font and paragraph formatting, bullets and numbering,
  columns, autofit, vertical text, fields and hyperlinks.
- **Add content**: pictures with crop and corrections, tables with styles, charts, SmartArt basics,
  audio and video (MP3, AAC, FLAC, ALAC, Ogg, Opus, WAV, AIFF; H.264, HEVC, VP9, AV1).
- **Present**: transitions (including Morph), entrance/emphasis/exit and motion-path animations,
  by-paragraph builds, full-screen slide show, presenter view, pen, rehearse timings, media playback.
- **Exchange files**: open and save PowerPoint `.pptx`, export PDF (slides, notes pages, handouts
  with selectable text), PNG/JPEG and outlines. Unsaved work is kept by AutoRecover.
- **Automate**: 200+ commands with undo, all scriptable from the CLI, a JSON control channel and an
  MCP server for AI agents.

## Agents, CLI and MCP

Every action in DeckCraft is a command with a stable id, so people, scripts and AI agents use the
same verbs:

```sh
deckcraft-cli commands format.          # list commands
deckcraft-cli run --sample --cmd 'slide.new={"layout":"titleOnly","title":"Hello"}' --save hello.deckcraft
deckcraft-cli mcp                       # MCP server over stdio (headless)
deckcraft-cli mcp --connect 7990        # drive the running app (deckcraft --control 7990)
```

</details>

---

## 라이선스 및 저작권 (License and Credits)

- DeckCraft는 [MIT](LICENSE-MIT) 또는 [Apache-2.0](LICENSE-APACHE) 듀얼 라이선스로 배포됩니다.
- 원본 프로젝트: [storytold/deckcraft](https://github.com/storytold/deckcraft) (Copyright (c) 2026 ArtCraft Team and the DeckCraft contributors)
- 다국어(i18n) 기반 아키텍처: [@dmatviichuk](https://github.com/dmatviichuk) ([PR #34](https://github.com/storytold/deckcraft/pull/34))
- 한국어(`ko`) 번역 카탈로그 및 한글 UI 폰트 폴백: [@JaebeenAhn](https://github.com/JaebeenAhn) ([ATTRIBUTION.md](ATTRIBUTION.md))
