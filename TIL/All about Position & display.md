 # <p align="center"> π All about Position & display(inline)

- position μμ±

  - relative
  - absolute
  - fixed

- display
  - inline
  - inline-block
  - block

<hr>
<br>

## π Position

CSS position μμ±μ λ¬Έμ μμ μμλ₯Ό λ°°μΉνλ λ°©λ²μ μ§μ ν©λλ€. <br>
top (en-US), right (en-US), bottom (en-US), left (en-US) <br>
μμ±μ΄ μμλ₯Ό λ°°μΉν  μ΅μ’ μμΉλ₯Ό κ²°μ ν©λλ€.

|Tag | μ€λͺ|
| -------- | ---------------------------------------------------------------------------------------------------------- |
| Static   | μμλ₯Ό λ¬Έμ νλ¦μ λ§μΆμ΄ λ°°μΉ                                                                             |
| relative | μ΄μ  μμ (μ£Όλ‘ λΆλͺ¨ μμ)μ `μμ°μ€λ½κ² μ°κ²°`νμ¬ μμΉλ₯Ό μ§μ                                              |
| absolute | `μνλ μμΉλ₯Ό μ§μ `ν΄ λ°°μΉ                                                                                |
| fixed    | μ§μ ν `μμΉμ κ³ μ `νμ¬ λ°°μΉ                                                                              |
| sticky   | μμΉμ λ°λΌ λμλ°©μμ΄ λ¬λΌμ§. μμμ μκ³μ (scroll λ°μ€ κΈ°μ€) μ΄μ μλ <br> κ·Έ μ΄νμλ fixedμ κ°μ΄ λμ |

<br>

```css
/* μλ¨ κ³ μ  λ€λΉκ²μ΄μ λ§λ€κΈ°*/
position: sticky;
top: 0;
```

<br>
<hr>
<br>

# π₯ Display

## `Inline`:

λνμ μΌλ‘ `<span>`μ΄λΌλ νκ·Έμ μ±μ§λ‘ content/text ν¬κΈ°λ§νΌλ§ μ μ νκ³  λμΌ λΌμΈμ λΆλ μ±μ§μλλ€.
'μ΄ κΈμ¨λ λκΊΌμ΄ ν¨κ³Όλ₯Ό μ£Όμλ€.'μ κ°μ΄ text λ΄μ νΉμ  λΆλΆμλ§ μ€νμΌμ κ°λ¨ν μ€λ λ§μ΄ μ¬μ©λμ£ .

π· inline tag

| Tag        | μ€λͺ                                                                   |
| ---------- | ---------------------------------------------------------------------- |
| `<span>`   | inlineμμλ€μ κ·Έλ£Ήννκ±°λ μμ­μ λλλ μ¬μ©νλ νκ·Έμλλ€.         |
| `<a>`      | λ§ν¬λ₯Ό ν΅ν΄ λ€λ₯Ένμ΄μ§, λ¬Έμ λ±μ μ°κ²°ν΄μ£Όλ νκ·Έμλλ€.               |
| `<img>`    | μ΄λ―Έμ§λ₯Ό μ½μνλ νκ·Έλ‘ μ§μ ν μ΄λ―Έμ§κ²½λ‘λ₯Ό ν΅ν΄ μ΄λ―Έμ§λ₯Ό λΆλ¬μ΅λλ€. |
| `<button>` | ν΄λ¦­ν  μ μλ λ²νΌμ μμ±νλ νκ·Έμλλ€.                             |
| `<br>`     | μ€λ°κΏν λ μ¬μ©ν©λλ€.                                                 |
| `<input>`  | μ¬μ©μλ‘λΆν° μλ ₯μ λ°μ λ μ¬μ©νλ©° formνκ·Έ λ΄λΆμμ λ§μ΄ μ°μλλ€.  |
| `<script>` | javascriptμ κ°μ μ€ν¬λ¦½νΈ μ½λλ₯Ό μ μν λ μ¬μ©ν©λλ€.                 |

- width/height μ μ© λΆκ°
- margin/padding-top/bottom μ μ© λΆκ°
- line-height μνλ λλ‘ μ μ© λΆκ°(spanμ μ μ© λΆκ°, κ°μΈκ³  μλ div μ μ²΄ ν¬κΈ°μλ§ μν₯)
  Width & Height are ignored. Margin & padding push elements away horizontally but not vertically.

  > κΈ°ν inline tag <br> `<abbr>, <acronym>, <b>, <bdo>, <big>, <cite>, <code>, <dfn>, <em>, <i>, <kbd> , <label>, <map>, <object>, <output>, <q>, <samp>, <select>, <small>, <strong> , <sub>, <sup>, <textarea>, <time>, <tt>, <var>`

