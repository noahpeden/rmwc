# Buttons

> Buttons communicate the action that will occur when the user touches them.

- import from **rmwc/Button**  
- import styles from **@material/button/dist/mdc.button.css**
- [https://material.io/develop/web/components/buttons/](https://material.io/develop/web/components/buttons/)

```jsx render
import { Button, ButtonIcon } from 'rmwc/Button';

<Button>Default</Button>
<Button><ButtonIcon icon="favorite" /> With Icon</Button>
<Button raised>Raised</Button>
<Button dense>Dense</Button>
<Button unelevated>Unelevated</Button>
<Button outlined>Outlined</Button>
<Button raised theme="secondary-bg on-secondary">With Theme</Button>


{/*
  Modify the Buttons Ripple.
  This example uses "accent" to control the color of the Ripple.
  See the documentation on Ripples.
  */
}
<Button theme="secondary" accent>With Theme</Button>
<Button ripple={false}>No Ripple</Button>
```

```jsx renderOnly
import { DocumentComponent } from 'rmwc/Base/utils/DocumentComponent';

<DocumentComponent displayName="Button" />
<DocumentComponent displayName="ButtonIcon" composes={['Icon']} />
```