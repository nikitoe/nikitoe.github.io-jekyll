---
layout: post
title: Study-Etc-Css-Basic
image: /assets/img/blog/study/background-css.png
sitemap: false
hide_last_modified: false
categories:
  - study
  - etcs
---

# [CSS] 기초 이론 정리

---

* toc
{:toc .large-only}
## 1. Selectors

```css
selector {
	property: value;
}
```

- Universal
    - **`*`** : 해당 전체 코드에대해 색깔을 초록색으로 지정한다.
    
    ```css
    * {
    	color : green;
    }
    ```
    
- Type
    - **`Tag`**
    
    ```css
    li {
    	color: green;
    }
    ```
    
- ID
    - **`#id`** : #마크를 이용하여 지정할 수 있다.
    
    ```css
    #special {
    	color: pink;
    }
    ```
    
- Class
    - **`.class`** : .마크를 이용하여 지정할 수 있다.
    
    ```css
    .red {
    	width: 100px;
    	height: 100px;
    	backgrounmd:yellow;
    }
    ```
    
- State
    - **`:`**  :tag옆에 :hover를 추가 함으로써, 마우스를 올릴 때의 이벤트를 지정할 수있다.
    
    ```css
    button:hover {
    	color: red;
    	background: beige;
    }
    ```
    
- Attribute
    - **`[ ]` :**  속성값이 있는 경우만 따로 지정할 수 있다.
    
    ```css
    a[href] {
    	color: purple;
    }
    
    /*링크중에 naver.com으로 되어있는 것만 지정*/
    a[href="naver.com"] {
    	color: purple;
    }
    
    /*naver로 시작되어있는 것만 지정*/
    a[href^="naver"] {
    	color: purple;
    }
    
    /*.com으로 끝나있는 것만 지정*/
    a[href$=".com"] {
    	color: purple;
    }
    
    ```
    

### 참고사이트

