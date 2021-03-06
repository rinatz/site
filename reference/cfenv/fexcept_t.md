#fexcept_t
* cfenv[meta header]
* std[meta namespace]
* typedef[meta id-type]
* cpp11[meta cpp]

```cpp
namespace std {
  typedef implementation-defined fexcept_t;
}
```
* implementation-defined[italic]

##概要
実装が持つ浮動小数点例外の状態フラグを表す型。


##例
```cpp
// 標準C++の浮動小数点例外を、
// Visual C++での浮動小数点例外の形式に変換する
#include <iostream>
#include <cfenv>

int main()
{
  float a = 1.0f;
  float b = 0.0f;
  float result = a / b;

  std::fexcept_t excepts = 0;
  std::fegetexceptflag(&excepts, FE_ALL_EXCEPT);

  if (excepts & _SW_ZERODIVIDE)
  {
    std::cout << "zero divided" << std::endl;
  }
}
```
* fexcept_t[color ff0000]
* std::fegetexceptflag[link fegetexceptflag.md]
* FE_ALL_EXCEPT[link fe_all_except.md]

###出力例
```
zero divided
```


##バージョン
###言語
- C++11

###処理系
- [Clang, C++11 mode](/implementation.md#clang): 3.0
- [GCC, C++11 mode](/implementation.md#gcc): 4.3.0
- [ICC](/implementation.md#icc): ??
- [Visual C++](/implementation.md#visual_cpp): ??


