#tan
```cpp
namespace std {
  template <class T>
  valarray<T> tan(const valarray<T>& v);
}
```

##概要
正接（タンジェント：tangent）を得る。


##戻り値
以下のコードと同等のことを行う：

```cpp
return v.apply(static_cast<T(*)(T)>(std::tan));
```
* apply[link ./apply.md]
* sin[link /reference/cmath/tan.md]


##例
```cpp
#include <iostream>
#include <valarray>

int main()
{
  const std::valarray<float> v = {0.1, 0.2, 0.3};

  std::valarray<float> result = std::tan(v);
  for (float x : result) {
    std::cout << x << std::endl;
  }
}
```
* tan[color ff0000]

###出力
```
0.100335
0.20271
0.309336
```

