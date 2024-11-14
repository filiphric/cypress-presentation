---
layout: default
---

# Open browser with devtools open

```js
import { defineConfig } from 'cypress';

export const defineConfig({
  setupNodeEvents(on, config) {
    on('before:browser:launch', (browser, launchOptions) => {
      if (browser.name === 'chrome' ) {
        launchOptions.args.push('--auto-open-devtools-for-tabs');
        return launchOptions;
      }
    });
  },
});
```

---
layout: default
---

# .then() vs .should()

```js
cy.get('element').then(($el) => {
  expect($el).to.be.visible;
});
```
```js
cy.get('element').should(($el) => {
  expect($el).to.be.visible;
});
```

---
layout: default
---

# passing types into requests

```js
interface Items {
  items: {
    id: number;
    name: string;
    price: number;
  }[];
}

cy.request<Items>('/api/items')
  .its('body.items') // autocompleted in VS Code
```

---
layout: default
---

# Testing API in Cypresss

```
npm i cypress-plugin-api
```

```js
import 'cypress-plugin-api/commands';
cy.api('/api/items')
```

![cypress-plugin-api](/images/demo.gif)

---
layout: default
---

# Hide XHR events

```
npm i cypress-plugin-xhr-events
```

```js
import 'cypress-plugin-xhr-events';
```

![cypress-plugin-xhr-events](/images/toggle.gif){class="h-100 m-auto"}
