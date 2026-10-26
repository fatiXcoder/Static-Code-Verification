
# Review Checklist

| No. | Category | Result (Issue/OK) | Defect |
|---:|---|---|---|
| 1 | Initialization | Issue | `sum` is uninitialized in `averageAttack()`. |
| 2 | Pointers | Issue | Null pointer dereferencing in `attackMonster()`, `getMonsterLabel()`, and `defeatMonster()`. |
| 3 | Arrays / Buffers | Issue | `spawnMonster()` exceeds array capacity, and `readBoss()` may cause buffer overflow. |
| 4 | Loops | Issue | `totalMonsterHealth()` uses `i <= monsterCount`, causing out-of-bounds access. |
| 5 | Arithmetic | Issue | Unsigned damage comparison is incorrect, and integer division may produce unintended results. |
| 6 | Control Flow | Issue | `playerRank()` does not return a value for scores of 100 or less. |
| 7 | Function Calls | Issue | `findMonster()` uses assignment instead of comparison; `getMonsterLabel()` returns a reference to a local variable. |
| 8 | Memory Management | Issue | Memory leaks, incorrect deallocation, use-after-free, and shallow-copy ownership problems. |

## Conclusion

Static code inspection identified defects in initialization, pointers, arrays, loops, arithmetic, control flow, function calls, and memory management. These defects should be corrected before execution and testing.
