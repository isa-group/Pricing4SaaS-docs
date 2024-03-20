---
sidebar_position: 1
---

# Main Component

The package provides a component that contains almost the whole logic you need to manage your toggles: `Feature`. This component allows to show or hide its children depending on the evaluation of a pricing feature. Depending on the context, it can have up to four children:
- `On`: This component will be shown if the feature is evaluated to `true`. It has the prop `expression`, which reads from the JWT the evaluation of the feature. You can use the `feature` function to locate features by their key. **REQUIRED**
- `Default`: This component will render its children if the evaluation of the feature performed in `On` component is `false`.
- `Loading`: This component will render its children while the evaluation of the feature is being performed.
- `ErrorFallback`: This component will render its children if an error occurs while the evaluation of the feature is being performed.

The evaluation of a feature that has the key `myFeature` would be:

```jsx
<Feature>
    <On expression={feature("cloudStorage")}>
        <p>Cloud Storage is enabled</p>
    </On>
    <Default>
        <p>Cloud Storage is disabled</p>
    </Default>
    <Loading>
        <p>Loading...</p>
    </Loading>
    <ErrorFallback>
        <p>An error occurred</p>
    </ErrorFallback>
</Feature>
```