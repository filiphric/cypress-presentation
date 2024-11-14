---
layout: two-cols
---

# Readability

- selectors
- test annotation

````md magic-move
```js
// ❌ don’t do it like this
it('board is visible', () => {})
it('works in edge cases', () => {})
it('handles input', () => {})
```

```js
// ✅ much better
it('creates a board and navigates to board detail', () => {})
it('throws error when trying to access private board', () => {})
it('shows a warning message when input is empty', () => {})
```
````

- documentation
  - installation of the projects
  - explanations, recommendations, examples
  - PR rules

::right::
<img src="/images/selectors.png" class="pt-20 pl-10" />

<style>
.two-columns {
  gap: 1rem;
  grid-template-columns: 6fr 5fr !important;
}

.slidev-layout li {
  font-size: 1.7rem;
}
.slidev-layout ul {
  padding-top: 10px
}

.slidev-layout ul li ul li {
  font-size: 1.2rem;
}
</style>

<!--
- why readability - because when you write a complex test that does a very complex thing and it finally passes, it feels like a victory. until you need to open that test again and debug what’s wrong. there’s a reason why developer have peer reviews and focus on writing good code - no one wants to refactor or add functionality to garbage code, because they are afraid something will break

- selectors can be a big part of readability
- approaches
  - data-id
  - accessibility selectors
  - everything else
  - you can combine approaches, it’s fine

- test annotation is another aspect that should not be overlooked
- when the test is passing, as long as it’s doing what it is supposed to be doing, it’s great
- but when you have to maintain it, it’s a whole different story, you need to understand what’s going on
- maybe it’s not you who wrote the test
- being able to navigate through the code efficiently is going to make a huge difference as your project contains more tests, more people contribute to it etc.

- providing good documentation you can help that a lot

Usually the documentation contains 3 important parts:
- installation of the projects
- explanations, recommendations, examples
- pull request rules (these can be added to the platform you use)
-->
