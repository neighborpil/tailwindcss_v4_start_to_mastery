# tailwindcss_v4_start_to_mastery

### Tailwind v4 - OKLCH Wheel
![IMG_0024.PNG](images/oklch.PNG)


## Lines
- border: 요소의 실제 테두리를 그려 레이아웃에 영향을 준다.
- ring: 요소 외곽 강조용으로, 레이아웃에는 영향이 없고 겹치는 순서(z-index)에도 유연하다.
   + box-shadow와 비슷한 개념으로, 요소의 외곽에 그림자를 추가하는 것과 유사하다.
- outline: border와 달리 요소 외곽에 그려지며, 레이아웃이나 요소 크기에 영향을 주지 않는다. 브라우저 기본 포커스 스타일로 자주 사용.
- divide: 부모 요소에 적용하면, 자식 사이에만 얇은 선이 들어간다. flex/grid 레이아웃에서 아이템 간 구분선으로 유용.
- size는 px단위이다: outline-2(2px), ring-4(4px), border-8(8px)

### ring, outline 차이
- ring
   + CSS box-shadow로 구현
   + 그림자 형태로 요소 경계 바로 바깥에 그려짐
   + ring-offset을 이용해 경계선과 그림자 사이에 여백을 줄 수 있음
   + border-radius를 그대로 따라감
   + offset에 색상을 줄 수 있다: ring-offset-pink-200
   + inset으로 라인을 안으로 줄 수 있다: ring-inset
- outline
   + CSS outline 속성으로 구현
   + 요소 경계 밖을 감싸는 선(“아웃라인”)
   + outline-offset으로만 오프셋 조절 가능
   + border-radius를 무시하고 항상 요소의 바운딩 박스를 감싸며, 둥글게 되지 않음
   + 선의 종류를 바꿀 수 있다: outline-dashed


### color inherits (v4)
- v4에서는 border, outline, placeholder, ring, divide 색상 속성이 상위 요소의 색상을 상속받는다.

### rounded
- border, ring, outline, divide에 적용 가능
- none, sm, md, lg, xl, 2xl, 3xl, full
- s, e, t, r, l, b, ss, se, ee, es, tl, tr, br, bl
- v4에서는 border-radius 속성으로 구현

### Utility class changes
#### opacity
- [bg, text, border, divide]-opacity-* 등이 없어졌다
- 대신 바로 표시하면 된다: bg-red-500/50, border-pin-300/20
- 5단위로 입력: 5, 10, 15, 20, 25, 30, 35, 40, 45, 50, 55, 60, 65, 70, 75, 80, 85, 90, 95

#### rounded, shadow, drop-shadow, blur, backdrop-blur
1. v3
- rounded-sm(2),
- rounded(4),
- rounded-md(6),
- rounded-lg(8),
- rounded-xl(12),
- rounded-2xl(16),
- rounded-3xl(24),

2. v4
- 
- **rounded-xs(0.125rem, 2px)**
- **rounded(0.25rem, 4px)**
- **rounded-sm(0.25rem, 4px)**,
- rounded-md(0.375rem, 6px),
- rounded-lg(0.5rem, 8px),
- rounded-xl(0.75rem, 12px),
- rounded-2xl(1rem, 16px),
- rounded-3xl(1.5rem, 24px),

#### outline
- v3: outline-none(transparent로 처리) v4에서는 **outline-hidden**로 처리된다
- v4: **outline-none** v4에서는 진짜 없어짐(outline-style: none)

#### ring
- v3의 ring 은 v4의 ring-3와 같아

## 방향(Logical Properties)
- ltr: left to right
- rtl: right to left
```html
<div dir="ltr">
  <div class="text-2xl p-4 m-4">Lorem ipsum dolor sit amet.</div>
</div>

<div dir="rtl">
  <div class="text-2xl p-4 m-4">Lorem ipsum dolor sit amet.</div>
</div>
```

## Width / Height
- [min|max]-w|h|size-[px,0.5-3.5, 4-12, 12-20, 20-64, 94-96, /2, /3, /4, /5, /6, /12, screen, min-w]
- custom width: w-[100px]
- w-2/3: dynamic width
- size: width와 height를 동시에 설정
- 1의 크기는 0.25rem이다: w-1(0.25rem), h-2(0.5rem), size-4(1rem)
- h-screen: 100vh

### h-screen, min-h-screen 차이
- h-screen: 100vh, 콘텐츠가 적든 많든 항상 뷰포트 높이와 똑같이 고정
- min-h-screen: 100vh보다 작을 때만 100vh로 설정, 콘텐츠가 적으면 뷰포트 높이만큼, 많으면 그 이상 확장
- 사용시점
   + h-screen: 주로 1페이지짜리 “히어로 섹션”을 뷰포트 전체로 꽉 채울 때
   + min-h-screen: 페이지 전체 레이아웃에서 배경을 화면만큼 채우되, 콘텐츠가 많으면 스크롤되면서 늘어나길 원할 때

### breakpoints
- sm: 640px (@media (min-width: 640px))
- md: 768px (@media (min-width: 768px))
- lg: 1024px (@media (min-width: 1024px))
- xl: 1280px (@media (min-width: 1280px))
- 2xl: 1536px (@media (min-width: 1536px))

### Interactivity
- hover: 마우스 오버 시
- focus: 요소에 포커스가 있을 때
- active: 요소가 클릭되었을 때
- visited: 링크가 클릭된 후
- disabled: 요소가 비활성화 되었을 때
- group: 부모 요소에 적용하여 자식 요소에 스타일을 적용할 때 사용
```html
<div class="group border-2 border-red-500 p-4 m-4 rounded-md bg-red-100 hover:bg-red-200">
  <h1 class="group-hover:text-green-500">Heading</h1>
  <p class="group-hover:text-red-800">Lorem ipsum dolor sit amet, consectetur adipisicing elit. Cumque, libero?</p>
</div>
```

### shadow
- shadow-[sm,md,lg,xl,2xl,inner,none]
-
  | 클래스          | 설명                 | 기본값 (box-shadow)                                                                                         |
  | --------------- | -------------------- | ---------------------------------------------------------------------------------------------------------- |
  | `shadow-sm`     | 작은 그림자          | `0 1px 2px 0 rgba(0, 0, 0, 0.05)`                                                                            |
  | `shadow`        | 기본 그림자 (DEFAULT) | `0 1px 3px 0 rgba(0, 0, 0, 0.1), 0 1px 2px 0 rgba(0, 0, 0, 0.06)`                                           |
  | `shadow-md`     | 중간 크기 그림자     | `0 4px 6px -1px rgba(0, 0, 0, 0.1), 0 2px 4px -1px rgba(0, 0, 0, 0.06)`                                      |
  | `shadow-lg`     | 큰 그림자            | `0 10px 15px -3px rgba(0, 0, 0, 0.1), 0 4px 6px -2px rgba(0, 0, 0, 0.05)`                                     |
  | `shadow-xl`     | 엑스트라 라지 그림자 | `0 20px 25px -5px rgba(0, 0, 0, 0.1), 0 10px 10px -5px rgba(0, 0, 0, 0.04)`                                  |
  | `shadow-2xl`    | 매우 큰 그림자       | `0 25px 50px -12px rgba(0, 0, 0, 0.25)`                                                                       |
  | `shadow-inner`  | 내부 그림자 (inset)  | `inset 0 2px 4px 0 rgba(0, 0, 0, 0.06)`                                                                        |
  | `shadow-none`   | 그림자 제거          | `none`                                                                                                       |

- shadow-[color]-[size/opacity] : 그림자 색상 변경

