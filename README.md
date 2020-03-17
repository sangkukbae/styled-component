# styled-component

## :page_facing_up: 목차 
* [Style an HTML Element](#style-an-html-element)
* [Style a React Component](#style-a-react-component)
* [Creating Global Styles](#creating-global-styles)
* [Adjust Style based on props](#adjust-style-based-on-props)
* [Animate Styled Components](#animate-styled-components)
* [Create and use a Theme](#create-and-use-a-theme)
* [Style pseudo-selectors and classes](#style-pseudo-selectors-and-classes)
* [Using the `css` prop to define styles](#using-the-css-prop-to-define-styles)
* [Using the `as` prop to reassign the HTML tag](#using-the-as-prop-to-reassign-the-html-tag)
* [Use the `attrs` method to add HTML attributes](#use-the-attrs-method-to-add-html-attributes)
* [Use Styled Components with the Object syntax](#use-styled-components-with-the-object-syntax)
* [Style a component based on complex props](#style-a-component-based-on-complex-props)

## Style an HTML Element
```jsx
import React from "react";
import styled from "styled-components";

const Heading1 = styled.h1`
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Oxygen,
    Ubuntu, Cantarell, "Open Sans", "Helvetica Neue", sans-serif;
  text-align: center;
  color: papayawhip;
`;

export default function App() {
  return (
    <div className="App">
      <Heading1>Hello Styled Components</Heading1>
    </div>
  );
}
```
[https://3ddyy.csb.app/](https://3ddyy.csb.app/)

## Style a React Component 
```jsx
import React from "react";
import Button from "@material-ui/core/Button";
import styled from "styled-components";

const FullWidthButton = styled(Button)`
  width: 100%;
  height: 50px;
`;

export default function App() {
  return (
    <div className="App">
      <h1>Hello Styled Components</h1>
      <FullWidthButton variant="contained" color="primary">
        Click me
      </FullWidthButton>
    </div>
  );
}
```
[https://ocgg9.csb.app/](https://ocgg9.csb.app/)

## Creating Global Styles
```jsx
import React from "react";
import styled, { createGlobalStyle } from "styled-components";
import movies from "./movies";

const Global = createGlobalStyle`
  body {
    text-align: center;
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
    color: green;
  }
`;

const Movies = styled.ul`
  margin: 0;
  margin-top: 50px;
  display: grid;
  max-width: 80%;
  grid-template-columns: repeat(3, 1fr);
  align-items: center;
`;

const Movie = styled.li`
  list-style: none;
  min-height: 40px;
`;

export default function App() {
  return (
    <>
      <Global />
      <Movies>
        {movies.map(({ title, rating }) => (
          <Movie>{title}</Movie>
        ))}
      </Movies>
    </>
  );
}
```
[https://c6j5s.csb.app/](https://c6j5s.csb.app/)

## Adjust Style based on props
```jsx
import React from "react";
import styled from "styled-components";

const people = ["Sara", "Alex", "Carolyn", "Monica", "Tomasz"];

const Person = styled.li`
  font-family: Arial, Helvetica, sans-serif;
  color: gray;

  ${props =>
    props.even &&
    `
       color: white;
        background: black;
        list-style: none;
      `}
`;

export default function App() {
  return (
    <div className="App">
      <h1>Hello Styled Components</h1>
      {people.map((person, i) => (
        <Person even={(i + 1) % 2 === 0}>{person}</Person>
      ))}
    </div>
  );
}
```
[https://x4lxx.csb.app/](https://x4lxx.csb.app/)

## Animate Styled Components
```jsx
import React from "react";
import styled, { keyframes } from "styled-components";

const move = keyframes`
  from {
    transform: translateX(0) rotate(0);
  }
  to {
    transform: translateX(100%) rotate(45deg);
  }

`;

const Heading = styled.h1`
  animation: ${move} 2s ease infinite;
  font-family: Arial, Helvetica, sans-serif;
`;

export default function App() {
  return (
    <div className="App">
      <Heading>Hello Styled Components</Heading>
    </div>
  );
}
```
[https://9s7wn.csb.app/](https://9s7wn.csb.app/)

## Create and use a Theme

```jsx
import React from "react";
import styled from "styled-components";

const Heading = styled.h1`
  font-family: ${({ theme }) => theme.fonts.body};
  color: ${props => props.theme.colors.purple};
`;

export default function App() {
  return (
    <div className="App">
      <Heading>Hello Styled Components</Heading>
    </div>
  );
}
```
[https://np4hx.csb.app/](https://np4hx.csb.app/)

## Style pseudo-selectors and classes
```jsx
import React from "react";
import styled from "styled-components";

const Heading = styled.h1`
  font-family: ${({ theme }) => theme.fonts.body};
  color: ${props => props.theme.colors.purple};
`;

const Button = styled.button`
  padding: 8px 12px;
  border: 0;
  color: ${props => props.theme.colors.tan};
  background: ${props => props.theme.colors.red};
  transition: all 200ms ease;

  ::before {
    content: "🎉";
  }

  :hover {
    background: ${props => props.theme.colors.tan};
    color: ${props => props.theme.colors.red};
  }
`;

export default function App() {
  return (
    <div className="App">
      <Heading>Hello Styled Components</Heading>
      <Button>I am a button</Button>
    </div>
  );
}
```

[https://50pbx.csb.app/](https://50pbx.csb.app/)

## Using the `css` prop to define styles
```jsx
import React from "react";
import styled from "styled-components/macro";

const Heading = styled.h1`
  font-family: ${({ theme }) => theme.fonts.body};
  color: ${props => props.theme.colors.purple};
`;

const Button = styled.button`
  font-family: ${({ theme }) => theme.fonts.body};
  display: inline-block;
  padding: 8px 12px;
  border: 0;
  color: ${props => props.theme.colors.tan};
  background: ${props => props.theme.colors.red};
  transition: all 200ms ease;
  font-size: 14px;
  text-decoration: none;

  :hover {
    background: ${props => props.theme.colors.tan};
    color: ${props => props.theme.colors.red};
  }
`;

export default function App() {
  return (
    <div className="App">
      <Heading>Hello Styled Components</Heading>
      <Button>I am a button</Button>
      <Button
        css={`
          color: green;
        `}
      >
        Another Button
      </Button>
      <Button as="a" href="https://google.com">
        google
      </Button>
    </div>
  );
}
```
[https://d2oph.csb.app/](https://d2oph.csb.app/)

## Using the `as` prop to reassign the HTML tag
```jsx
import React from "react";
import styled from "styled-components/macro";

const Heading = styled.h1`
  font-family: ${({ theme }) => theme.fonts.body};
  color: ${props => props.theme.colors.purple};
`;

const Button = styled.button`
  font-family: ${({ theme }) => theme.fonts.body};
  display: inline-block;
  padding: 8px 12px;
  border: 0;
  color: ${props => props.theme.colors.tan};
  background: ${props => props.theme.colors.red};
  transition: all 200ms ease;
  font-size: 14px;
  text-decoration: none;

  :hover {
    background: ${props => props.theme.colors.tan};
    color: ${props => props.theme.colors.red};
  }
`;

export default function App() {
  return (
    <div className="App">
      <Heading>Hello Styled Components</Heading>
      <Button>I am a button</Button>
      <Button
        css={`
          color: green;
        `}
      >
        Another Button
      </Button>
      <Button as="a" href="https://google.com">
        google
      </Button>
    </div>
  );
}
```
[https://ii197.csb.app/](https://ii197.csb.app/)

## Use the `attrs` method to add HTML attributes
```jsx
import React from "react";
import styled from "styled-components";

const Heading = styled.h1`
  font-family: ${({ theme }) => theme.fonts.body};
  color: ${props => props.theme.colors.purple};
`;

const Button = styled.button.attrs(props => ({
  type: props.type || "button"
}))`
  font-family: ${({ theme }) => theme.fonts.body};
  display: inline-block;
  padding: 8px 12px;
  border: 0;
  color: ${props => props.theme.colors.tan};
  background: ${props => props.theme.colors.red};
  transition: all 200ms ease;
  font-size: 14px;
  text-decoration: none;

  :hover {
    background: ${props => props.theme.colors.tan};
    color: ${props => props.theme.colors.red};
  }
`;

export default function App() {
  return (
    <div className="App">
      <Heading>Hello Styled Components</Heading>
      <Button type="submit">I am a button</Button>
      <Button>I am another one</Button>
    </div>
  );
}
```
[https://dtgk4.csb.app/](https://dtgk4.csb.app/)

## Use Styled Components with the Object syntax
```jsx
import React from "react";
import styled from "styled-components";

// const Heading = styled.h1`
//  text-align: center;
//  font-size: ${props => (props.small ? 16 : 14)}px;
//  font-family: -apple-system, sans-serif
// `;

const Heading = styled.h1(({ small }) => ({
  textAlign: "center",
  fontSize: small ? 16 : 24,
  fontFamily: "apple-system, sans-serif"
}));

export default function App() {
  return (
    <div className="App">
      <Heading>Hello Styled Components</Heading>
      <Heading small>I am smaller</Heading>
    </div>
  );
}
```
[https://6jjs0.csb.app/](https://6jjs0.csb.app/)

## Style a component based on complex props 
```jsx
import React from "react";
import styled from "styled-components";
import movies from "./movies";

const Grid = styled.main`
  max-width: 80%;
  margin: 50px auto;
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  grid-gap: 20px;
`;

const Rating = styled.span`
  display: block;
  color: ${({ rating, theme }) => {
    if (rating < 2.3) return theme.red;
    if (rating < 2.7) return theme.yellow;

    return theme.accent;
  }};
  background: ${props => (props.length === props.number ? "black" : null)};
`;

export default function App() {
  return (
    <Grid>
      {movies.map((movie, i) => (
        <article>
          {movie.title}
          <Rating
            length={movies.length}
            number={i + 1}
            rating={parseFloat(movie.rating)}
          >
            {movie.rating}/10
          </Rating>
        </article>
      ))}
    </Grid>
  );
}
```
[https://lfy8o.csb.app/](https://lfy8o.csb.app/)

:memo: **참고 자료**   
* [https://egghead.io/playlists/styling-react-applications-with-styled-components-8834](https://egghead.io/playlists/styling-react-applications-with-styled-components-8834)
