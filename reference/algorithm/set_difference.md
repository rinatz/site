#set_difference
* algorithm[meta header]
* std[meta namespace]
* function template[meta id-type]

```cpp
namespace std {
  template <class InputIterator1, class InputIterator2, class OutputIterator>
  OutputIterator set_difference(InputIterator1 first1, InputIterator1 last1,
                                InputIterator2 first2, InputIterator2 last2,
                                OutputIterator result);

  template <class InputIterator1, class InputIterator2, class OutputIterator,
            class Compare>
  OutputIterator set_difference(InputIterator1 first1, InputIterator1 last1,
                                InputIterator2 first2, InputIterator2 last2,
                                OutputIterator result, Compare comp);
}
```

##概要
2つのソート済み範囲の差集合を得る


##要件
結果の範囲は両方の入力の範囲と重なっていてはならない。


##効果
`[first1,last1)` から、`[first2,last2)` に存在していない要素を `result` へコピーする。構築された範囲はソートされている。


##戻り値
構築された範囲の終端


##計算量
最大で `2 * ((last1 - first1) + (last2 - first2)) - 1` 回の比較を行う


##備考
`[first1,last1)` が `m` 個、`[first2,last2)` が `n` 個の等価な要素を含んでいる場合、`[first1,last1)` から最後の [`max`](max.md)`(m-n, 0)` 要素が出力の範囲へコピーされる。


##例
```cpp
#include <iostream>
#include <set>
#include <algorithm>
#include <iterator>

int main()
{
  std::multiset<int> a = {1, 2, 3, 4, 5, 6};
  std::multiset<int> b = {2, 3, 4};
  std::multiset<int> result;

  // a - bの差集合を作る
  std::set_difference(a.begin(), a.end(),
                      b.begin(), b.end(),
                      std::inserter(result, result.end()));

  std::for_each(result.begin(), result.end(), [](int x) {
    std::cout << x << std::endl;
  });
}
```
* std::set_difference[color ff0000]
* std::multiset[link /reference/set/multiset.md]
* begin()[link /reference/set/set/begin.md]
* end()[link /reference/set/set/end.md]
* std::inserter[link /reference/iterator/inserter.md]
* std::for_each[link for_each.md]
* std::cout[link /reference/iostream/cout.md]
* std::endl[link /reference/ostream/endl.md]

###出力
```
1
5
6
```


