---
layout: two-cols
---

# Project design

- <span v-mark="{color: '#41B0F6', type: 'underline', at: 0}">custom commands</span>
  - utility commands
  - API calls
  - action sequences
- typescript
- organizing custom commands
- code coverage

::right::

```ts {*|1-7|16-18|9-15|*}{lines:true}
declare global {
  namespace Cypress {
    interface Chainable {
      addBoardApi: typeof addBoardApi;
    }
  }
}

/**
 * Creates a new board using the API
 * @param name name of the board
 * @example
 * cy.addBoardApi('new board')
 *
 */
export const addBoardApi = function(
  this: any, name: string
): Cypress.Chainable<any> {

  return cy
    .request('POST', '/api/boards', { name })
    .its('body', { log: false }).as('board');
    
};

```

<style>
.two-columns {
  gap: 1rem;
  grid-template-columns: 10fr 10fr !important;
}

.two-columns .col-right {
  padding-top: 20px !important;
}


</style>

<!--
- moving on to the topic of how to design your whole project
- one of the superpowers of Cypress is the ability to expand your command library by custom commands
- three types of commands
  - utility commands - getbyDataId, getClipboard, getTooltip
  - api calls
  - action sequences - as we shown, don’t overcomplicate it

- one of the things you can notice in this custom command shown on the right, that it is full of typescript
- this single command will take care of
  - [click] autocompletion
  - [click] correct types for parametern and return types
  - [click] jsdoc documentation
  - [click]
-->

---
layout: two-cols
---

# Project design

- custom commands
  - utility commands
  - API calls
  - action sequences
- typescript
- <span v-mark="{color: '#41B0F6', type: 'underline', at: 0}">organizing custom commands</span>
- code coverage

::right::
<img src="/images/custom_commands.png" class="pt-[30%]" />

<!--
- normally, a place to add your custom commands is the commands.js file that is created by default
- but as you scale up, it is much better to organize them in separate files and store them in it’s own folder
- if you are in a monorepo situation, it’s really hand to create your own library of commands, which then can be imported and used across multiple different projects
-->

---
layout: two-cols
---

# Project design

- custom commands
  - utility commands
  - API calls
  - action sequences
- typescript
- organizing custom commands
- <span v-mark="{color: '#41B0F6', type: 'underline', at: 0}">code coverage</span>


```js
it('opens the page', () => {
  cy.visit('/')
})
```


::right::
<img src="/images/code_coverage.png" />

<style>
.two-columns {
  gap: 1rem;
  grid-template-columns: 1fr 1fr !important;
}

.slidev-code {
  margin-top: 30px;
  margin-right: 130px;
}
</style>

<!--
- one other tool that can be great for keeping up with the project growing is the code coverage

- in the example - a simple visit covers 25% of the application
- this also demonstrates the power of e2e tests

- gets a bad reputation - usually there’s a story of a non-technical manager trying to chase numbers and traumatizing the whole team
- but it’s really useful to think of code coverage as an undiscovered map areas - any rts games fans?
- as project grows bigger, it is impossible for one "test manager" to keep track of every user story being covered by a test
- it also provides information of the areas in app that are being overtested
-->
