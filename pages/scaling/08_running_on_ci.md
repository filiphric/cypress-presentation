---
layout: two-cols
---

# Running in CI

- <span v-mark="{color: '#41B0F6', type: 'underline', at: 0}">tagging tests</span>
- configuration
- running in parallel

::right::

<div class="pt-[30%]">
tagging tests:
```js
it('creates a new board', { tags: ['@smoke'] }, () => {
  // test
})
```
running tags:

```
npx cypress run --env grepTags='@smoke'
```
</div>

<style>
.slidev-layout li {
  font-size: 1.7rem;
}
.slidev-layout ul {
  padding-top: 100px;
}
</style>

<!--
- Cypress really pushed hard on the idea of running your end to end test on your pull requests, or even on every commit
- it came at the time when CI/CD pipelines were getting integrated left and right in companies
- but as your project grows, you may get to a point where your build finishes in 1 minute, but your e2e tests run for 45 - everyone hates that, and for once again, testing is becoming a liability

- so a very nice way of dealing with that so to start tagging your tests
- this is actually one of those things that is good to think about early, because once you scale up and the need for tagging your test emerges, it can be a fairly long process to start tagging your tests from scratch
-->

---
layout: two-cols
---

# Running in CI

- tagging tests
- <span v-mark="{color: '#41B0F6', type: 'underline', at: 0}">configuration</span>
- running in parallel

::right::

<div class="pt-[10%]">
configuration:

```ts
import { defineConfig } from 'cypress'

export default defineConfig({
  // other config attributes
  setupNodeEvents(on, config) {
    // if version not defined, use local
    const version = config.env.version || 'local'
    // load env from json
    config.env = require(`./cypress/config/${version}.json`);
    // change baseUrl
    config.baseUrl = config.env.baseUrl

    return config
  }
})
```

running tests:
```
npx cypress open --env version="production"
```

</div>

<style>
.slidev-layout li {
  font-size: 1.7rem;
}
.slidev-layout ul {
  padding-top: 100px;
}
.two-columns {
  gap: 1rem;
  grid-template-columns: 9fr 10fr !important;
}
</style>

<!--
- another area that’s good to have in mind as the project scales up is the configuration
- chances are you might want to run same tests agains different environments
  - because your API got updated
  - because you have spun up a new environment
  - because you want to run your tests on production
- basically any time you want to run pretty much the same test multiple times, it’s good to move that to the cli level
- so as you can see in this code, we can run different versions production/staging/qa just by changing a flag
- same goes for stuff such as multiple languages, or any type of high level stuff
- this enables you to be prepared for situations like when your ecommerce store diversifies to another country and so on
-->

---
layout: two-cols
---

# Running in CI

- tagging tests
- configuration
- <span v-mark="{color: '#41B0F6', type: 'underline', at: 0}">running in parallel</span>

::right::

<div class="absolute top-35 right-20 w-100" at='0' v-click.hide='1'>
Cypress cloud
<img src="/images/cy_cloud.png" />

running:
```
npx cypress run --record --key=abc123
```
</div>

<div class="absolute top-35 right-20 w-100" v-click at="1">
cypress-split
<img src="/images/cy_split.png" />

running:
```
npx cypress run --env split=true
```
</div>


<style>
.slidev-layout li {
  font-size: 1.7rem;
}
.slidev-layout ul {
  padding-top: 100px;
}
.two-columns {
  gap: 1rem;
  grid-template-columns: 9fr 10fr !important;
}
</style>

<!--
- finally as your project grows in size, it is time to make sure that your tests run fast enough
- even if in your journey are still not there, and you have just a couple of tests, it is good to think about running your tests in parallel from day one - why is that
- if you have one test that creates stuff, one that edits stuff and then another one that deletes stuff, you need to ask yourself if they are not going to interfere with one another if they don’t run on the same machine
- another thing about parallelism in Cypress is this myth that you need to pay for running in parallel, which is kinda unfortunate, since that’s not true
- it is true that Cypress provides a paid service and one of the selling point is that you can run your tests in parallel, but what the Cypress cloud service does is that it makes parallelisation easy and records analytical data on your tests so that they can load-balance them 

- but you don’t have to do that and you can instrument your own parallelization and there are also very cool plugins that help you do so
- one from an ex cypress engineer, called cypress split
- the command you see is pretty much all you have to do in order to split your tests evenly across multiple parallel machines
- if you need load balancing, then you need to do that yourself, but there’s plenty of ways of how you can configure this plugin
-->
