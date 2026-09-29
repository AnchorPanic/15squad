# AnchorPanic 1.5주년 · 15달러 스쿼드 챌린지

정적 페이지 하나로 동작합니다. 서버도 빌드도 필요 없습니다.

---

## 1. 조직 생성

개인 계정이 아니라 **Organization**으로 만드시는 것을 권합니다.
개인 계정에 두면 담당자가 바뀔 때 소유권 이전이 번거롭고, 퇴사 시 접근이 막힙니다.

```
github.com → 우측 상단 + → New organization → Free 선택
Organization name : AnchorPanic
```

이미 선점된 이름이면 `AnchorPanicKR`, `AnchorPanic-KR` 등으로 대체합니다.

## 2. 저장소 생성

저장소 이름에 따라 최종 주소가 달라집니다.

| 저장소 이름 | 주소 |
|---|---|
| `AnchorPanic.github.io` | `https://anchorpanic.github.io/` |
| `squad` | `https://anchorpanic.github.io/squad/` |

이벤트 페이지를 앞으로 여러 개 올릴 계획이면 두 번째가 낫습니다.
이번 하나로 끝이면 첫 번째가 주소가 짧습니다.

```
공개 범위 : Public
```

**Private으로 두면 GitHub Pages가 유료 플랜에서만 동작합니다.**
소스가 공개되어도 문제 없는 내용이므로 Public으로 둡니다.

## 3. 파일 업로드

이 폴더의 내용을 그대로 올립니다.

```
index.html          페이지 본체 (이 이름이어야 합니다)
.nojekyll           Jekyll 빌드 비활성화
assets/icons/       캐릭터 아이콘 68개
```

웹에서 올릴 경우 `Add file → Upload files`에 폴더째 끌어다 놓으면 됩니다.

## 4. Pages 활성화

```
저장소 → Settings → Pages
Source : Deploy from a branch
Branch : main / (root)
Save
```

1~2분 후 주소가 발급됩니다.

## 5. 커스텀 도메인 (선택)

앵커패닉이나 넵튠 도메인의 서브도메인을 쓸 수 있으면 그쪽이 낫습니다.
공식 이벤트 페이지 주소가 `github.io`인 것보다 신뢰도가 높습니다.

```
DNS에 CNAME 레코드 추가 → anchorpanic.github.io
저장소 Settings → Pages → Custom domain 에 입력
Enforce HTTPS 체크
```

---

## 아이콘 준비

`assets/icons/` 폴더에 `캐릭터명.png` 형식으로 넣습니다.
필요한 68개 목록은 같은 폴더의 `FILELIST.txt`에 있습니다.

- 정사각형 권장, 128x128 정도면 충분
- 파일명은 목록과 정확히 일치해야 합니다
- `여명의 기사·루미스.png` 처럼 가운뎃점이 들어간 이름도 그대로 씁니다
- 아이콘이 없으면 이름 텍스트로 대체되며 기능은 정상 동작합니다

한글 파일명이 문제가 되면 영문 코드로 바꾸고 `index.html`의 `iconPath()`
함수에 매핑 테이블을 추가하면 됩니다.

---

## 커뮤니티 운영

카페와 아카라이브는 `<script>`를 허용하지 않으므로 HTML을 직접 붙여넣을 수 없습니다.
링크만 걸고, 공지 본문에는 가격표 이미지를 함께 올립니다.

링크가 막히거나 인앱 브라우저에서 이미지 저장이 안 되는 경우를 대비해
아래 형식의 수동 응모도 함께 받는 것을 권합니다.

```
UID : 22000200035
스쿼드 : 홍엽 $5 / 유카리 $4 / 옌 $3 / 케미아 $2 / 트리거 $1
합계 : 15 / 15
```

---

## 가격표 수정

`index.html` 안의 `DATA` 배열만 고치면 됩니다.

```javascript
const DATA = [
  { price:5, list:["설희","어비스 알리시아", ...] },
  ...
];
```

`BUDGET`과 `SIZE` 상수로 예산과 편성 인원도 조정할 수 있습니다.
