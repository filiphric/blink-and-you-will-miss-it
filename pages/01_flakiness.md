---
layout: default
---

# Testing pyramid
<img src="/images/pyramid.png" class="h-70 m-auto mt-10" />

<!--
- at the risk of half people leaving my presentation, I’m going to show the testing pyramid
- probably all know this model 
- e2e tests costly and slow, unit tests are cheap and fast
- i believe that this model is very outdated
- we have much better tools nowadays
- especially the cost of creating a test is not so high
- as a result we now have more of them
-->

---
layout: default
---

# Testing speed
<img src="/images/turtle.png" class="h-10 m-auto mt-[16%]" />

<!--
- but let’s stop at this little guy
- because as I said, we have some great tools nowadays
- but they all seem to be battling for speed of execution
- I have read countless blog posts comparing pw and cy or some other tools
- they are focusing on execution
-->

---
layout: section
---

# Speed of execution vs. speed of maintenance

<!--
- but if you answered "yes" to any of the questions from before, you know there’s a difference between speed of execution and speed of maintenance
- the funny thing is that we sometimes don’t notice this
- when it takes 30 minutes to run your tests in the pipeline, we as developers are happy to spend a month of our time migrating from one testing tool to another so that we can take it down to 25 minutes
- and we do all this work, because we believe that maintaining e2e tests is just too much work - still mentally living at the top of the pyramid
- and to be completely honest, I think in many way we really are living at the top of that pyramid, example
-->

---
layout: default
---

# Flaky test "fixing" strategies
![](/images/strategies.png){class="h-80"}

<!--
- we have these so-called strategies helping us live with the fact that our tests are flaky
- I’ve seen these strategies across many companies I’ve worked with
- muting a test
- quarantining a test
- retrying a test
- adding a longer timeout
- reproducing a test locally
- deleting a test
-->

---
layout: default
---
# Flaky test "fixing" strategies

![](/images/stages_of_grief.png){class="h-80"}

<!-- 
- or as I like to call them:
- shock
- denial 
- anger
- bargaining 
- depression
- acceptance
-->

---
layout: center
---
![](/images/what_happens.png)

<!-- 
- These strategies exist, because we have limited visibility into what is happening in CI
- many times, we are simply left with an error message:
-->

---
layout: two-cols
---
# e2e flakiness

```plain
❌ Timed out retrying: Expected to find element, but never found it.
```

```plain
❌ failed because the element cannot be interacted with
```

```plain
❌ failed because the element is covered by another element
```

```plain
❌ failed because the page updated
```

```plain
❌ ...
```

<!-- 
- The main problem when dealing with e2e tests is the lack of context
- e2e test usually copies a user story
- when element is not found, it tells us nothing about what exactly failed
- when a test ends up with an error like this, the problem that caused this error happened a couple of steps before
- I want to share a couple of stories with you that start with a mysterious message like this
- these are stories I either encountered personally, or with our clients at Replay
- one of those clients is Metabase
 -->
