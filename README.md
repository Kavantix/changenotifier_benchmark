# getx_benchmark

This benchmark may help us in finding a faster implementation for ChangeNotifier.

Result of running this on a phone of mine in Release Mode (flutter run --release -t lib/benchmark.dart):

```
┌───────────────────────────────────────────────────────────────────────────────────────────────────────────┐
│                                          ValueNotifier benchmark                                          │
├───────────────────────────────────┬───────────────────────────────────┬───────────────────────────────────┤
│           ValueNotifier           │           Value (GetX)            │        CleverValueNotifier        │
├─────────────┬─────────┬───────────┼─────────────┬─────────┬───────────┼─────────────┬─────────┬───────────┤
│  Listeners  │ Updates │ Time [µs] │  Listeners  │ Updates │ Time [µs] │  Listeners  │ Updates │ Time [µs] │
├─────────────┼─────────┼───────────┼─────────────┼─────────┼───────────┼─────────────┼─────────┼───────────┤
│             │      10 │         5 │             │      10 │         2 │             │      10 │         1 │
│             ├─────────┼───────────┤             ├─────────┼───────────┤             ├─────────┼───────────┤
│             │     100 │        16 │             │     100 │         4 │             │     100 │         2 │
│             ├─────────┼───────────┤             ├─────────┼───────────┤             ├─────────┼───────────┤
│           1 │    1000 │       419 │           1 │    1000 │        34 │           1 │    1000 │        24 │
│             ├─────────┼───────────┤             ├─────────┼───────────┤             ├─────────┼───────────┤
│             │   10000 │      1857 │             │   10000 │       354 │             │   10000 │       239 │
│             ├─────────┼───────────┤             ├─────────┼───────────┤             ├─────────┼───────────┤
│             │  100000 │     19115 │             │  100000 │      4386 │             │  100000 │      2402 │
├─────────────┼─────────┼───────────┼─────────────┼─────────┼───────────┼─────────────┼─────────┼───────────┤
│             │      10 │         7 │             │      10 │         1 │             │      10 │         1 │
│             ├─────────┼───────────┤             ├─────────┼───────────┤             ├─────────┼───────────┤
│             │     100 │        19 │             │     100 │         4 │             │     100 │         3 │
│             ├─────────┼───────────┤             ├─────────┼───────────┤             ├─────────┼───────────┤
│           2 │    1000 │       184 │           2 │    1000 │        44 │           2 │    1000 │        34 │
│             ├─────────┼───────────┤             ├─────────┼───────────┤             ├─────────┼───────────┤
│             │   10000 │      2500 │             │   10000 │       430 │             │   10000 │       348 │
│             ├─────────┼───────────┤             ├─────────┼───────────┤             ├─────────┼───────────┤
│             │  100000 │     24319 │             │  100000 │      4377 │             │  100000 │      3520 │
├─────────────┼─────────┼───────────┼─────────────┼─────────┼───────────┼─────────────┼─────────┼───────────┤
│             │      10 │         5 │             │      10 │         1 │             │      10 │         1 │
│             ├─────────┼───────────┤             ├─────────┼───────────┤             ├─────────┼───────────┤
│             │     100 │        29 │             │     100 │         6 │             │     100 │         6 │
│             ├─────────┼───────────┤             ├─────────┼───────────┤             ├─────────┼───────────┤
│           4 │    1000 │       298 │           4 │    1000 │        63 │           4 │    1000 │        56 │
│             ├─────────┼───────────┤             ├─────────┼───────────┤             ├─────────┼───────────┤
│             │   10000 │      2923 │             │   10000 │       625 │             │   10000 │       567 │
│             ├─────────┼───────────┤             ├─────────┼───────────┤             ├─────────┼───────────┤
│             │  100000 │     29993 │             │  100000 │      6248 │             │  100000 │      5611 │
├─────────────┼─────────┼───────────┼─────────────┼─────────┼───────────┼─────────────┼─────────┼───────────┤
│             │      10 │         8 │             │      10 │         2 │             │      10 │         1 │
│             ├─────────┼───────────┤             ├─────────┼───────────┤             ├─────────┼───────────┤
│             │     100 │        56 │             │     100 │        12 │             │     100 │        12 │
│             ├─────────┼───────────┤             ├─────────┼───────────┤             ├─────────┼───────────┤
│           8 │    1000 │       570 │           8 │    1000 │       119 │           8 │    1000 │       118 │
│             ├─────────┼───────────┤             ├─────────┼───────────┤             ├─────────┼───────────┤
│             │   10000 │      6118 │             │   10000 │      1196 │             │   10000 │      1353 │
│             ├─────────┼───────────┤             ├─────────┼───────────┤             ├─────────┼───────────┤
│             │  100000 │     58917 │             │  100000 │     18892 │             │  100000 │     12613 │
├─────────────┼─────────┼───────────┼─────────────┼─────────┼───────────┼─────────────┼─────────┼───────────┤
│             │      10 │        14 │             │      10 │         3 │             │      10 │         3 │
│             ├─────────┼───────────┤             ├─────────┼───────────┤             ├─────────┼───────────┤
│             │     100 │       105 │             │     100 │        20 │             │     100 │        22 │
│             ├─────────┼───────────┤             ├─────────┼───────────┤             ├─────────┼───────────┤
│          16 │    1000 │      1010 │          16 │    1000 │       195 │          16 │    1000 │       214 │
│             ├─────────┼───────────┤             ├─────────┼───────────┤             ├─────────┼───────────┤
│             │   10000 │     11177 │             │   10000 │      1971 │             │   10000 │      2169 │
│             ├─────────┼───────────┤             ├─────────┼───────────┤             ├─────────┼───────────┤
│             │  100000 │    101948 │             │  100000 │     19888 │             │  100000 │     21073 │
├─────────────┼─────────┼───────────┼─────────────┼─────────┼───────────┼─────────────┼─────────┼───────────┤
│             │      10 │        23 │             │      10 │         5 │             │      10 │         5 │
│             ├─────────┼───────────┤             ├─────────┼───────────┤             ├─────────┼───────────┤
│             │     100 │       181 │             │     100 │        36 │             │     100 │        39 │
│             ├─────────┼───────────┤             ├─────────┼───────────┤             ├─────────┼───────────┤
│          32 │    1000 │      1823 │          32 │    1000 │       349 │          32 │    1000 │       380 │
│             ├─────────┼───────────┤             ├─────────┼───────────┤             ├─────────┼───────────┤
│             │   10000 │     23565 │             │   10000 │      3506 │             │   10000 │      3804 │
│             ├─────────┼───────────┤             ├─────────┼───────────┤             ├─────────┼───────────┤
│             │  100000 │    215614 │             │  100000 │     35212 │             │  100000 │     38208 │
├─────────────┴─────────┴───────────┼─────────────┴─────────┴───────────┼─────────────┴─────────┴───────────┤
│ Total Time:                502818 │ Total Time:                 97985 │ Total Time:                 92829 │
└───────────────────────────────────┴───────────────────────────────────┴───────────────────────────────────┘
``