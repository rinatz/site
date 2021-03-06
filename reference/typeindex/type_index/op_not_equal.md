#operator!=
* typeindex[meta header]
* std[meta namespace]
* type_index[meta class]
* class template[meta id-type]
* cpp11[meta cpp]

```cpp
bool operator!=(const type_index& rhs) const noexcept;
```

##概要
非等値の判定を行う


##戻り値
`*target != *rhs.target`

※`target`は、`type_index`のメンバ変数として保持されている`type_info`オブジェクトへのポインタ(説明用)


##例外
投げない


##例
```cpp
#include <cassert>
#include <typeindex>

int main()
{
  std::type_index t1 = typeid(int);
  std::type_index t2 = typeid(double);

  assert(t1 != t2);
  assert(t1 != typeid(double));
}
```
* assert[link /reference/cassert/assert.md]

###出力
```
```

##バージョン
###言語
- C++11

###処理系
- [GCC, C++11 mode](/implementation.md#gcc): 4.6.1

