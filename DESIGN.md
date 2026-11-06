---
name: "내 영화 티어리스트"
description: "영화 제목과 개인의 평가를 중심에 둔 영화 비평지형 보드"
colors:
  paper: "#f5f2eb"
  ink: "#292b28"
  muted: "#62635b"
  accent: "#974735"
  line: "#d3d0c5"
  white: "#fffefa"
  inverse: "white"
  hover: "#eae6dc"
  drop: "#e6e2d6"
typography:
  display:
    fontFamily: 'Georgia, "Batang", serif'
    fontSize: "44px"
    fontWeight: 600
    lineHeight: 1.18
    letterSpacing: "-.03em"
  headline:
    fontFamily: 'system-ui, -apple-system, "맑은 고딕", sans-serif'
    fontSize: "21px"
    fontWeight: 700
    letterSpacing: "-.02em"
  body:
    fontFamily: 'system-ui, -apple-system, "맑은 고딕", sans-serif'
    lineHeight: 1.6
  label:
    fontFamily: 'system-ui, -apple-system, "맑은 고딕", sans-serif'
    fontSize: "14px"
    fontWeight: 650
  card:
    fontFamily: 'system-ui, -apple-system, "맑은 고딕", sans-serif'
    fontSize: "14px"
    fontWeight: 550
  tier:
    fontFamily: "Georgia, serif"
    fontSize: "34px"
    lineHeight: 1
rounded:
  control: "7px"
spacing:
  tight: "8px"
  control-gap: "10px"
  small: "12px"
  medium: "16px"
  section: "24px"
components:
  button-default:
    backgroundColor: "{colors.white}"
    textColor: "{colors.ink}"
    rounded: "{rounded.control}"
    padding: "9px 15px"
  button-default-hover:
    backgroundColor: "{colors.hover}"
  button-primary:
    backgroundColor: "{colors.ink}"
    textColor: "{colors.inverse}"
    rounded: "{rounded.control}"
    padding: "9px 15px"
  button-reset:
    backgroundColor: "transparent"
    textColor: "{colors.ink}"
    rounded: "{rounded.control}"
    padding: "9px 15px"
  input-title:
    backgroundColor: "{colors.white}"
    textColor: "{colors.ink}"
    rounded: "{rounded.control}"
    padding: "11px 13px"
  card-movie:
    backgroundColor: "{colors.white}"
    textColor: "{colors.ink}"
    typography: "{typography.card}"
    rounded: "{rounded.control}"
    padding: "12px 16px"
  card-movie-selected:
    backgroundColor: "{colors.ink}"
    textColor: "{colors.inverse}"
---

# Design System: 내 영화 티어리스트

## Overview

**Creative North Star: "영화 비평지"**

따뜻한 종이 바탕에 짙은 잉크와 적갈색 강조를 얹는다. 포스터 대신 영화 제목과 등급이 화면의 중심이며, 선택한 제목은 잉크색 반전으로 구분한다. 방향은 사용자가 질문 없이 결정을 위임한 범위에서 정했으며 사용자 인터뷰 결과로 간주하지 않는다.

기준 구현은 `영화_A_초안.html`, 결정 근거는 `evidence/디자인_결정.md`다. 이 문서는 코드 추출 결과다. 브라우저 실행이 차단되어 실제 렌더링, 글꼴 대체, 390px 화면의 넘침과 키보드 사용성은 시각 검증하지 못했다.

**Key Characteristics:**
- 제목 중심의 담백한 영화 보드
- 종이·잉크 대비와 절제된 적갈색 강조
- 구분선으로 나눈 등급 행과 반전되는 선택 카드

## Colors

### Primary
- **적갈색 강조** (`accent`): 제목의 두 번째 구절, S 등급, 상태 안내, 포커스 테두리와 텍스트 선택에 사용한다.

### Neutral
- **따뜻한 종이** (`paper`): 전체 배경.
- **짙은 잉크** (`ink`): 본문, 주요 구분선, 추가 버튼과 선택 카드 배경.
- **옅은 잉크** (`muted`): 사용 안내, 개수, 빈 등급과 저장 상태.
- **종이 경계** (`line`): 버튼·입력 테두리와 행 구분선.
- **밝은 종이** (`white`): 기본 버튼·입력·카드 배경. 반전 글자는 별도 `inverse`를 사용한다.
- **눌러볼 수 있는 면** (`hover`): 기본 버튼과 미선택 카드의 호버 배경.
- **놓을 수 있는 면** (`drop`): 드래그가 진입한 등급 행의 배경.

