# react-smart-scroll

Vertical scroll solution that follows what you actually read

```jsx
import { Fragment as 👻 } from 'react';
import { Section } from 'react-smart-scroll';

export const Page = () => (
  <👻>
    <Section name="introduction">
      <h1>Introductin</h1>
      <p>By default Section wraps it's content with a div</p>
    </Section>
    <Section name="chapterOne" component="section">
      <h2>Chapter one</h2>
      <p>You can also provide component prop that specifies html tag rendered by Section</p>
    </Section>
    <Section name="chapterTwo" render={(handleRef) => (
      <YourWrapperComponent ref={handleRef}>
        <h2>Chapter two</h2>
        <p>You can also use your wrapping component as long as you provide a reference to a rendered DOM element</p>
      </YourWrapperComponent>
    )} />
  </👻>
);
```

```jsx
import { ScrollSpy } from 'react-smart-scroll';

const labels = {
  introduction: "Introduction",
  chapterOne: "Chapter one",
  chapterTwo: "Chapter two",
};

export const Navigation = () => (
  <nav>
    <ul>
      <ScrollSpy render={(sections) => (
        {sections.map(section => (
          <li key={section.name} className={section.active ? "active" : null}>
            <a href="#" onClick={section.scroll}>{labels[section.name]}</a>
          </li>
        ))}
      )} />
    </ul>
  </nav>
)
```

```jsx
import { SectionSpy } from 'react-smart-scroll';

export const Navigation = () => (
  <nav>
    <ul>
      <SectionSpy
        name="introduction"
        render={section => (
          <li className={section.active ? 'active' : null}>
            <a href="#" onClick={section.scroll}>
              Introduction
            </a>
          </li>
        )}
      />
    </ul>
  </nav>
);
```