<br>

## `block` :

- blockμ λ¬΄μ‘°κ±΄ ν μ€μ μ μ , λ€μ νκ·Έλ λ€μ μ€μ λ°°μΉ
- width, heightκ°μ ν΅ν΄ ν¬κΈ°λ₯Ό μ§μ ν  μ μμ΅λλ€.

π· Block tag

| Tag      | μ€λͺ                                          |
| -------- | --------------------------------------------- |
| `<div>`  | μμ­μ λλλ μ¬μ©νλ νκ·Έ μλλ€            |
| `<p>`    | λ¬Έλ¨ λλ λ¬Έμ₯μ λλλ μ¬μ© <br>             |
| `<form>` | μ¬μ©μκ° μλ ₯ν λ°μ΄ν°λ₯Ό μλ²λ‘ μ μ‘νκΈ° μν¨ |

> κΈ°ν block νκ·Έ <br> `<address>, <blockquote>, <canvas>, <fieldset>, <figcaption>, <figure>, <hr>, <main>, <noscript>, <pre> , <table>, <tfoot>, <video>`

Block elements break the flow tof a document. Width, Height, Width, Height, Margin & Padding are respected.

<br>

## `Inline-block` :

block μμ±κ³Ό linine μμ±μ λͺ¨λ κ°μ§κ³  μλ νν μλλ€.
block μμ±μ²λΌ widthλ₯Ό μ€μ ν  μ μμΌλ©° μμλ€μ΄ μμ°¨μ μΌλ‘ κ°λ‘λ‘ λ°°μΉλ©λλ€.

- width/height μ μ© κ°λ₯
- margin/padding-top/bottom μ μ© κ°λ₯
- line-height μ μ© κ°λ₯
  λ€λ§ κ³ λ €ν΄μΌ ν  κ²μ΄ μμ΅λλ€.
- inline-block λΌλ¦¬ κ³΅λ°±μ΄ μκΈ°κ² λλλ°, μ΄λλ μμ divμ { font-size: 0; } λ₯Ό μ μ©νλ©΄ ν΄κ²°μ΄ λ©λλ€.
- inline-block λΌλ¦¬ λμ΄κ° μλ§μμ μμ κ³΅λ°±μ΄ μκΈ°λλ°, μ΄λλ { vertical-align: ---; } κ°μΌλ‘ top λ±μ μ€μ λ§μΆ°μ£Όμλ©΄ λ©λλ€.

Behaved like an inline element except Width, Height, Marign & Padding are respected.

```css
/* inline to block or block to inline*/
h1 **{ display:iline;}**
or
span **{ display: block;}**
```

```css
/*μΈλΌμΈ μμλ κ°λ‘μΈλ‘κ° μ μ©λμ§ μμ μΈλΌμΈ λΈλ½μ μ¬μ©*/
div {
  border: 5px solid #black;
  display: inline-block;
  /*margin: 10px;*/
}
```

```css
h1 {
  display: none;
}
/* Hide elements */
```

<br>
<hr>
<br>

# π Flex-box

- νλ μ€λ°μ€(Flexbox)λ μμλ₯Ό λ¨μΌ μ°¨μ(ν λλ μ΄)μ λ°°μΉν©λλ€. <br>
- π‘ `Flexbox` :β¨MAIN AXIS (λ³ΈμΆ) & CROSS AXIS (κ΅μ°¨)β¨Β νλ λ μΆμΌλ‘ κ΅¬μ±
- βοΈ λ³ΈμΆμ κΈ°λ³Έ λ°©ν₯μ μΌμͺ½μμ μ€λ₯Έμͺ½
- Flexbox is one-dimensional layout method for laying out items in rows or columns
  - κΉ¨μ ν π‘ `grid`
    - gridλ 2μ°¨μ λ μ΄μμ μμ€ν(μμ§, μν λ λ€ κ°λ₯)μΌλ‘ λΆλ₯
    - gridλ ν­λͺ©μ λ λ°©ν₯μΌλ‘ λ μ΄μμ ν  μμλ λ°λ©΄Β flexλ ν λ°©ν₯λ§ κ°λ₯

## `Flex direction`

μ»¨νμ΄λ μμμ λ³ΈμΆ λ°©ν₯μ κ²°μ νλ μμ±

```css
flex-direction: row; /* [λν΄νΈ] μ’-μ° */
flex-direction: row-reverse; /*μ°-μ’*/
flex-direction: column; /*μ-ν*/
flex-direction: column-reverse; /*ν-μ*/
```

