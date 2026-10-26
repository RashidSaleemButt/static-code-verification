# Review Checklist

| Category | Result | Defect |
|---|---|---|
| initialization | Issue | `sum` in `averageAttack()` is not initialized, and several variables are used without validation or safe setup. |
| pointers | Issue | `findMonster()` may return `nullptr`, but the result is dereferenced without checking; `getMonsterLabel()` returns a reference to a local variable; `defeatMonster()` deletes an object and then uses it. |
| arrays/buffers | Issue | `spawnMonster()` does not check the array capacity, so more than `MAX_MONSTERS` entries can overflow the array. `readBoss()` writes into a fixed-size buffer without checking input length. |
| loops | Issue | `totalMonsterHealth()` loops to `<= monsterCount`, which reads past the valid range of the array. Loop bounds are not safe for all conditions. |
| arithmetic | Issue | `calculateDamage()` does integer division, which truncates the result; `averageAttack()` uses uninitialized data and divides by zero when no monsters exist. |
| central flow | Issue | `if (monsters[i]->id = id)` is an assignment, not a comparison; the function therefore always returns the first monster. `playerRank()` has no return value for some valid inputs. |
| function calls | Issue | `attackMonster()`, `getMonsterLabel()`, and `readBoss()` call functions assuming the monster exists; `readBoss()` also performs incorrect memory deletion (`delete` instead of `delete[]`). |
| classes | Issue | The class has a shallow-copy problem (`Game copy = game`), leaked memory (`bonus`), and the destructor does not handle pointer ownership safely. |
