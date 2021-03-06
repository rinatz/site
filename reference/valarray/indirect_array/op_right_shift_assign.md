#operator>>=
* valarray[meta header]
* std[meta namespace]
* indirect_array[meta class]
* function[meta id-type]

```cpp
void operator>>=(const valarray<T>& xs) const;
```

##概要
右シフトの複合代入を行う。


##効果
元となる`valarray`オブジェクトから参照によって抽出した各要素を、`xs`の各要素の値だけ左シフトする。


##戻り値
なし


##備考
`valarray`から抽出した要素数と`xs`の要素数が異なる場合、その挙動は未定義。


##例
```cpp
#include <iostream>
#include <valarray>
#include <bitset>

int main()
{
  std::valarray<int> v = {
    0b01010001,
    0b10100000,
    0b01011000
  };

  std::valarray<std::size_t> mask = {0, 1, 2};

  std::indirect_array<int> result = v[mask];

  // 抽出した要素を4ビット右シフトする
  result >>= std::valarray<int>(4, mask.size());

  for (int x : v) {
    std::cout << std::bitset<8>(x).to_string() << std::endl;
  }
}
```

###出力
```
00000101
00001010
00000101
```