### Justify-content

μ£ΌμΆμ κΈ°μ€μΌλ‘ μμμ μ½νμΈ λ₯Ό μ΄λ»κ² λ°°μΉ ν μ§ κ²°μ νλ μμ± | λ§€λ² μ’ μ λ ¬μ΄ μλ μ£ΌμΆμλ°λΌ λ€λ¦

```css
justify-content: flex-start;
justify-content: flex-end;
justify-content: center;
justify-content: space-between; /*μ»¨νμ΄λ λ μ¬λ°±μ μμ κ³  μμ μ¬μ΄μ μ¬λ°±μ λ§λ¬*/
justify-content: space-around; /*μμμ λλ μ κ°μ μ¬λ°±μ λΆμ¬ | μ€μ°¨κ° λ°μν¨*/
justify-content: space-evenly; /*μμ, μ»¨νμ΄λ μ¬μ΄μ κ· λ±ν μ¬λ°± λΆμ¬*/
```

### WRAP

π‘ **flex-wrap: wrap;**
μ£ΌμΆμ΄ μνμΌ λ μλ‘μ΄ νμ λ§λ€μ΄ μμλ₯Ό μ λ ¬νκ³  μ£ΌμΆμ΄ μμ§μΌ λλ μλ‘μ΄ μ΄μ λ§λ€μ΄ μμλ₯Ό μ λ ¬νλ μμ±.

```css
flex-wrap: wrap-reverse;
flex-wrap: nowrap;
```

### `ALIGN ITEMS` | κ΅μ°¨μΆμ λ°λΌ μμ΄νμ λ°°μ΄

**flex μ»¨νμ΄λ** μ μ§μ νλ μμ±μ΄λ©°, κ΅μ°¨μΆμ λ°λΌΒ **flex ν­λͺ©**μ΄μ μ λ ¬νλ λ°©μμ μ§μ ν©λλ€.

```css
align-tiems: flex-start;
align-tiems: flex-end;
align-items: baseline; /*νμ€νΈλΌμΈμ μ λ ¬*/
```

### `ALIGN CONTENT`

νμ΄λ μ΄μ΄ μ¬λ¬ κ°μΌ λ κ΅μ°¨μΆμ μ€μ¬μΌλ‘ μ λ ¬νλ align-content

μ£ΌμΆμ λ°λΌΒ **flex ν­λͺ©** νμ μ λ ¬νλ λ°©μμ μ§μ ν©λλ€.

```css
align-content: spcae-between;
align-content: flex-start;
align-content: center; /*λ© λ¦¬λ²μ€λ νλ μ€κ° μ μ© λμ΄μμ΄μΌ ν¨*/
align-self: flex-end; /*ν μμ΄νλ§ λμ μ λ§Ίμ*/
```

### Flex sizing properties

```css
flex-grow: 1;
flex-shrink: 2; /*0μ λ£μΌλ©΄ μ€μ§ μλλ€λ₯!*/
```

## `Flex basis`

Defines the initial size of an element before additional space is distributed. | ν­λͺ©μ ν¬κΈ°λ₯Ό κ²°μ 

## `Flex grow`

Controls the amount of available space an element should take up. Accepts a unit- less number value | μμμ **κ³΅κ°μ΄ μμ λ**, μΌλ§λ μ°¨μ§ ν μ§ κ²°μ  Flex basisλ³΄λ€ ν° κ°μΌλ‘ λμ΄λ¨ (λΉμ¨κ°)

## `Flex shrink`

If items are larger than the container, they shrink according to flex-shrink. | μμμ **κ³΅κ°μ΄ μμ λ**, μμλ€μ΄ μ€μ΄λλ λΉμ¨μ ν΅μ , κ°μ κ°μ§ μμκ° λ¨Όμ  μ€μ΄λ¬ (λΉμ¨κ°)

### Flex μκΈ°

```css
/* one value, width/height: flex-basis*/
flex:10em;
flex: 30%;
flex: min-content;

/*Two calues: flex-grow | flex-shrink */
flex: 1 30px

/*Three values: flex-grow | flex-shrink | flex-basis */
flex:2 2 10%
```

<hr>
μΆμ²:

- https://poiemaweb.com/css3-flexbox
- https://m.blog.naver.com/PostView.naver?isHttpsRedirect=true&blogId=leesd88&logNo=220682157303
- https://engkimbs.tistory.com/m/922
- https://calmdawnstudio.tistory.com/m/51
- https://developer.mozilla.org/ko/docs/Glossary/Flexbox
