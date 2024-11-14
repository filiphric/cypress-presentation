---
layout: two-cols
---

# Test design

- focusing on behaviors
- arrange - act - assert
- testing patterns
  - POM?
  - BDD?
  - DRY?
  - Custom commands?


::right::
<img src="/images/project_1.png" class="w-80 my-15" />
<img src="/images/aaa.png" class="w-80 mt-10" />

<style>
.slidev-layout li {
  font-size: 1.7rem;
}
.slidev-layout ul {
  padding-top: 10%;
}
.slidev-layout ul li ul li {
  font-size: 1.2rem;
}
</style>

<!--
- one question that’s going to be important as you scale your project is how do you design each individual test - building block of your whole test project - **so let’s talk about that for a moment**

- focus on behaviors

- quoting Kent C. Dodds - The more your tests resemble the way your software is used, the more confidence they can give you.
- as you scale up, your tests are going to resemble user stories, and you can organize those user stories into folders as shown in a picture

- another thing that’s going to become more important as your project scales up, is the pattern of your individual test
- I highly recommend using the arrange act assert pattern
- in Cypress you can put your "arrange" part in before or beforeEach block and group those tests that have the same test setup

- then finally, there’s the question of testing patterns - POM, Custom commands, BDD,... - which one is the best?
- many of you might have read that you should not use POM with Cypress and instead use App actions
- the problem is, no one really knows what app actions are
- the underlying problem of the question "should I use POM" is - how do I make abstractions in my project and make sure that as the project scales up, I don’t end up refactoring my whole project every month

- and it is a very good question, that you should ask early - the only problem with that question is that at the time you are asking it, you might not gave all the information
- you may have heard about the "DRY" principle - don’t repeat yourself, and that’s what POM is all about
- and it’s hard to say if POM is good or bad or that DRY principle is good or bad - my advise here is (and it might come of weird being said at "Cypress at scale" webinar) Don’t try to optimize too early
- if you optimize too early, it might be just you guessing what may happen in the future
- so let’s be more specific, because I’d like to show you how this premature optimization usually happens
-->

---
src: ./05a_abstractions.md
---
