- ## `Challenge 1`

```js
function incrementNumberByOne(number) {
    return ++number;
}

alert(incrementNumberByOne(1));
```

- ## `Challenge 2`

```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset="utf-8">
        <title>Red Matter</title>
        <style type="text/css">
            a {
                color: red;
                text-transform: uppercase;
                text-decoration: none;
            }
            a:before {
                content: ">";
            }
        </style>
    </head>
    <body>
        <a href="http://www.redmatter.com">redmatter.com</a>
    </body>
</html>
```

- ## `Challenge 3`

```js
function getDayOfWeek(dayNumber) {
    switch (dayNumber) {
        case 0:
            day = "Sunday";
            break;
        case 1:
            day = "Monday";
            break;
        case 2:
            day = "Tuesday";
            break;
        case 3:
            day = "Wednesday";
            break;
        case 4:
            day = "Thursday";
            break;
        case 5:
            day = "Friday";
            break;
        case 6:
            day = "Saturday";
            break;
    }
    return day;
}

alert(getDayOfWeek(3) + " and " + getDayOfWeek(4));
```

- ## `Challenge 4` - "white-wpace: no-wrap" Solution

```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset="utf-8">
        <title>Red Matter</title>
        <style type="text/css">
            body {
                font-family: "sans-serif";
                font-size: 1em;
                white-space: nowrap;
            }
            .column {
                /* width: 50%; */
                width: calc(50% - 2.25em);
                padding: 1em;
                border: 1px solid red;
                float: left;
                white-space: normal;
            }
        </style>
    </head>
    <body>
        <div class="column">
            Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.
        </div>
        <div class="column">
            Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.
        </div>
    </body>
</html>
```

The problem with this solution is that it does not remove the `white-space` between the divs and needs resetting back to `normal` on the child elements (div).

The gap between the two divs result in an overall width of 100% plus 4px. This can be remedied by using the CSS `calc` function to subtract 2px from each div and optional 0.25px from html / body content margin & padding for scroll free and visual optimization on this case.

- ## `Challenge 4` - CSS3 Using Flexbox

```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset="utf-8">
        <title>Red Matter</title>
        <style type="text/css">
            body {
                font-family: "sans-serif";
                font-size: 1em;
                display: flex;
            }
            .column {
                width: 50%;
                padding: 1em;
                border: 1px solid red;
                float: left;
                flex-grow: 1;
            }
        </style>
    </head>
    <body>
        <div class="column">
            Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.
        </div>
        <div class="column">
            Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.
        </div>
    </body>
</html>
```

`Flexbox` is not supported in IE10 or below and only partially supported in IE11.

- ## `Challenge 5`

```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset="utf-8">
        <title>Red Matter</title>
    </head>
    <body>
        <table id="products">
            <tr>
                <th>Product Code</th>
                <th>Description</th>
                <th>Price</th>
                <th></th>
            </tr>
            <tr>
                <td data-column="code">1001</td>
                <td data-column="description">Yealink T10</td>
                <td data-column="price">79.99</td>
                <td data-column="actions"><button type="button" value="1001">Add to Basket</button></td>
            </tr>
            <tr>
                <td data-column="code">1001</td>
                <td data-column="description">Yealink T20</td>
                <td data-column="price">109.99</td>
                <td data-column="actions"><button type="button" value="1002">Add to Basket</button></td>
            </tr>
        </table>
        <script>
            function btnClick(event) {
                const tr = event.target.parentNode.parentNode;
                const description = tr.querySelector('[data-column="description"]').innerText;
                const price = tr.querySelector('[data-column="price"]').innerText;
                alert('The ' + description + ' costs ' + price);
            }

            document.querySelectorAll('#products [data-column="actions"] button').forEach(button => {
                button.onclick = btnClick;
            });
        </script>
    </body>
</html>
```