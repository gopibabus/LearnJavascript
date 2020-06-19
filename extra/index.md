# 🔥DeadLocks in JavaScript

<img src="./assets/images/deadlock.png" alt="deadlock" width="700" height="400"/>

?> **Deadlocks** are a set of blocked processes each holding a resource and waiting to acquire a resource held by another process. This is the term you frequently listen in Operating Systems and MySQL.

?> Being single-threaded means that deadlocks are impossible except in conditions in which sequential process would fail to end. This could happen if a program has cyclic dependencies.

```js
var loop = true,
    block = setTimeout(function(){loop = false}, 1);
while(loop);
```

!> Above one is a deadlock, because while loop is waiting that condition is setted to false while timeout, the one who'll set that condition to false, is waiting while loop end to be executed.