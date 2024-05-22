---
layout: center
---
# False positive flake

<!-- 
- we like our tests green
- but there are cases where a green tests hides a real issue
- failed: https://app.replay.io/recording/cypresse2ea11ycyts--5927ab03-d263-4c91-a159-68ea4c3d1269
- passing: https://app.replay.io/recording/cypresse2ea11ycyts--c6e8789f-96e0-40dc-b528-c3cd07d8132a
-->

---
layout: default
---
# False positive flake

```js
beforeEach(() => {
  cy.visit('/');
  cy.contains('Loading').should('not.exist');
  cy.injectAxe();
});

it('Checks accessibility of a page', () => {
  cy.checkA11y();
});
```

<!-- 
- show code, then go to demo
- we see the error message, but we don’t see what exactly is coing on
- the nature of Cypress commands is that they sometimes hide what is going on behind
- but we can actually see those violations
- search elements
- search react components
- compare to passing test - code was not ran at all
-->

---
layout: default
---
# False positive flake

```js {*|8}
beforeEach(() => {
  cy.visit('/');
  cy.contains('Loading').should('not.exist');
  cy.injectAxe();
});

it('Checks accessibility of a page', () => {
  cy.get('.modal').should('be.visible')
  cy.checkA11y();
});
```
<!-- 
- the problem now is, that we did not make sure that application is ready for accessibility check
- [click] we need to make sure by check the modal presence first
-->
