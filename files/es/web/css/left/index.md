---
title: left
slug: Web/CSS/left
translation_of: Web/CSS/left
---
{{CSSRef}}

La propiedad `left` especifica parte de la posición de un elemento (posicionado - es decir, con una posición determinada por código).

Para los elementos con una posición absoluta (aquellos que tienen la propiedad {{ Cssxref("position") }}`: absolute` ó `position: fixed`), la propiedad left determina la distancia entre el margen izquierdo del elemento y el borde izquierdo de su bloque contenedor.

{{EmbedInteractiveExample("pages/css/left.html")}}

{{cssinfo}}

## Sintaxis

```
left: <length> | <percentage> | auto | inherit ;
```

### Valores

- {{cssxref("&lt;length&gt;")}}
  - : Una longitud, un valor negativo, cero, un valor positivo.
- {{cssxref("&lt;percentage&gt;")}}
  - : Un porcentaje del ancho del bloque contenedor.

## Ejemplos

### CSS

```css
#wrap {
  width: 700px;
  margin: 0 auto;
  background: #5C5C5C;
}

pre {
  white-space: pre;
  white-space: pre-wrap;
  white-space: pre-line;
  word-wrap: break-word;
}

#example_1 {
  width: 200px;
  height: 200px;
  position: absolute;
  left: 20px;
  top: 20px;
  background-color: #D8F5FF;
}

#example_2 {
  width: 200px;
  height: 200px;
  position: relative;
  top: 0;
  right: 0;
  background-color: #C1FFDB;

}
#example_3 {
  width: 600px;
  height: 400px;
  position: relative;
  top: 20px;
  left: 20px;
  background-color: #FFD7C2;
}

#example_4 {
  width:200px;
  height:200px;
  position:absolute;
  bottom:10px;
  right:20px;
  background-color:#FFC7E4;
}
```

### HTML

```html
<div id="wrap">
  <div id="example_1">
    <pre>
      position: absolute;
      left: 20px;
      top: 20px;
    </pre>
    <p>The only containing element for this div is the main window, so it positions itself in relation to it.</p>
  </div>

  <div id="example_2">
    <pre>
      position: relative;
      top: 0;
      right: 0;
    </pre>
    <p>Relative position in relation to its siblings.</p>
  </div>

  <div id="example_3">
    <pre>
      float: right;
      position: relative;
      top: 20px;
      left: 20px;
    </pre>
    <p>Relative to its sibling div above, but removed from flow of content.</p>

    <div id="example_4">
      <pre>
        position: absolute;
        bottom: 10px;
        right: 20px;
      </pre>
      <p>Absolute position inside of a parent with relative position</p>
    </div>
  </div>
</div>
```

{{EmbedLiveSample('Ejemplos',1200,650)}}

## Especificaciones

- [CSS 2.1](http://www.w3.org/TR/CSS21/visuren.html#propdef-left)
- [CSS 3](http://www.w3.org/Style/CSS/current-work#positioning)

## Compatibilidad entre navegadores

{{Compat("css.properties.left")}}

## Ver también

- {{ Cssxref("position") }}, {{ Cssxref("top") }}, {{ Cssxref("right") }}, {{ Cssxref("bottom") }}
