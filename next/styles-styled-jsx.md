# Dynamic CSS

## Inside component

style jsx - allows to write scoped component styles in js/jsx

Component:

```jsx
const Button = (props) => (
    <button>
        {props.children}
        <style jsx>{`
            button {
                padding: ${'large' in props ? '50' : '20'}px;
                background: ${props.theme.background};
                color: #999;
                display: inline-block;
                font-size: 1em;
            }
        `}</style>
    </button>
);
```

Use case:

```jsx
<Button large theme={{ background: 'blue' }}>
    Click me
</Button>
```

Notes:

{props.children} - renders any content that is put inside the btn

the conditional styles in the component check what is passed to the actual used component and render that in the ui.

Props are defined wherever the component is used and they determine how it looks and behaves.

## Outside component

style jsx allows to write styles outside of the component render method or in separate js modules

styled-jsx/css library exports 3 tags that can used to tag styles:

`css`, the default export, to define scoped styles.
`css.global` to define global styles.
`css.resolve` to define scoped styles that resolve to the scoped className and a styles element.

### css tag

use to define scope styles - the styles defined with css tag will apply only to the component they are written in, they will not affect other components

```jsx
import css from 'styled-jsx/css';

const { className, styles } = css`
    h1 {
        color: blue;
    }
`;

const MyComponent = () => (
    <>
        <h1 className={className}>Hello World</h1>
        <style jsx>{styles}</style>
    </>
);
```

### css.resolve tag

Use it to define scoped styles with additional benefits (to define scoped styles that resolve to a scoped className and a styles element)
.resolve returns an object containing unique generated className and styles element which encapsulates the styles defined in css.resolve block

```jsx
import css from 'styled-jsx/css';

const { className: h1ClassName, styles: h1Styles } = css.resolve`
    h1 {
        color: red;
    }
`;

// is this correct way to add styles?
const MyComponent = () => (
    <>
        <h1 className={h1ClassName}>Hello World</h1>
        <p>Nice to meet you</p>
        <style jsx>{`
            p {
                color: red;
            }
            ${h1Styles}
        `}</style>
    </>
);
```

```jsx
// another way to add styles?

const { className, styles } = css.resolve`
    a {
        color: green;
    }
`;

export default () => (
    <div>
        {/* use the className */}
        <Link className={className}>About</Link>

        {/* render the styles for it */}
        {styles}
    </div>
);
```
