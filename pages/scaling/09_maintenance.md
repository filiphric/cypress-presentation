---
layout: two-cols
---

# Maintenance

- maintenance vs. development cost
- flaky tests

::right::
<div class="absolute top-45 right-20 w-100" at="0" v-click.hide='1'>
<img src="/images/speed_improvement.png"/>
</div>

<div class="absolute top-30 right-20 w-100" v-click at="1">

```js
cy.contains('01')
cy.contains('04')
```

<video src="/images/stopwatch.mov" autoplay loop class="h-[80%] m-auto" />

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
- as your project grows, it is important to think about the cost of maintenance that you are introducing with every new test
- this graph may not look like this for you today, but it can very well look like that later and driving down that debugging and maintenance time is going to be important
- that’s why today we are talking about readability, and not about which framework runs the fastest on CI

- but when we talk about testing and test code, we cannot really skip talking about the application under test
- all that we said today might be useful, but as you scale up, you are still going to be hitting some flaky tests - and they are going to add to your debugging time and to your testing time

- for those situations, you need to make sure that you have a proper insight into how your test ran and what it actually did
- so it’s good to make a stop and talk about what flakiness actually is and I want to demonstrate that with the following example [click]

- even though we are not checking every number, the test passes
- this demonstrates the interaction between the test script and the application under test
- flakiness is essentially a disconnect or a de-sync between the test script and application under test
- whenever flakiness occurs, it usually happens inbetween commands, so debugging a test flake, is mostly looking at the application and getting a good understanding of what is happening inside

- that’s why I have been talking to testers about getting more technical and getting a better understanding of the application code as it is crucial when debugging
- and will drive that debugging time down
-->

---
layout: two-cols
---

# Maintenance

- maintenance vs. development cost
- flaky tests

::right::
<div class="absolute top-30 right-20 w-100">
 <img src="/images/test_replay.png"/>
 <img src="/images/dashboard.png" class="pt-5" />
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