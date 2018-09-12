# Adaptive Radix Trie

## Usage

```cpp
#include <art.hpp>

using namespace art;

int main() {
  art<int> m;

  int v = 2;
  // set k to v
  m.set("k", &v);

  // get value of k
  int * v_ptr = m.get("k");

  // delete k
  m.del("k");

  return 0;
}
```

## Test

```cpp
# build test binaries
make [release]

# run tests
make test

# run benchmarks
make bench
```

## Benchmark results

#### read/write, real dataset, zipf distributed
```
===============================================================================
   Name (baseline is *)   |   Dim   |  Total ms |  ns/op  |Baseline| Ops/second
===============================================================================
              art_mixed * | 1048576 |  2211.614 |    2109 |      - |   474122.5
          red_black_mixed | 1048576 |  2370.996 |    2261 |  1.072 |   442251.2
            hashmap_mixed | 1048576 |  1198.802 |    1143 |  0.542 |   874686.7
===============================================================================
```

#### Insertion
```
===============================================================================
   Name (baseline is *)   |   Dim   |  Total ms |  ns/op  |Baseline| Ops/second
===============================================================================
      art_insert_sparse * | 1048576 |   662.458 |     631 |      - |  1582856.8
  red_black_insert_sparse | 1048576 |  1047.248 |     998 |  1.581 |  1001268.3
    hashmap_insert_sparse | 1048576 |   651.702 |     621 |  0.984 |  1608979.6
===============================================================================
```

#### Removal
```
===============================================================================
   Name (baseline is *)   |   Dim   |  Total ms |  ns/op  |Baseline| Ops/second
===============================================================================
      art_delete_sparse * | 1048576 |   556.471 |     530 |      - |  1884331.6
  red_black_delete_sparse | 1048576 |  1069.961 |    1020 |  1.923 |   980013.0
    hashmap_delete_sparse | 1048576 |   392.914 |     374 |  0.706 |  2668716.3
===============================================================================
```

## References

* [The Adaptive Radix Tree: ARTful Indexing for Main-Memory Databases](http://www-db.in.tum.de/~leis/papers/ART.pdf)
