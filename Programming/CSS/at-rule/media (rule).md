#CSS 

```
/* At the top level of your code */
@media screen and (min-width: 900px) {
  article {
    padding: 1rem 3rem;
  }
}

/* Nested within another conditional at-rule */
@supports (display: flex) {
  @media screen and (min-width: 900px) {
    article {
      display: flex;
    }
  }
}

```

## media types

`all` (default)
`print`
`screen`

## media features
https://developer.mozilla.org/en-US/docs/Web/CSS/@media#media_features