## Typography

큰 제목은 명조 계열, 본문과 조작부는 시스템 고딕 계열을 사용한다. 전면의 토큰이 기준이며 실제 글꼴은 운영체제에 따라 달라진다.

- **Display:** 페이지 제목. 화면 폭 950px 이하에서 36px, 480px 이하에서 32px로 줄어든다.
- **Headline:** 보드 제목. 화면 폭 480px 이하에서 19px로 줄어든다.
- **Body:** 안내와 조작부의 기본 서체·행간. 기본 글자 크기는 CSS에서 별도로 지정하지 않는다.
- **Label / Card:** 입력 라벨과 영화 제목. 굵기 차이로 역할을 나눈다.
- **Tier:** S/A/B/C 등급 문자. 미분류는 시스템 서체의 17px·700으로 구별한다.
- 보조 문구는 12–15px 범위이며, 개수 표시는 고정폭 숫자를 사용한다.

## Layout

넓은 화면의 바깥 컨테이너는 최대 1400px, 여백은 세로 56px·가로 40px다. 좌측 설명 250px와 우측 가변 보드 사이를 64px 띄운다. 좌측 설명은 상단 40px에서 고정된다.

950px 이하에서는 한 열, 여백 32px·24px, 영역 간격 32px로 전환하고 설명의 고정을 해제한다. 480px 이하에서는 여백 28px·16px, 영역 간격 28px를 사용한다.

등급 행은 등급명과 카드 영역의 두 열이다. 등급명 열은 기본 88px, 작은 화면에서는 62px다. 카드는 8px 간격으로 줄바꿈한다. 긴 영화 제목과 선택 안내는 단어 중간 줄바꿈을 허용한다. 미분류 영역은 위쪽 간격과 진한 구분선으로 분리한다.

## Elevation & Depth

그림자를 사용하지 않는다. 종이색 면, 얇은 구분선, 선택 카드의 명암 반전으로 계층을 만든다. 드래그 대상은 적갈색 점선 외곽선으로 표시한다. 전환 애니메이션은 정의되어 있지 않다.

## Shapes

버튼·입력·영화 카드는 같은 완만한 모서리를 공유한다. 보드와 등급 행은 둥근 상자가 아니라 직선 구분선으로 나눈다. 포커스는 적갈색 3px 외곽선과 3px 간격으로 표현한다.

## Components

- **기본 버튼:** 밝은 종이 바탕과 얇은 경계. 최소 높이 44px, 이동 버튼 최소 너비 48px. 호버 시 배경과 경계를 진하게 한다. 비활성은 불투명도 0.5와 금지 커서로 표시한다.
- **추가 버튼:** 잉크색 반전. 폼 아래쪽에 정렬하며 현재 CSS에서는 호버해도 배경색이 유지된다.
- **처음으로 버튼:** 투명 배경의 보조 조작. 호버·포커스는 기본 버튼 규칙을 따른다.
- **제목 입력:** 밝은 종이 바탕, 옅은 잉크의 안내 문구, 적갈색 커서. 입력 오류는 별도 붉은 필드가 아니라 상태 문구로 알린다.
- **영화 카드:** 버튼 형태의 제목. 선택 상태는 `aria-pressed`와 잉크색 반전으로 표시한다. 작은 화면에서는 안쪽 여백을 10px·12px로 줄인다.
- **등급 행:** 빈 상태 안내를 유지한다. 드래그 진입 시 면 색과 점선 외곽선을 바꾼다. 클릭 선택 후 등급 버튼으로 옮기는 경로도 제공한다.

## Do's and Don'ts

### Do:
- **Do** 영화 제목을 읽을 수 있게 줄바꿈과 카드의 최대 너비 제한을 유지한다.
- **Do** 선택 상태와 키보드 포커스를 서로 다른 표시로 유지한다.
- **Do** 좁은 화면에서 한 열 배치와 줄바꿈되는 이동 버튼을 유지한다.

### Don't:
- **Don't** 현재의 평면적 계층을 설명하면서 그림자나 애니메이션이 구현되어 있다고 기록한다.
- **Don't** 이 추출 문서를 실제 브라우저 검증의 증거로 사용한다.
