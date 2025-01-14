Windowsの場合にはWSL2上のUbuntuを用いることを推奨．
この研修の[GitHubリポジトリ](https://github.com/ykinolab-tokai/initial-training)をforkしておく．

# 第1章: 基本操作
1. `q01.txt`という名前のテキストファイルを作成せよ（中身は自由）．
1. `q02.txt`という名前のテキストファイルに，絶対パスと相対パスについての説明を記述せよ．
1. `q03.txt`という名前のテキストファイルに，`pwd`コマンドについての説明を記述せよ．
1. `q04.txt`という名前のテキストファイルに，ホームディレクトリについての説明を記述せよ．
1. `q05.txt`という名前のテキストファイルに，`ls`コマンドについての説明を記述せよ．
1. `q06.txt`という名前のテキストファイルに，`cd`コマンドについての説明を記述せよ．
1. `q07.txt`という名前のテキストファイルに，`mkdir`コマンドについての説明を記述せよ．
1. `q08.txt`という名前のテキストファイルに，`cat`コマンドについての説明を記述せよ．

# 第2章: Python
1. Python には2章で紹介した以外にも数多くの組み込み関数が定義されています。組み込み関数を適切に使うことでコードを簡潔に記せます。`a=[4, 8, 3, 4, 1]` というリストに対して以下の操作を行う組み込み関数を[公式ドキュメント](https://docs.python.org/ja/3/library/functions.html)からそれぞれ探し、適用して下さい。すなわち、以下のコードセル中の `FUNC` の部分を適切な組み込み関数に置き換えてください。

    - リスト `a` の長さを求める。
    - リスト `a` に含まれる値の最大値を求める。
    - リスト `a` に含まれる値の最小値を求める。
    - リスト `a` に含まれる値の合計値を求める。
    - リスト `a` をソートして、`[1, 3, 4, 4, 8]` というリストを返す。

    ```python
    # 以下の FUNC という部分を組み込み関数に置き換えてください

    a = [4, 8, 3, 4, 1]
    res = FUNC(a)
    print(res)
    ```
1. 以下の演算や関数をそれぞれ評価したとき、結果の値と型が何になるか予想してください。実際にコードを実行して、結果が予想と合うか確かめてください。型の確認には `type()` 関数を使用しましょう。

    - `1.2 + 3.8`
    - `10 // 100`
    - `1 >= 0`
    - `'Hello World' == 'Hello World'`
    - `not 'Chainer' != 'Tutorial'`
    - `all([True, True, False])`  (`all` の定義は[公式ドキュメントを参照](https://docs.python.org/ja/3/library/functions.html#all))
    - `any([True, True, False])`  (`any` の定義は[公式ドキュメントを参照](https://docs.python.org/ja/3/library/functions.html#any))
    - `abs(-3)`  (`abs` の定義は[公式ドキュメントを参照](https://docs.python.org/ja/3/library/functions.html#abs))
    - `2 // 0`
1. 機械学習では大量のデータを扱うことが多いため、リストの扱いに慣れておくと便利なことが多いです。
`a=[4, 8, 3, 4, 1]` というリストに対して以下の操作を行うコードを書いて下さい。

    - リスト `a` の先頭の要素を取り除いて、`[8, 3, 4, 1]` となるようにして下さい。
    - リスト `a` の末尾の要素を取り除いて、`[4, 8, 3, 4]` となるようにして下さい。
    - リスト `a` の末尾に `100` という値を追加して、`[4, 8, 3, 4, 1, 100]` となるようにして下さい。

1. **リスト内包表記**はリストを生成するための簡潔な手段です。例えば、平方数のリスト `[0, 1, 4, 9, 16, ...]` を構成したいとき、
    ```python
    squares = []
    for x in range(10):
        squares.append(x ** 2)
    ```
    と書く代わりに、
    ```python
    squares = [x ** 2 for x in range(10)]
    ```
    と書くことができます。リスト内包表記は一般に `[(式) for (変数) in (iterableオブジェクト)]` という構文を取ります。リスト内包表記の一般的な説明は[公式ドキュメント](https://docs.python.org/ja/3/tutorial/datastructures.html#list-comprehensions)を参照して下さい。リスト内包表記で `in` の後に続く iterable オブジェクトは `range` である必要はなく、例えばリストを指定できます。

    ```python
    a = [4, 8, 3, 4, 1]
    squares = [x ** 2 for x in a]
    print(squares)  # => [16, 64, 9, 16, 1]
    ```

    以下の問いに答えて下さい。

    (1) `a=[4, 8, 3, 4, 1]` というリストに対し、要素が偶数なら `0`, 奇数なら `1` に変換するコードをリスト内包表記を用いて書いて下さい。この結果、このリストは `[0, 0, 1, 0, 1]` に変換されるべきです。

    (2) (1) で書いたコードと組み込み関数を組み合わせて、リスト `a` に含まれる奇数の個数を数えるコードを書いて下さい。

    (3) リスト内包表記では、`if` 文を用いることで条件を満たす要素だけをリストに残すことができます。例えば
    ```python
    b = [x for x in range(10) if x > 5]
    ```
    と記すと、`b` は要素が `5` より大きいもののみが残り `[6, 7, 8, 9]` となります。

    リスト内包表記を使ってリスト `a` から奇数の要素だけを残すコードを書いて下さい。
1. Python では文字列型に対して便利な組み込み関数が多数定義されています([公式のドキュメント](https://docs.python.org/ja/3/library/stdtypes.html#text-sequence-type-str))。組み込み関数を使って以下の処理を行って下さい。

    (1) [str.join()](https://docs.python.org/ja/3/library/stdtypes.html#str.join) を使って、`0` から `99` までの数をスペース区切りで並べた文字列 `"0 1 2 3 4 ... 99"` を構成して下さい。

    (2) [str.format()](https://docs.python.org/ja/3/library/stdtypes.html#str.format) を使って `float` の値 `(1.0 / 7.0)` の小数点以下9桁までを表示して下さい。
1. クラスを実装する練習として、データを管理するクラスを実装してみましょう。
次のメソッドを全て持つクラス `DataManager` を記述して下さい。

    * `__init__(self, x, y, z)`: 3つの数 `x`, `y`, `z` をコンストラクタで受け取り、インスタンスの属性でそれぞれの値を記憶する。
    * `add_x(self, delta)`: `x` に `delta` だけ足して、値を更新する。
    * `add_y(self, delta)`: `y` に `delta` だけ足して、値を更新する。
    * `add_z(self, delta)`: `z` に `delta` だけ足して、値を更新する。
    * `sum(self)`: `x`, `y`, `z` の3つの数の合計値を返す。

    このクラスを使って以下のようなコードが書けるものとします。

    ```python
    data_manager = DataManager(2, 3, 5)
    print(data_manager.sum())  # => 10
    data_manager.add_x(4)      # => data_manager.x の値が 2 から 6 に更新される
    print(data_manager.sum())  # => 14
    data_manager.add_y(0)      # => data_manager.y の値が 3 から 3 に更新される
    print(data_manager.sum())  # => 14
    data_manager.add_z(-9)     # => data_manager.z の値が 5 から -4 に更新される
    print(data_manager.sum())  # => 5
    ```
1. 以下で定義される関数 `f`, `g` があるとします。

    ```python
    def f(a):
        a = [6, 7, 8]
    
    def g(a):
        a.append(1)
    ```

    これらに対し、次のコードの実行結果がどうなるか予想して下さい。実際にコードを実行して予想と一致しているか確認し、なぜそのような結果になったのか説明して下さい。

    ```python
    def somefunction():
        a0 = [1, 2, 3]
        f(a0)
        print(a0)

        a1 = [1, 2, 3]
        g(a1)
        print(a1)
    
    somefunction()
    ```
1. 2以上の整数 `p` が素数であるとは、「どんな `2` 以上 `p-1` 以下の整数 `k` に対しても `p` は `k` で割り切れない」が成り立つことを指します。素数を小さい順から列挙すると、`2`, `3`, `5`, `7`, `11`, `13`, `17`, ... となります。
チュートリアルで学んだ制御構文である `if` や `for` を用いて、`2` から `100` からまでに含まれる素数を列挙して下さい。

# 第3章: NumPy, Matplotlibと数学の基本

# 第4章: 微積分の基礎
ここからは、紙と鉛筆を用意してください。

### 問4.1 (導関数)
1. 導関数の定義 $f'(x) = \lim_{h \rightarrow 0} \frac{f(x+h)-f(x)}{h}$ を用いて以下の関数 $f_1(x), f_2(x)$ の導関数 $f^{'}_1(x), f^{'}_2(x)$ をそれぞれ求めて下さい。

    * $f_1(x) = x^3$.
    * $f_2(x) = \sqrt{x}$. (ヒント: 分母と分子に $(\sqrt{x+h}+\sqrt{x})$ を掛けて式を整理してみて下さい)

1. 微分の線形性 $\left( cf(x) \right)^{'} = c f'(x)$, $\left( f(x) + g(x) \right)^{'} = f^{'}(x) + g^{'}(x)$ を用いて、以下の関数の導関数を求めて下さい。

    * $f_1(x) = 2x^2-5x+1$
    * $f_2(x) = \sum_{k=1}^{123} (k^2+1)x^k$

1. 積の微分 $\bigl( f(x) \cdot g(x) \bigr)^{'} = f^{'}(x)g(x) + f(x)g^{'}(x)$ を使って以下の関数を微分して下さい。

    * $f_1(x) = x \cdot x$.
    * $f_2(x) = x \cdot x^2$.
    * $f_3(x) = x \cdot x^3$.

    これを繰り返していくと、$g(x) = x^{100}$ に対して $g^{'}(x) = 100x^{99}$ などが成り立つことを確かめて下さい。

1. 合成関数の微分則 $\frac{d}{dx} f(g(x)) = \frac{df(u)}{du}\frac{du}{dx}$ ($u=g(x)$) を使って以下の関数を微分して下さい。

    * $f_1(x) = (x+1)^3$.
    * $f_2(x) = (4x)^3$.
    * $f_3(x) = \exp(2x-1)$.
    * $f_4(x) = \exp(-x^2)$.
    * $f_5(x) = 2^x$.  (ヒント: $2^x = \exp(\log(2) x)$ を利用しましょう)

1. $f(x) = x^2 + 1$, $g(x) = f(f(x))$ とします。

    (1) $g(x) = x^4 + 2x^2 + 2$ となることを確認して下さい。また、これより $g'(x) = 4x^3 + 4x$ となることを確認して下さい。

    (2) 一方で、合成関数の微分則によって $g'(x)$ を計算し、(1) で求めた導関数と一致することを確認して下さい。

    (3) $h(x) = f(f(f(x)))$ とします。合成関数の微分によって $h'(x)$ を計算して下さい。(ヒント: $h(x)=f(g(x))$ であることを利用しましょう)

1. 指数関数 $\exp(x)$ と対数関数 $\log(x)$ の導関数は以下で定まります。

    $$
    \begin{align}
    \exp^{'}(x) &= \exp(x). \\
    \log^{'}(x) &= \frac{1}{x}. \\
    \end{align}
    $$

    このことをプログラムを用いた実験によって確認してみましょう。
    **数値微分**は導関数を近似的に計算する手法です。導関数の定義

    $$f^{'}(x) = \lim_{h \rightarrow 0} \frac{f(x+h)-f(x)}{h}$$

    において、極限を取る代わりにある微小な値 $\Delta h$ を $h$ に代入し、

    $$
    f'(x) \approx \frac{f(x+\Delta h)-f(x)}{\Delta h}
    $$

    として計算することによって導関数の値を近似する方法が数値微分です。具体的な $x$ の値に対する $\exp(x)$ の微分を数値微分によって計算するコードは以下のようになります。

    ```python
    import math  # exp を呼び出すために math モジュールをインポート

    def f(x):
        return math.exp(x)

    def dfdx_approx(x):
        dh = 0.0001
        return (f(x + dh) - f(x)) / dh
    ```

    (1) `x=-3,-2,-1,0,1,2,3` に対して数値微分の関数 `dfdx_approx` を呼び出し、その結果得られた値と正確な微分の値($\exp^{'}(-3),\ldots,\exp^{'}(3)$)とを比較して下さい。

    (2) 対数関数 $\log(x)$ についても同様の実験を行い、`x=0.25,0.5,1,2,4,8` に対して比較して下さい。Python から対数関数を呼び出す場合、`math.log` を使用しましょう。

1. ニューラルネットワークのモデルでよく扱われる関数の導関数を計算してみましょう。

    * $\mathrm{ReLU}(x) = \max(x, 0)$.
    * $\tanh(x) = \frac{e^x - e^{-x}}{e^x + e^{-x}}$.  (注意: 商の微分則 $\bigl(\frac{f(x)}{g(x)}\bigr)^{'}=\frac{f^{'}(x)g(x)-f(x)g^{'}(x)}{g(x)^2}$ を用いましょう)
    * $\mathrm{Sigmoid}(x) = \frac{1}{1 + e^{-x}}$.
    * $\mathrm{Softplus}(x) = \log(1+e^x)$.

1. 
    (1) 2変数関数 $f(x, y) = |x| + |y|$ に対して偏微分 $\frac{\partial}{\partial x}f(x,y)$, $\frac{\partial}{\partial y}f(x,y)$ を求めて下さい。

    (2) 2変数関数 $f(x, y) = |x + y|$ に対して偏微分 $\frac{\partial}{\partial x}f(x,y)$, $\frac{\partial}{\partial y}f(x,y)$ を求めて下さい。

# 第5章: 複素数

# 第6章: 線形代数の基礎
1. Python コード上でベクトルや行列に関する演算を行うことを考えてみましょう。ベクトルは `float` のリスト、行列は `float` のリストのリストによって表すことができます。例えば、

    $$
    {\bf x}=\begin{bmatrix}
    3 \\
    7 \\
    2
    \end{bmatrix}, \
    {\bf A}=\begin{bmatrix}
    1 & 2 & 3 \\
    4 & 5 & 6
    \end{bmatrix}
    $$

    というベクトルと行列はそれぞれ `[3, 7, 2]` と `[[1, 2, 3], [4, 5, 6]]` と Python コード上で表すことができます。

    (1) 2つのベクトル ${\bf x}$, ${\bf y}$ を受け取り、その和 ${\bf x} + {\bf y}$ を返す関数を書いて下さい。コードは例えば以下のようになります。

    ```python
    def vector_sum(x, y):
        # ...

    x = [1, 2, 3]
    y = [8, 1, 2]
    answer = vector_sum(x, y)
    print(answer)  # => [9, 3, 5]
    ```

    (2) 2つの行列 ${\bf X}$, ${\bf Y}$ を受け取り、その和 ${\bf X} + {\bf Y}$ を返す関数を書いて下さい。コードは例えば以下のようになります。

    ```python
    def matrix_sum(X, Y):
        # ...

    X = [[1, 2, 3],
        [4, 5, 6]]
    Y = [[8, 1, 2],
        [-1, 0, -2]]
    answer = matrix_sum(X, Y)
    print(answer)  # => [[9, 3, 5], [3, 5, 4]]
    ```

    (3) 行列 ${\bf X}$ とベクトル ${\bf y}$ を受け取り、その積 ${\bf X}{\bf y}$ を返す関数を書いて下さい。

    ```python
    def matrix_vector_product(X, y):
        # ...

    X = [[1, 2, 3],
        [4, 5, 6]]
    y = [8, 1, 2]
    answer = matrix_vector_product(X, y)
    print(answer)  # => [16, 49]
    ```

    (4) 2つの行列 ${\bf X}$, ${\bf Y}$ を受け取り、その積 ${\bf X}{\bf Y}$ を返す関数を書いて下さい。

    ```python
    def matrix_product(X, Y):
        # ...

    X = [[1, 2, 3],
        [4, 5, 6]]
    Y = [[8, 1],
        [-1, 0],
        [0, 1]]
    answer = matrix_product(X, Y)
    print(answer)  # => [[6, 4], [27, 10]]
    ```

    (5) 行列 ${\bf X}$ を受け取り、その転置 ${\bf X}^{\rm T}$ を返す関数を書いて下さい。

    ```python
    def matrix_transpose(X):
        # ...

    X = [[1, 2, 3],
        [4, 5, 6]]
    answer = matrix_transpose(X)
    print(answer)  # => [[1, 4], [2, 5], [3, 6]]
    ```

1. Python コード上でベクトルや行列に関する演算を行うことを考えてみましょう。ベクトルは `float` のリスト、行列は `float` のリストのリストによって表すことができます。例えば、

    $$
    {\bf x}=\begin{bmatrix}
    3 \\
    7 \\
    2
    \end{bmatrix}, \
    {\bf A}=\begin{bmatrix}
    1 & 2 & 3 \\
    4 & 5 & 6
    \end{bmatrix}
    $$

    というベクトルと行列はそれぞれ `[3, 7, 2]` と `[[1, 2, 3], [4, 5, 6]]` と Python コード上で表すことができます。

    (1) 2つのベクトル ${\bf x}$, ${\bf y}$ を受け取り、その和 ${\bf x} + {\bf y}$ を返す関数を書いて下さい。コードは例えば以下のようになります。

    ```python
    def vector_sum(x, y):
        # ...

    x = [1, 2, 3]
    y = [8, 1, 2]
    answer = vector_sum(x, y)
    print(answer)  # => [9, 3, 5]
    ```

    (2) 2つの行列 ${\bf X}$, ${\bf Y}$ を受け取り、その和 ${\bf X} + {\bf Y}$ を返す関数を書いて下さい。コードは例えば以下のようになります。

    ```python
    def matrix_sum(X, Y):
        # ...

    X = [[1, 2, 3],
        [4, 5, 6]]
    Y = [[8, 1, 2],
        [-1, 0, -2]]
    answer = matrix_sum(X, Y)
    print(answer)  # => [[9, 3, 5], [3, 5, 4]]
    ```

    (3) 行列 ${\bf X}$ とベクトル ${\bf y}$ を受け取り、その積 ${\bf X}{\bf y}$ を返す関数を書いて下さい。

    ```python
    def matrix_vector_product(X, y):
        # ...

    X = [[1, 2, 3],
        [4, 5, 6]]
    y = [8, 1, 2]
    answer = matrix_vector_product(X, y)
    print(answer)  # => [16, 49]
    ```

    (4) 2つの行列 ${\bf X}$, ${\bf Y}$ を受け取り、その積 ${\bf X}{\bf Y}$ を返す関数を書いて下さい。

    ```python
    def matrix_product(X, Y):
        # ...

    X = [[1, 2, 3],
        [4, 5, 6]]
    Y = [[8, 1],
        [-1, 0],
        [0, 1]]
    answer = matrix_product(X, Y)
    print(answer)  # => [[6, 4], [27, 10]]
    ```

    (5) 行列 ${\bf X}$ を受け取り、その転置 ${\bf X}^{\rm T}$ を返す関数を書いて下さい。

    ```python
    def matrix_transpose(X):
        # ...

    X = [[1, 2, 3],
        [4, 5, 6]]
    answer = matrix_transpose(X)
    print(answer)  # => [[1, 4], [2, 5], [3, 6]]
    ```

1. ${\bf x}$ を次元数 $n$ のベクトル、${\bf A}$ を $n \times n$ の正方行列とします。

    $$
    {\bf x}=\begin{bmatrix}
    x_{1} \\
    \vdots \\
    x_{n}
    \end{bmatrix}, \
    {\bf A}=\begin{bmatrix}
    a_{11} & \ldots & a_{1n} \\
    \vdots &        & \vdots \\
    a_{n1} & \ldots & a_{nn}
    \end{bmatrix}
    $$


    二次形式に関する微分 $\frac{\partial}{\partial {\bf x}} \left( {\bf x}^{\rm T}{\bf A}{\bf x} \right) = {\bf x}^{\rm T} \left( {\bf A} + {\bf A}^{\rm T} \right)$ を証明してみましょう。

    (1) ${\bf x}^{\rm T}{\bf A}{\bf x} = \sum_{i=1}^n \sum_{j=1}^n a_{ij} x_i x_j$ であることを示して下さい。さらに、これより以下を示して下さい。
    $$
    {\bf x}^{\rm T}{\bf A}{\bf x} = a_{11} x_1^2 + \left( \sum_{i=2}^n (a_{1i} + a_{i1}) x_i \right) x_1 + \sum_{i=2}^n \sum_{j=2}^n x_i x_j a_{ij}.
    $$

    (2) 偏微分 $\frac{\partial}{\partial x_1} \left( {\bf x}^{\rm T}{\bf A}{\bf x} \right)$ を計算し、$\sum_{i=1}^n (a_{1i} x_i + a_{i1} x_i)$ となることを示して下さい。

    (3) 一般に、$k=1,\ldots,n$ に対して $\frac{\partial}{\partial x_k} \left( {\bf x}^{\rm T}{\bf A}{\bf x} \right) = \sum_{i=1}^n (a_{ki} x_i + a_{ik} x_i)$ となることを示して下さい。これによって $\frac{\partial}{\partial {\bf x}} \left( {\bf x}^{\rm T}{\bf A}{\bf x} \right) = {\bf x}^{\rm T} \left( {\bf A} + {\bf A}^{\rm T} \right)$ が成り立つことを確かめて下さい。

1. $f, g$ をベクトルを入力とする実数値関数とします。
微分について以下の性質が成り立つことを示して下さい。

    * $\frac{\partial}{\partial {\bf x}}(f({\bf x}) + g({\bf x})) = \frac{\partial}{\partial {\bf x}}f({\bf x}) + \frac{\partial}{\partial {\bf x}}g({\bf x})$.
    * $c$ を任意の実数とするとき、$\frac{\partial}{\partial {\bf x}}(cf({\bf x})) = c\frac{\partial}{\partial {\bf x}}f({\bf x})$.
    * $c$ を任意の実数、${\bf b}$ を任意のベクトルとするとき、$\frac{\partial}{\partial {\bf x}}f(c{\bf x} + {\bf b}) = c\frac{\partial}{\partial {\bf y}}{\bf f}({\bf y})$. (ここで ${\bf y}=c{\bf x}+{\bf a}$ とする。)

1. ${\bf x}$ を $n$ 次元ベクトルとします。
    以下の関数 $f$ に対するベクトルの微分 $\frac{\partial}{\partial {\bf x}}f({\bf x})$ を計算して下さい。

    * $f({\bf x}) = \max(x_1, x_2, \ldots, x_n)$.

    * $f({\bf x}) = \sqrt{x_1^2 + x_2^2 + \ldots + x_n^2}$.

    * $f({\bf x}) = |x_1 + x_2 + \ldots + x_n|$.

1. 3次元ベクトルに対するベクトル値関数 ${\bf f}$ を以下によって定義します。
    $$
    {\bf f}(\begin{bmatrix}
    x_{1} \\
    x_{2} \\
    x_{3}
    \end{bmatrix}) = \begin{bmatrix}
    x_{2}^2 \\
    x_{3}^2 \\
    x_{1}^2
    \end{bmatrix}.
    $$

    (1) ${\bf f}({\bf x})$ のヤコビ行列 $\frac{\partial}{\partial {\bf x}}{\bf f}({\bf x})$ を計算して下さい。

    (2) ${\bf f}({\bf f}({\bf x}))$ を計算して下さい。

    (3) ${\bf f}({\bf f}({\bf x}))$ のヤコビ行列 $\frac{\partial}{\partial {\bf x}}{\bf f}({\bf f}({\bf x}))$ を、(1) の結果を用いて計算して下さい。

    (4) $\frac{\partial}{\partial {\bf x}}{\bf f}({\bf f}({\bf x}))$ を合成関数の微分則 $\frac{\partial}{\partial {\bf x}} {\bf f}( {\bf g}({\bf x}))  = \frac{\partial {\bf f}}{\partial {\bf u}}({\bf u}) \frac{\partial {\bf g}}{\partial {\bf x}}({\bf x})$ (${\bf u}={\bf g}({\bf x})$) によって計算し、結果が (3) と一致することを確認して下さい。

1. ${\bf A}$, ${\bf B}$ を $n \times n$ 行列とします。$n$ 次元ベクトル ${\bf x}$ に対して ${\bf f}({\bf x})={\bf A}{\bf x}$, ${\bf g}({\bf x})={\bf B}{\bf x}$ とします。

    合成関数の微分則を用いて $\frac{\partial}{\partial {\bf x}}{\bf g}({\bf f}({\bf x})) = {\bf B}{\bf A}$ を示して下さい。

1. (1) $f(y, z) = 2y-3z$ とします。このとき、1変数関数 $g(x)$ と $h(x)$ に対して

    $$
    \frac{d}{dx}f(g(x), h(x)) = 2g^{'}(x)-3h^{'}(x)
    $$

    であることを確認して下さい。

    (2) $f(y, z) = yz$ とします。このとき $\frac{d}{dx}f(g(x), h(x)) = g^{'}(x)h(x) + g(x)h^{'}(x)$ であることを確認して下さい。

    (3) 2変数実数値関数 $f(y, z)$ と1変数関数 $g(x), h(x)$ に対し以下が成り立つことを合成関数の微分則 $\frac{\partial}{\partial {\bf x}} {\bf f}( {\bf g}({\bf x}))  = \frac{\partial {\bf f}}{\partial {\bf u}}({\bf u}) \frac{\partial {\bf g}}{\partial {\bf x}}({\bf x})$ (${\bf u}={\bf g}({\bf x})$) を用いて示して下さい。

    $$
    \frac{d}{dx}f(g(x), h(x)) = \frac{\partial f}{\partial y}(y, z) \cdot g^{'}(x) + \frac{\partial f}{\partial z}(y, z) \cdot h^{'}(x)
    $$

    ここで、$y=g(x)$, $z=h(x)$ とします。この結果が (1) と (2) の式の一般化になっていることを確かめて下さい。

    (4) 平面上を移動する点があり、時刻 $t$ の点の座標 $(x(t), y(t))$ は $x(t)=t^2+t+1, y(t)=t^2-t+1$ であるとします。座標 $(x,y)$ にいるとき、点は $E(x,y)=\exp(\frac{1}{\sqrt{x^2+y^2}})$ のエネルギーを持っているとします。エネルギーの時間に関する微分 $\frac{\partial}{\partial t}E(x(t),y(t))$ を (3) の結果を用いて求めて下さい。

1. ベクトル値関数 ${\bf f}$ を以下で定義します。

    $$
    {\bf f}(\begin{bmatrix}
    z \\
    w
    \end{bmatrix}) = \begin{bmatrix}
    \frac{e^z}{e^{z+w}} \\
    \frac{e^w}{e^{z+w}}
    \end{bmatrix}.
    $$

    ${\bf X}$ を $2 \times N$ 行列、${\bf y}$ を $N$ 次元ベクトルとします。
    偏微分 $\frac{\partial}{\partial x_{ij}}{\bf f}({\bf X}{\bf y})$ を計算して下さい。ここで、$x_{ij}$ は ${\bf X}$ の $(i,j)$ 成分とします。

# 第7章: 確率・統計の基礎
1. 偏りのあるコイン ${\rm A}$ と ${\rm B}$ があります。
    コイン ${\rm A}$ を振ったときに表が出る確率は1/4、裏が出る確率は3/4です。コイン ${\rm B}$ を振ったときに表が出る確率は2/3、裏が出る確率は1/3です。

    この二つのコインのうちどちらか一つを等しい確率でランダムに選び、選んだ方のコインを振るという試行を考えます。
    選んだコインが ${\rm A}$ と ${\rm B}$ どちらだったかを表す確率変数を $X$、コインを振った結果(表裏)を表す確率変数を $Y$ とします。

    (1) 同時確率 $p(X={\rm A}, Y=表)$, $p(X={\rm A}, Y=裏)$, $p(X={\rm B}, Y=表)$, $p(X={\rm B}, Y=裏)$ をそれぞれ計算して下さい。

    (2) 同時確率を周辺化して、確率 $p(Y=表)$ と $p(Y=裏)$ を計算して下さい。
1. 問6.1 の試行で条件付き確率 $p(Y=表 \mid X={\rm A})$ を計算して下さい。
1. (1) 問6.1 の試行で事後確率 $p(X={\rm A} \mid Y=表)$, $p(X={\rm B} \mid Y=表)$, $p(X={\rm A} \mid Y=裏)$, $p(X={\rm B} \mid Y=裏)$ をそれぞれ計算して下さい。

    (2) 問6.1 の試行を行った後、コインは表が出たとします。この後さらに同じコインを振ったときに再び表が出る確率を計算して下さい。
1. 一様な確率で1から6までの数が出るサイコロがあります。
    サイコロを何回か連続で振る試行を考えます。サイコロを振った後、直前に出た数より大きい数が出たときに「ラッキーである」と呼ぶことにします。
    例えばサイコロを5回振って 2,5,3,4,4 と順に出た場合、2回目と4回目はラッキーですが、それ以外はラッキーではありません。

    いま、サイコロを 10 回振って一度もラッキーではなかったとします。このとき、次にサイコロを振ってラッキーになる確率はいくらになるでしょうか。プログラムを使って分析してみて下さい。
1. 偏りのあるサイコロの出る目の確率を推定する問題を考えます。サイコロを振ったときに出る数を表す確率変数を $X$ とします。確率モデルのパラメータを $\theta=(\theta_1, \theta_2, \theta_3, \theta_4, \theta_5, \theta_6)$ として、確率 $p(X=x)$ を

    $$
    f(x; \theta) = \theta_x
    $$

    によってモデル化します。ここで、パラメータは $\theta_1, \ldots, \theta_6 \ge 0$ かつ $\theta_1+\ldots+\theta_6=1$ を満たさなくてはならないとします。

    いま、サイコロを60回振って、1の目が30回、それ以外の目が6回出たとします。

    (1) 観測データに対する対数尤度を求めて下さい。

    (2) プログラムを用いて、$\theta=(\theta_1, \ldots, \theta_6)$ に様々な値を入れた場合に対数尤度がどのようになるかを観測して下さい。$\theta$ がどのようなときに対数尤度が大きくなるか予想してください。
1. ポアソン分布は正の実数 $\lambda>0$ をパラメータとして持つ分布です。$0$ 以上の整数値を取る確率変数 $X$ が以下の確率値に従うとき、$X$ はポアソン分布に従うと言います。

    $$p(X=k)=\frac{\lambda^k e^{-\lambda}}{k!} \; \; \; (k=0,1,2,\ldots).$$

    いま、ある交差点で特定の時間帯に存在する歩行者の人数のをポアソン分布でモデル化することを考えます。
    $X$ を特定の時間帯に存在する歩行者の人数を表す確率変数とします。確率 $p(X=k)$ は上記のポアソン分布に従うとします。

    20日間の観測結果によると、$i$ 日目には $10+i$ 人の歩行者を観測したことが分かっているとします。($i=1,2,\ldots,20$)

    (1) 観測データに対する対数尤度を求めて下さい。

    (2) 対数尤度を最大にする $\lambda$ の値を求めて下さい。

    (3) (2) で求めた $\lambda$ をパラメータとして用いたとき、$k=0,1,\ldots,50$ に対して $p(X=k)$ をプログラムを用いて計算して下さい。なお、累乗 $\lambda^k$ の計算には組み込み関数の `pow` を、階乗 $k!$ の計算には `math` モジュールにある `math.factorial` を用いると便利です。

1. 6章の例6.7.1 にあるコイントスの試行で、事前確率 $p(\theta)$ を以下のように変更した場合にどうなるかを考えてみます。

    $$
    p(\theta)=\begin{cases}
    3 & (1/3 \le \theta \le 3/2) \\
    0 & (\text{otherwise})
    \end{cases}
    $$

    コインを10回振って9回表が出て1回裏が出たとき、MAP 推定によってパラメータ $\theta$ を推定して下さい。

1. 生徒が100人いる学校で期末試験をした結果、科目Aと科目Bの点数は以下のような結果になりました。

    * 科目A: 20点の生徒が50人、80点の生徒が50人
    * 科目B: 0点の生徒が1人、1点の生徒が1人、2点の生徒が1人、…、99点の生徒が1人

    この二つの科目について、生徒の点数の平均と標準偏差をそれぞれ計算して下さい。プログラムを用いてもよいです。

    この例から分かるように、データのばらつきが非常に異なる性質をもっていても平均や標準偏差が近い値になることがあります。

# 第8章: パラメータ推定

# 第9章: 信号処理の基礎

# 第10章: ファイル入出力

# 第11章: ニューラルネットワーク

# 参考文献
- [Chainer Tutorial](https://tutorials.chainer.org/ja/tutorial.html)
- 田中，信号・データ処理のための行列とベクトル