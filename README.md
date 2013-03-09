# Principios para escribir HTML consistente e idiomático

El siguiente documento esquematiza una guía de estilo razonable para el desarrollo con HTML.
Estas directrices aconsejan el uso de patrones comunes y sensibles.
Pueden ser adaptados en función de tus necesidades para crear tu propio libro de estilo

Esto es un documento vivo por lo que nuevas ideas son bienvenidas. Se tan amable de contribuir.

## Tabla de contenidos

1. [Principios Generales](#principios-generales)
2. [Espacios](#espacios)
3. [Formato](#formato)
4. [Orden de los atributos](#orden-atributos)
5. [Nombres](#nombres)
6. [Ejemplos Practicos](#ejemplos)

[Licensia](#licensia)


<a name="principios-generales"></a>
## 1. Principios Generales

* Todo el código debe dar la impresión de estar escrito por la misma persona, no importa
  cuanta gente haya colaborado.
* Haga cumplir estrictamente los estilos acordados.
* En caso de dudas a la hora de decidir sobre un estilo, use patrones ya existentes.


<a name="espacios"></a>
## 2. Espacios

Sólo debe existir un estilo en todo su código fuente. Sea siempre consistente 
en el uso de los espacios. Use los espacios para mejorar la legibilidad.

* Nunca mezcle espacios y tabuladores para la indentación.
* Elija entre indentado con espacios o tabuladores reales. Sea fiel a su elección 
  sin excepciones. (Preferencia: espacios)
* Si utiliza espacios, elija el número de caracteres para cada nivel de indentación
  (Preferencia: 4 espacios)

Tip: configure your editor to "show invisibles". This will allow you to
eliminate end of line whitespace, eliminate unintended blank line whitespace,
and avoid polluting commits.


<a name="format"></a>
## 3. Format

* Always use lowercase tag and attribute names.
* Write one discrete element per line.
* Use one additional level of indentation for each nested element.
* Use valueless boolean attributes (e.g. `checked` rather than
  `checked="checked"`).
* Always use double quotes to quote attribute values.
* Omit the `type` attributes from `link` stylesheet, `style` and `script`
  elements.
* Always include closing tags.
* Don't include a trailing slash in self-closing elements.

(Keep line-length to a sensible maximum, e.g., 80 columns.)

Example:

```html
<div class="tweet">
    <a href="path/to/somewhere">
        <img src="path/to/image.png" alt="">
    </a>
    <p>[tweet text]</p>
    <button disabled>Reply</button>
</div>
```

### Exceptions and slight deviations

Elements with multiple attributes can have attributes arranged across multiple
lines in an effort to improve readability and produce more useful diffs.

Example:

```html
<a class="[value]"
 data-action="[value]"
 data-id="[value]"
 href="[url]">
    <span>[text]</span>
</a>
```


<a name="attribute-order"></a>
## 4. Attribute order

HTML attributes should be listed in an order that reflects the fact that class
names are the primary interface through which CSS and JavaScript select
elements.

1. `class`
2. `id`
3. `data-*`
4. Everything else

Example:

````html
<a class="[value]" id="[value]" data-name="[value]" href="[url]">[text]</a>
````


<a name="naming"></a>
## 5. Naming

Naming is hard, but very important. It's a crucial part of the process of
developing a maintainable code base, and ensuring that you have a relatively
scalable interface between your HTML and CSS/JS.

* Use clear, thoughtful, and appropriate names for HTML classes. The names
  should be informative both within HTML and CSS files.
* Avoid _systematic_ use of abbreviated class names. Don't make things
  difficult to understand.

Example with bad names:

```html
<div class="cb s-scr"></div>
```

```css
.s-scr {
  overflow: auto;
}

.cb {
  background: #000;
}
```

Example with better names:

```html
<div class="column-body is-scrollable"></div>
```

```css
.is-scrollable {
    overflow: auto;
}

.column-body {
    background: #000;
}
```


<a name="example"></a>
## 6. Practical example

An example of various conventions.

```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset="utf-8">
        <title>Document</title>
        <link rel="stylesheet" href="main.css">
        <script src="main.js"></script>
    </head>
    <body>
        <article class="post" id="1234">
            <time class="timestamp">March 15, 2012</time>
            <a data-id="1234"
             data-analytics-category="[value]"
             data-analytics-action="[value]"
             href="[url]">[text]</a>
            <ul>
                <li>
                    <a href="[url]">[text]</a>
                    <img src="[url]" alt="[text]">
                </li>
                <li>
                    <a href="[url]">[text]</a>
                </li>
            </ul>

            <a class="link-complex" href="[url]">
                <span class="link-complex__target">[text]</span>
                [text]
            </a>

            <input value="text" readonly>
        </article>
    </body>
</html>
```


<a name="license"></a>
## License

_Principles of writing consistent, idiomatic HTML_ by Nicolas Gallagher is
licensed under the [Creative Commons Attribution 3.0 Unported
License](http://creativecommons.org/licenses/by/3.0/). This applies to all
documents and translations in this repository.

Based on a work at
[github.com/necolas/idiomatic-html](https://github.com/necolas/idiomatic-html).
