# Chips

> Chips represent complex entities in small blocks, such as a contact.

- Module **@rmwc/chip**  
- Import styles:
  - import **'@material/chips/dist/mdc.chips.css'**;
- MDC Docs: [https://material.io/develop/web/components/chips/](https://material.io/develop/web/components/chips/)

Please note that in MDC, the ChipSet code contains logic for selecting single and multiple chips (filter and choice chip sets). This doesn't fit well with React's uni-directional data flow. Instead it is recommended to write your own filtering and selection logic and just apply the `selected` prop to the `Chip` component directly.

```jsx render
import { Chip, ChipSet } from '@rmwc/chip';

<ChipSet>
  <Chip selected text="Cookies" />
  <Chip text="Pizza" />
  <Chip text="Icecream" />
</ChipSet>

{/* With Icons */}
<ChipSet>
  <Chip
    leadingIcon="favorite"
    text="Cookies"
    trailingIcon="close"
  />
</ChipSet>

{/* Events */}
<ChipSet>
  <Chip
    key="my-chip"
    text="Click Me"
    selected={this.state.evtSelected}
    onRemove={evt => console.log('onRemove', evt.detail)}
    onInteraction={evt => console.log('onInteraction', evt.detail)}
    onTrailingIconInteraction={evt => console.log('onTrailingIconIteraction', evt.detail)}
    trailingIcon="close"
  />
</ChipSet>
```

## Filter and Choice Chipsets

You can specify a `ChipSet` as either a `filter` of `choice` which slightly changes the visual styling of selected chips. While `material-components-web` has some built in functionality for chip sets, it doesn't fit well with React's unidirectional data flow. It is recommended you use standard React patterns to store selected chips in your state and render them accordingly.

Clicking on the trailing close icon will trigger a close animation and put the chip in an exited state, but it is up to you to remove component out from rendering. The you use the `onRemove` prop implement this behavior.

```jsx render
import {
  Chip,
  ChipSet
} from '@rmwc/chip';

<ChipSet filter>
  <Chip
    selected={this.state.cookies}
    onClick={() => this.setState({cookies: !this.state.cookies})}
    checkmark
    text="Cookies"
    trailingIcon="close"
  />
  <Chip
    selected={this.state.pizza}
    onClick={() => this.setState({pizza: !this.state.pizza})}
    leadingIcon="local_pizza"
    checkmark
    text="Pizza"
    trailingIcon="close"
  />
  <Chip
    selected={this.state.icecream}
    onClick={() => this.setState({icecream: !this.state.icecream})}
    checkmark
    leadingIcon="favorite_border"
    trailingIcon="close"
    text="Icecream"
  />
</ChipSet>

<ChipSet choice>
  <Chip
    selected={this.state.cookiesChoice}
    onClick={() => this.setState({cookiesChoice: !this.state.cookiesChoice})}
    text="Cookies"
    trailingIcon="close"
  />
  <Chip
    selected={this.state.pizzaChoice}
    onClick={() => this.setState({pizzaChoice: !this.state.pizzaChoice})}
    leadingIcon="local_pizza"
    text="Pizza"
    trailingIcon="close"
  />
  <Chip
    selected={this.state.icecreamChoice}
    onClick={() => this.setState({icecreamChoice: !this.state.icecreamChoice})}
    leadingIcon="favorite_border"
    trailingIcon="close"
    text="Icecream"
  />
</ChipSet>
```

```jsx renderOnly
import { DocumentComponent } from '@rmwc/base/utils/document-component';
import * as docs from './docgen.json';
import * as iconDocs from '@rmwc/icon/docgen.json';

<DocumentComponent docs={docs} displayName="Chip" />
<DocumentComponent docs={docs} displayName="ChipSet" />
```
