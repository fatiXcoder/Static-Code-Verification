
# Code Review Report

| Line / Function | Defect Type | Why It Is a Problem | Proposed Fix | Severity |
|---|---|---|---|---|
| `spawnMonster()` | Array Overflow | More than five monsters can exceed the array capacity. | Check `monsterCount < MAX_MONSTERS` before insertion. | High |
| `findMonster()` | Assignment Instead of Comparison | `monsters[i]->id = id` modifies the ID instead of comparing it. | Replace `=` with `==`. | High |
| `attackMonster()` | Null Pointer / Unsigned Arithmetic | A missing monster can cause a crash, and unsigned arithmetic makes the health check unreliable. | Check `m != nullptr`; use signed integers and validate damage. | Critical |
| `totalMonsterHealth()` | Out-of-Bounds Access | `i <= monsterCount` accesses an invalid array element. | Change the condition to `i < monsterCount`. | High |
| `getMonsterLabel()` | Dangling Reference | Returns a reference to a local string that is destroyed after the function returns. | Return `std::string` by value and check for a missing monster. | High |
| `averageAttack()` | Uninitialized Variable / Division by Zero | `sum` is uninitialized, and division by zero is possible when no monsters exist. | Initialize `sum = 0.0` and check `monsterCount > 0`. | High |
| `defeatMonster()` | Use-After-Free / Invalid Ownership | Accesses `m->name` after deleting the monster and does not remove its pointer from the array. | Print the name before deletion, remove the pointer, and update the count. | Critical |
| `playerRank()` | Missing Return | Scores of 100 or less do not return a value. | Add a final return statement. | Medium |
| `readBoss()` | Buffer Overflow / Incorrect Deallocation | Input may exceed the buffer, and `delete` is incorrect for memory allocated with `new[]`. | Use `std::string` or use `delete[]` for the allocated array. | High |
| `main()` | Memory Leak | The dynamically allocated `bonus` monster is never deleted. | Use a stack object or a smart pointer. | Medium |
| `Game` Copy Operation | Shallow Copy / Double Deletion | `Game copy = game` copies raw pointers, allowing both objects to delete the same monsters. | Implement deep copying or disable copying and use safe ownership. | Critical |
| `calculateDamage()` | Integer Arithmetic | Integer division discards fractional damage. | Use `attack * armorPercent / 100.0`. | Low |
