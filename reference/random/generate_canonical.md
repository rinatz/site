#generate_canonical
* random[meta header]
* std[meta namespace]
* function template[meta id-type]
* cpp11[meta cpp]

```cpp
namespace std {
  template<class RealType, size_t bits, class URNG>
  RealType generate_canonical(URNG& g);
}
```

##概要
実数区間\[0.0,1.0\)に展開（事実上正規化）された一様分布乱数を得るための関数テンプレート。 
テンプレート引数に与える `RealType` 型について、 `bits` だけの分解能を持つ仮数部を `URNG g`を必要な回数だけ繰り返し呼び出して生成する。


##テンプレートパラメータ
- `class RealType` : 生成する実数の型。
- `size_t bits` : 生成する実数における仮数部への分解能の最低要求。最大値は `std::`[`numeric_limits`](/reference/limits/numeric_limits.md)`<RealType>::`[`digits`](/reference/limits/numeric_limits/digits.md) 。
- `class URNG` : 一様乱数生成器の型。

##関数パラメータ
- URNG& g : 一様乱数生成器。


##例外
`URNG g` が例外を送出する場合はそれに準ずる。


##例
```cpp
#include <random>
#include <iostream>
 
int main()
{
  std::default_random_engine g(123456789);
 
  for(auto n = 3; n; --n)
    std::cout
      << "g directly: "
      << g()
      << std::endl
      ;
 
  for(auto n = 3; n; --n)
    std::cout
      << "generate_canonical<float, std::numeric_limits<float>::digits>"
         " [std::numeric_limits<float>::digits = "
      << std::numeric_limits<float>::digits
      << "] "
      << std::generate_canonical<float, std::numeric_limits<float>::digits>(g)
      << std::endl
      ;
}
```


###出力
```
g directly: 469049721
g directly: 2053676357
g directly: 1781357515
generate_canonical<float, std::numeric_limits<float>::digits> [std::numeric_limits<float>::digits = 24] 0.561695
generate_canonical<float, std::numeric_limits<float>::digits> [std::numeric_limits<float>::digits = 24] 0.415307
generate_canonical<float, std::numeric_limits<float>::digits> [std::numeric_limits<float>::digits = 24] 0.0661187
```

##バージョン
###言語
- C++11

###処理系
- [Clang, C++11 mode](/implementation.md#clang): 3.0
- [GCC, C++11 mode](/implementation.md#gcc): 4.4
- [ICC](/implementation.md#icc): ??
- [Visual C++](/implementation.md#visual_cpp): ??

###備考
- GCC 4.9時点において、`float`型を指定した場合に、値`1.0`が生成されることがあるバグがある([Bug 63176](https://gcc.gnu.org/bugzilla/show_bug.cgi?id=63176))
- Clang 3.3時点において、値`1.0`が生成されることがある([Bug 18767](http://llvm.org/bugs/show_bug.cgi?id=18767))

###参考
- N3337 p.909 §26.5.7.2

