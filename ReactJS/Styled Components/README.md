## Styled Components in ReactJS

## What are Styled Components?

*   It is a CSS-in-JS styling solution for React and React Native.
*   It uses tagged template literals which allows you to write plain CSS that is scoped to a single component inside your JS code.

### Benefits / Features

*   **Automatic Critical CSS:** The library keeps track of what components are rendered on the screen and injects only their styles. Hence, we are injecting only the necessary amount of code.
*   **No class name bug:** It generates unique class names for every style, hence the dev does not have to worry about duplication, typo, etc.
*   **Easier deletion of CSS:** Since every style is tied to a component, hence an unused component means unused styling.
*   **Dynamic Styling:** It makes styling based on props possible.
*   **Painless Maintenance:** Makes it easier to maintain style as component and style is stored together.
*   **Automatic Vendor Prefixing:** Write your CSS as per current standard, and the library will handle the browser specific rendering.

Recommended VSCode Extension: **vscode-styled-components**

**Install Styled Components Library**

`npm i styled-components -save`

Syntax: 

```plaintext
constr component_name = styled.HTML_element`
	//CSS here
`;
```

Example:

```javascript
import React from "react";
import styled from "styled-components";


import "./App.css";


const StyledButton = styled.button`
    padding: 15px 32px;
    background-color: #4caf50;
    border-color: #4caf50;
    font-size: 16px;
`;


function App() {
    return (
        <div>
            <button> Normal Button </button> <br />
            <StyledButton>Styled Button</StyledButton>
        </div>
    );
}


export default App;
```

Conventionally we keep code in `Button.js` and styling in `Button.styles.js`

### Using Props

```javascript
import styled from "styled-components";

export const StyledButton = styled.button`
    padding: 15px 32px;
    background-color: ${(props) =>
        props.variant === 'outlined' ? '#FFF' : '#4caf50'};
    border-color: #4caf50;
    font-size: 16px;
`;
```

### Extending Styles

Used to reuse styling code and / or add additional properties for some specific customisation.

```javascript
import styled from "styled-components";

export const StyledButton = styled.button`
    padding: 15px 32px;
    background-color: ${(props) =>
        props.variant === 'outlined' ? '#FFF' : '#4caf50'};
    border-color: #4caf50;
    font-size: 16px;
`;


export const FancyButton = styled(StyledButton)`
    background-image: linear-gradient(to right, #f6d365 0%, #fda085 100%);
`;
```

### Polymorphic Prop with Styled Component

`<FancyButton as = "a">Fancy Button</FancyButton>`

Now this component will be rendered as an anchor tag in the source html.

### **Pseudo Classes in Styled Components**

```javascript
import styled from "styled-components";

export const StyledButton = styled.button`
    padding: 15px 32px;
    background-color: ${(props) =>
        props.variant === 'outlined' ? '#FFF' : '#4caf50'};
    color: ${(props) =>
        props.variant === 'outlined' ? '#4caf50' : '#FFF'};
    border-color: #4caf50;
    font-size: 16px;
    transition: 0.5s all ease-out;
    //Pseudo Classes


    &:hover {
        background-color: ${(props) =>
        props.variant !== 'outlined' ? '#FFF' : '#4caf50'};
    color: ${(props) =>
        props.variant !== 'outlined' ? '#4caf50' : '#FFF'};
    }
`;
```

### Passing Props and Adding Attributes

```javascript
export const SubmitButton = styled(StyledButton).attrs({
    type: 'submit'
})`
	// CSS here
`;
```

Now, on inspecting the HTML you will get a type attribute. We can also make this attribute as props to the current component as:

```javascript
export const SubmitButton = styled(StyledButton).attrs((props) => ({
    type: 'submit'
}))`
	// CSS Here
`;
```

### Adding Animations

```javascript
const rotate = keyframes`
    from {
        transform: rotate(0deg);
    }
    to {
        transform: rotate(360deg);
    }
`;

export const AnimatedButton = styled(StyledButton)`
    height: 40vh;
    pointer-events: none;
    animation: ${rotate} infinite 2s linear;
`;
```

### Theming with Styled Components

Styled Components have full theming support by exporting the `ThemeProvider` component.

Declating the theme

```javascript
import { ThemeProvider } from "styled-components";

const theme = {
    dark: {
        primary: '#000',
        text: '#fff'
    },
    light: {
        primary: '#fff',
        text: '#000'
    }
}



function App() {
    return (
        <ThemeProvider theme={theme}>
        	// This theme will be accessible to all the components here
		</ThemeProvider>
    );
}
```

Using the theme

```javascript
export const DarkButton = styled(StyledButton)`
    border: 2px solid ${(props) => props.theme.dark.primary};
    background-color: ${(props) => props.theme.dark.primary};;
    color: ${(props) => props.theme.dark.text};
`;
```

### Working with Global Styles

Used to add base stylesheet

```javascript
import {createGlobalStyle } from "styled-components";
const GlobalStyle = createGlobalStyle`
    button {
        font-family: 'Roboto';
    }
`;
function App() {
    return (
        <GlobalStyle />
		... more code here
	);
}
```