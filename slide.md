# 最近の C++ 事情

([@pink_bangbi](https://twitter.com/pink_bangbi))  
2018/03/10


---

### 自己紹介
- - -

* なまえ  : おしょー（not 学生）
* Twitter : [@pink_bangbi](https://twitter.com/pink_bangbi)
* github  : [osyo-manga](https://github.com/osyo-manga)
* ブログ  : [Secret Garden(Instrumental)](http://secret-garden.hatenablog.com)
* C++ 関連
  * 10年以上やっていますが C++ 出来ない
  * 基本的に言語仕様を追ったり遊んだりしているだけで、あんまりものをつくったりはしていない
  * 最近は Ruby とか書いている

---

# おねがい
### プロ C++er の方は石を投げないでください

---

# 今回話す内容

---

# 最近の C++ 事情

---

### 内容

- - -

* C++ の歴史          <!-- .element: class="fragment" -->
* コンパイラ事情      <!-- .element: class="fragment" -->
* 最新の言語機能紹介(new!)  <!-- .element: class="fragment" -->

---

# C++ とは

---

### C++ とは
- - -

C言語の拡張として開発された言語  
クラス、仮想関数、多重継承、テンプレート、例外処理などの機能が追加された  
手続き型プログラミング・データ抽象・オブジェクト指向プログラミング・ジェネリックプログラミングなど、複数のプログラミングパラダイムを組み合わせている

---

# つまりすごい C言語
## C言語と C++ は
## Java と JavaScript ぐらい違う

---

#### C++ ってどこ使われているの
- - -

* グラフィック系        <!-- .element: class="fragment" -->
  * Vulkan/DirectX
  * Unreal Engine 4
* 競技プログラミング界隈        <!-- .element: class="fragment" -->
  * 速度重視されているので使われていることが多いみたい
* facebook        <!-- .element: class="fragment" -->
* その他速度がボトルネックとなる部分        <!-- .element: class="fragment" -->

---

# C++ の歴史

---

### C++ の歴史

- - -

* 1998年 : C++98 <!-- .element: class="fragment" -->
* 2003年 : C++03     <!-- .element: class="fragment" -->
  * C++ と言えばこれを指すことが多かった
* 2011年 : C++11                   <!-- .element: class="fragment" -->
  * 8年ぶりに改定され型推論やラムダ式など多数のモダンな機能が実装された
* 2014年 : C++14                    <!-- .element: class="fragment" -->
* 2017年 : C++17 現行のバージョン  <!-- .element: class="fragment" -->
* 2020年 : C++20 リリース予定      <!-- .element: class="fragment" -->

3年周期に次のバージョンが策定されている  <!-- .element: class="fragment" -->

---

# コンパイラ事情

---

### コンパイラ事情

- - -

C++ はまず、言語仕様（規格）があり、それを元にしていくつかの処理系(コンパイラ)が実装されている  
C++ を使用する場合はこのコンパイラを使用してコードから実行ファイルにコンパイルして使う  
各処理系やバージョンによって実装されている言語機能が違うので注意する必要がある

---

#### 代表的なコンパイラ

- - -

* GCC(最新版 v7.3)                   <!-- .element: class="fragment" -->
  * GNUコンパイラコレクション
  * 最新版では C++17 までの言語仕様を実装済み
* MSVC(Visual Studio 2017 15.4)      <!-- .element: class="fragment" -->
  * 最新版 C++14 の言語仕様は実装済み
  * C++11 と C++17 まだ実装中
* Clang(最新版 v6.0.0)               <!-- .element: class="fragment" -->
  * LLVM の一部として開発されている
  * 最新版では C++17 までの言語仕様を実装済み

詳しくは ↓ ↓ ↓                    <!-- .element: class="fragment" -->

>>>

## 各処理系の言語仕様対応状況

>>>

## GCC(最新版 v7.3)

- - -

* C++11 -std=c++11 オプション
  * 4.8.1 にて実装完了
* C++14 -std=c++14 オプション
  * 5.1 にて実装完了
* C++17 -std=c++1z オプション
  * 7.1 にて現行の言語仕様の実装を完了
* 各言語仕様を使用する場合は `-std=c++14` オプション等を使用する必要がある

>>>

## Clang(最新版 v6.0.0)

- - -

* C++11 -std=c++11 オプション
  * 3.3 にて実装完了
* C++14 -std=c++14 オプション
  * 3.4 にて実装完了
* C++17 -std=c++17 オプション
  * 5.0.0 にて現行の言語仕様の実装を完了
* C++20
  * 6.0 にて開発中
* 各言語仕様を使用する場合は `-std=c++17` オプション等を使用する必要がある

>>>

## MSVC(Visual Studio 2017 15.5)

- - -

* C++11
  * Visual Studio 2015 にてだいたい実装済み
  * 最新版でも全ての機能は未対応
* C++14
  * Visual Studio 2017 にて実装完了
* C++17
  * Visual Studio 2015 から対応開始
  * Visual Studio 2017 15.5 にて対応中

>>>

MSVC はバージョンによって実装している機能がバラバラなので正直 よくわからん！！

>>>

C++ の最新の言語機能を使いたい場合は
処理系やバージョンによって使用できる機能が異なるので事前に調べてください

---


# 最新の言語機能紹介
---

## 拡張・追加されたキーワード

---

### [nullptr(C++11)](https://cpprefjp.github.io/lang/cpp11/nullptr.html)
- - -

`NULL` の代わりに `nullptr` というキーワードが追加

```cpp
// C++03
int* p = NULL;

// C++11
int* p2 = nullptr;

int a = 42;
// NULL は 0 として定義されているのでこういう比較ができてしまう
if( a == NULL ){ /* ... */ }

// nullptr はポインタ型でのみ比較するのでこれはエラーになる
if( a == nullptr ){ /* ... */ }
```

---

## [constexpr(C++11,14)](https://cpprefjp.github.io/lang/cpp11/constexpr.html)
- - -
コンパイル時に実行される事を明示化する

```cpp
// この関数をコンパイル時に実行する事が出来る
// C++11 では関数が return 文のみという制限があった
constexpr int
factorial(int n){
	return n == 1 ? 1 : n * factorial(n - 1);
}

// コンパイル時に処理される assert
static_assert(factorial(5) == 120);
```

>>>

C++14 では制限が緩和され for 文なども書けるように

```cpp
constexpr int
factorial(int n){
	int sum = 1;
	for(int i = 1 ; i <= n ; ++i){
		sum *= i;
	}
	return sum;
}

static_assert(factorial(5) == 120, "");
```

---

# 型推論

C++11 以降では `auto` というキーワードを使用して型を推論する事が出来る

---

### [変数定義(C++11)](https://cpprefjp.github.io/lang/cpp11/auto.html)
- - -
C++11 では変数定義時に右辺値から型を推論して変数型を定義することが出来る

```cpp
// 右辺値から型を推論して定義する
// この場合 n は int 型になる
auto n = 42;

// c は char 型
auto c = 'X';

// 右辺値から型を推論するのでこういう書き方は出来ない
auto m;		// Error

std::vector<int> v;
// このように長い型を定義する場合に便利
// std::vector<int>::iterator it = v.begin();
auto it = v.begin();
```

---

### [戻り値型(C++14)](https://cpprefjp.github.io/lang/cpp14/return_type_deduction_for_normal_functions.html)
- - -
C++14 では戻り値型を推論することも出来る

```cpp
auto
range1_5(){
	std::vector<int> result{1, 2, 3, 4, 5};
	return result;
}


template<typename T, typename U>
auto
plus(T a, U b){
	return a + b;
}
assert(plus(1, 2) == 3);
assert(plus(std::string("homu"), "mami") == "homumami");
```

---

# 言語機能

---


### [非静的メンバ変数の初期化(C++11)](https://cpprefjp.github.io/lang/cpp11/non_static_data_member_initializers.html)
- - -

非静的メンバ変数の定義時に初期値を設定できる

```cpp
struct person{
    // メンバ変数の定義時に初期値が設定できる
    std::string name = "homu";
    int age = 14;
};

person p;

assert(p.name == "homu");
assert(p.age  == 14);
```

---

### [初期化リスト(C++11)](https://cpprefjp.github.io/lang/cpp11/initializer_lists.html)
- - -

波括弧`{}` によりリストを初期化する事が出来る

```cpp
// 従来の配列の初期化
int array[] = {1, 2, 3, 4, 5};

// C++03 以前では1つずつ v.push(1); する必要があったが
// C++11 では配列と同じような感じで初期化することができる
std::vector<int> v = {1, 2, 3, 4, 5};

// std::map もこんな感じで初期化できる
std::map<int, std::string> table = {
    {1, "homu"},
    {2, "mami"},
    {3, "mado"},
};
```

---

#### [クラステンプレートのテンプレート引数推論(C++17)](https://cpprefjp.github.io/lang/cpp17/type_deduction_for_class_templates.html)
- - -

クラステンプレート引数をコンストラクタに渡す型から推論する事が出来る

```cpp
// C++03 以前
std::vector<int> v = {1, 2, 3, 4, 5};
std::pair<int, char> data = {42, 'c'};

// C++17 からは引数から推論出来るようになった
std::vector v2 = {1, 2, 3, 4, 5};
std::pair data2 = {42, 'c'};
```

---

### [ラムダ式(C++11)](https://cpprefjp.github.io/lang/cpp11/lambda_expressions.html)
- - -

無名関数を定義するための構文が新しく追加された

```cpp
// [キャプチャする変数](引数型) -> 戻り値型 { 関数の中身 }
auto plus = [](int a, int b) -> int {
	return a + b;
};

// 関数と同じように呼び出すことが出来る
assert(plus(1, 2) == 3);

int n = 3;
// ラムダ式内で外部の変数を使用する場合は
// 明示的に定義する
auto plus3 = [n](int m){
	return n + m;
}
assert(plus3(2) == 5);
```

>>>

```cpp
// クロージャっぽいもの
// キャプチャした変数を書き換える場合は mutable を追記する
int count = 0;
auto counter = [count]() mutable -> int {
	return count++;
};

assert(counter() == 0);
assert(counter() == 1);
assert(counter() == 2);


std::vector<int> v = {1, 2, 3, 4, 5};
// 関数に直接渡すことも出来る
std::for_each(v.begin(), v.end(), [](int n){
	std::cout << n << std::endl;
});
```

---

### [ジェネリックラムダ(C++14)](https://cpprefjp.github.io/lang/cpp14/generic_lambdas.html)
- - -

C++14 では引数に `auto` を使って型推論出来るように

```cpp
// 引数型を auto にすることで型推論される
// 戻り値型も省略可能（戻り値型の省略は C++11 でも一部可能）
auto plus = [](auto a, auto b){
    return a + b;
};

assert(plus(1, 2) == 3);
assert(plus("homu"s, "mami") == "homumami");
```

---

### [範囲for文(C++11)](https://cpprefjp.github.io/lang/cpp11/range_based_for.html)
- - -

配列やコンテナに対して for 文をかけるようになった

```cpp
int xs[] = {1, 2, 3, 4, 5};
// for( 変数定義 : コンテナ（配列） )
for(auto x : xs){
	// ...
}

// std::vector なんかも回せる
std::vector<int> v{1, 2, 3, 4, 5};
for(auto n : v){
	// ...
}
```

---

### [型エイリアス(C++11)](https://cpprefjp.github.io/lang/cpp11/alias_templates.html)

`using` を使用して型エイリアスを定義することが出来る

```cpp
// C++03 時代は typedef を使用していた
typedef int age_type;
typedef int (*func_type)(int, char);

// using を使用することでより直感的に定義できる
using age_type = int;
using func_type = int (*)(int, char);


// テンプレート引数を受け取ることも出来る
template<typename T>
using hash = std::map<std::string, T>;
```

---

### [構造化束縛(C++17)](https://cpprefjp.github.io/lang/cpp17/structured_bindings.html)
- - -
特定の型を分解して各要素を取り出す事が出来る

```cpp
std::pair<std::string, int> homu{ "homu", 14 };
// std::pair を分解してそれぞれの変数に代入できる
// auto を使用することで
// name は std::string 型
// age  は int 型
// と推論して定義できる
auto [name, age] = homu();
```

>>>

```cpp
std::vector<std::tuple<int, std::string, int>> vc = {
    { 1, "homu", 14 },
    { 2, "mami", 15 },
    { 3, "mado", 14 }
};

// 変数を定義する部分で std::tuple を分割して値を受け取ることが出来る
for(auto [id, name, age] : vc){
    std::cout << "id:"   << id   << ", "
              << "name:" << name << ", "
              << "age:"  << age  << std::endl;
}
```

---

# 標準ライブラリ

---

## [std::stringリテラル(C++14)](https://cpprefjp.github.io/reference/string/basic_string/op_s.html)
- - -

文字列を `std::string` として定義するためのリテラルライブラリが追加された。

```cpp
#include <string>

// s リテラルを使うための宣言
using namespace std::literals::string_literals;

// 文字列に s リテラルを追加することで
// std::string として扱われる
// str は std::string 型
auto str = "homu"s;

assert(str + str == "homuhomu");
```

---

#### その他いろいろ
- - -

* 固定長配列ライブラリ `<array>(C++11)`
* スマートポインタ `<memory>` (C++11)
* スレッドライブラリ `<thread>`(C++11)
* 乱数ライブラリ `<random>`(C++11)
* 時間ユーティリティライブラリ `<chrono>`(C++11)
* 正規表現ライブラリ `<regex>`(C++11)
* ファイルシステムライブラリ `<filesystem>`(C++17)
* 無効値を表現するライブラリ `<optional>`(C++17)
* 型安全な共用体ライブラリ `<variant>`(C++17)

---

### 他にも…
- - -

* decltype で式から型を取得する(C++11)
* 可変長テンプレート引数型(C++11)
* 右辺値参照とムーブセマンティクス(C++11)
* `constexpr` ラムダ式(C++17)
* `if constexpr` 文(C++17)
* etc...

---

# まとめ

---

### まとめ

- - -

* C++ はいまも進化し続けている          <!-- .element: class="fragment" -->
* C++ を使うときはどのコンパイラのどのバージョンなのか確認する          <!-- .element: class="fragment" -->
* C++03 の時に比べて言語仕様は増えているが格段に書きやすくなっている          <!-- .element: class="fragment" -->
* 今回は言語仕様しか紹介できなかったが標準ライブラリも強化されているので気になる人は調べてみるとよい          <!-- .element: class="fragment" -->

---

# C++ は趣味でやると
# とても楽しいので
# みんなやろう!!

---

# 便利サイト

* [Wandbox](https://wandbox.org/)
  * オンラインでコードが実行できるサイト
* [cpprefjp - C++日本語リファレンス](https://cpprefjp.github.io/)
  * 日本語で最新の C++ 情報がまとまってる
* [cppreference.com](http://en.cppreference.com/w/)
  * 英語のリファレンスサイト

---

## ご清聴
## ありがとうございました