- [MDN CSS Selectors]([https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Selectors](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Selectors))
- [MDN CSS Reference]([https://developer.mozilla.org/en-US/docs/Web/CSS/Reference](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference))
- [MDN CSS Properties Reference](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Properties_Reference)
- [Selector game]([https://flukeout.github.io/](https://flukeout.github.io/))

<br>

## 2. 헷갈리는 컨셉

### Position

- **`static`**
- **`relative`** : 원래 있던 item에서 옮겨진다
- **`absolute`** : 가까이 담겨있는 상자안에서 옮겨진다
- **`fixed`** : 상자에서 완전히 벗어난 페이지상에서 옮겨진다
- **`sticky`** : 원래 있어야 하는 자리에 그대로있고, 크르롤이 되어도 계속 그자리에 그대로 있다.

### Display

- **`inline`** : 물건
- **`inline-block`** : 한줄에 여러개가 직렬될 수 있는 특별한 상자
- **`block`** : 한줄당 하나씩 들어가는 상자

### 참고사이트

- [https://caniuse.com/](https://caniuse.com/): 어떤 속성값이 어떤 브라우저에서 많이 사용되는지 알 수 있다.
- [MDN CSS Position]([https://developer.mozilla.org/en-US/docs/Web/CSS/position](https://developer.mozilla.org/en-US/docs/Web/CSS/position))
- [MDN CSS Display]([https://developer.mozilla.org/en-US/docs/Web/CSS/display](https://developer.mozilla.org/en-US/docs/Web/CSS/display))

<br>

## 3. Flex box

### Tip

- 편리하게 태그 만들기
    - `**div.container2>div.items.items${$}*10**`
- **`100vh`** : item에 상관없이 100%다 적용시킬때


### Container

- **`display`**
    - **`flex`**
- **`flex-direction`**: 방향 지정 (수직이 중심 축인지, 수평이 중심 축인지)
    - `**row**` : (기본값)왼쪽에서 오른쪽으로(수평축은 열)
    - **`row-reverse`** : 오른쪽에서 왼쪽으로 역순(수평축은 열)
    - **`column`** : 위쪽에서 아래쪽으로(수직춘은 행)
    - **`column-reverse`** : 아래쪽에서 위쪽으로(수직축은 행)
- **`flex-wrap`**: 한 줄에 가득차면 다음 줄로 넘어가게 할 것인지, 아닌지 결정
    - **`nowrap`** :  (기본값) item들이 많아져도 한 줄에 빼곡하게 붙어 있음
    - **`wrap`** : item 한 줄에 꽉차게 되면 자동적으로 다음 라인으로 넘어 감
    - **`wrap-reverse`** : 오른쪽에서 왼쪽으로 item들이 한 줄에 꽉차면 다음 라인으로 넘어 감
- **`flex-flow`**: flex-direction과 flex-wrap을 합한 값으로 한번에 묶어서 작성 가능 (ex. flex-flow : column nowrap;)
- **`justify-content`** : 중심축에서 item들을 어떻게 배치할 것인지 결정
    - **`flex-start`** : (기본값)왼쪽에서 오른쪽으로 배치
    - **`flex-end`** : 순서는 유지하되, 오른쪽으로 붙여서 배치(수직축일땐 아래쪽으로 붙여서 배치 )
    - **`flex-center`** : center 기준으로 배치
    - **`space-around`** : 박스를 둘러싸게 space를 넣어 줌
    - **`space-evenly`** : 똑같은 간격을 넣어 줌
    - **`space-between`** : 중간에만 간격을 넣어 줌
- **`align-items`** : 반대축에서 item들을 어떻게 배치할 것인지 결정
    - **`center`** : 가운데에 배치
    - **`baseline`** : text를 기준으로 배치
- **`align-content`** : 반대축에서 item들을 어떻게 배치할 것인지 결정
    - **`flex-start`**: 여러 줄들을 컨테이너의 꼭대기에 정렬
    - **`flex-end`**: 여러 줄들을 컨테이너의 바닥에 정렬
    - **`center`**: 여러 줄들을 세로선 상의 가운데에 정렬
    - **`space-between`**: 여러 줄들 사이에 동일한 간격을 둠
    - **`space-around`** : 여러 줄들 주위에 동일한 간격을 둠
    - **`stretch`** : 여러 줄들을 컨테이너에 맞도록 늘림


### Item

- **`order`** : item의 순서를 지정
- **`flex-grow`** : container의 사이즈가 변경되었을때, item들이 얼마나 어떻게 줄어들고 늘어나야 되는지 정의한다(늘어날 때)
- **`flex-shrink`** : container의 사이즈가 변경되었을때, item들이 얼마나 어떻게 줄어들고 늘어나야 되는지 정의한다(줄어들 때)
- **`flex-basis`** :  item들이 공간을 얼마나 차지해야되는지 세부적으로 명시할 수 있게 도와 줌
    - auto : flex-grow와 flex-shrink에 맞게 자동으로
    - %으로 각 item에 지정 가능(커질때나 작아직때에도 container의 width에 따라 자동적으로 적용 가능)
- **`align-self`** : item별로 item들을 정렬 (지정한 item 하나만 정렬가능)


### 참고사이트

- [Color tools]([https://material.io/resources/color/#!/?view.left=0&view.right=0](https://material.io/resources/color/#!/?view.left=0&view.right=0))
- [CSS Tricks for Flexbox]([https://css-tricks.com/snippets/css/a-guide-to-flexbox/](https://css-tricks.com/snippets/css/a-guide-to-flexbox/))
- [MDN Flexbox])[https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Flexible_Box_Layout/Basic_Concepts_of_Flexbox](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Flexible_Box_Layout/Basic_Concepts_of_Flexbox))
- Flex box game
    - [한국어 버전]([https://flexboxfroggy.com/#ko](https://flexboxfroggy.com/#ko))
    - [영어 버전]([https://flexboxfroggy.com/#](https://flexboxfroggy.com/#ko)am)
    - [일본어 버전]([https://flexboxfroggy.com/#](https://flexboxfroggy.com/#ko)ja)
- [CSS games]([https://codepip.com/games/](https://codepip.com/games/))