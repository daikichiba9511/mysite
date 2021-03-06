@def title = "statistics"
@def tags = ["syntax", "code"]

# ベイズ推論

\tableofcontents

## 統計的推測

データを支配している、未知で観測不可能な確率分布を真の確率分布と呼ぶ。サンプルはこの真の確率分布に従って生成されていると考え、このときのサンプルを $x^n = (x_1, x_2, \dots, x_i, \dots , x_n)$とする。

標本抽出などで得られたサンプルを元に確率分布モデルを組み合わせて、真の確率分布の推測を行うことを**統計的推測**と呼ぶ。

ベイズ推論は統計的推測の手法の一つである。

分析者は確率モデルを組み合わせることで、分析対象のサンプルを生成するような真の確率分布は$p^{*}(x)$だろうと推測を行う。この$p^{*}(x)$を**予測分布**と呼ぶ。

統計的推測では予測分布によって推論を行うので、以下ではまず予測分布を構成する。

また、生成されたサンプルは標本抽出などでのデータの取られ方によって確率的に揺らぐ。そのためサンプルによって結果は変動することが分かる。従って、サンプルを確率変数の実現値として考える。


![bayes_outline](https://daikichiba9511.github.io/mysite/statistics/images/statistics01_images/bayes_outline.png)

## 予測分布

予測分布を構成するために、まずパラメータの事後分布について定義する。その後定義した事後分布を用いて予測分布を定義する。

\definition{事後分布}{
確率分布モデルを$p(x | w)$、この時、パラメータwの事前分布を$\varphi(w)$とおく。

定数$\beta$を$0 < \beta < \infty$を満たす実数であるとする。これを**逆温度**と呼ぶ。

このとき、パラメータ$w$、逆温度$\beta$の**事後分布**を

$$
p(w|X^n) = \frac{1}{Z_{n}(\beta)}\phi(w)\prod_{i=1}^{n}p(x_{i}|w)^{\beta}
$$

と定義する。ここで$Z_{n}(\beta)$は**分配関数**と呼ばれるもので

$$
Z_n(\beta) = \int_W \phi(w) \prod_{i=1}^n p(x_{i}|w)^{\beta}dw
$$

である。特に$\beta=1$のときの$Z_n(1)$を**周辺尤度**と呼ぶ。

}

\note{}{
    ここで定義した事後分布は確率変数であることに注意。\
    \
    これは分配関数がサンプルによって決まるので確率的に変動する、すなわち確率変数であるためである。\
    \
    サンプルが確率変数であるのでサンプルに依存して決まる値は確率的に値が変動することに注意されたい。
}

次に予測分布を構成する。そのために事後分布に関して平均を求める操作を以下のように定義する

\definition{事後分布に関する平均}{
パラメータ$w$の関数の関数f(w)に対して、事後分布 $p(w|x^{n})$ による平均値を

$$
\mathbb{E}_{w} [ f(w) ] = \int f(w) p(w | x^{n}) dw
$$

とする。これはパラメータ$w$について積分してるためwの関数ではないことに注意されたい。(3)もまたサンプルx^{n}によって確率的に変動する値である。
}

以上で定義してきた事後分布と(3)を用いて予測分布は以下のように定義される。

\definition{予測分布}{
    事後分布によって確率分布モデル $p(x | w)$ を平均したもの
    $$
    \begin{aligned}
        p^*(x) &= \mathbb{E}_{w} [ p(x | w) ] \\
                &= \int p(x | w)p(w|x^{n}) dw 
    \end{aligned}
    $$
    を**予測分布** という。これを$p^*(x)=p(x|x^n)$
    と書くこともある。
}

よって、分析対象のサンプルを生成している真の確率分布が上記で定義した予測分布であろうと推測するのがベイズ推測である。

## 以下メモ

ここから下は自分が考えてること、理解してることを雑多にメモとして残している。

### 統計という枠組み

統計的推測を行うのに当たって、独立同分布(i.i.d)であることを仮定していることに注意されたい。つまり、サンプルは全て同じ母集団の分布から
出ていることを仮定している。

この仮定が成り立っていると言えない状況つまり、時系列予測などでよくある学習した分布と予測対象の分布が大きく違ったりなどすると推測は途端に難しくなり、統計以外の道具を使う必要が出てくる。

自分が解析するときに作成する確率モデルの中でたまたま観測されたサンプルが発生したときにはどのような様子になるか、統計的推測は現実を解析、推測するために確率モデルを作ってシミュレーションすることで何らかの結果を観察し、分析、推測しようというものである。

### 頻度主義とベイズ主義

頻度主義やベイズ主義なんかを持ち出す解説でよくある、「頻度論はパラメータが固定で、ベイズはパラメータは確率変数」だのような解説は誤りであると思われる。統計的に推論を行うということは全数調査ができないからサンプリング（標本調査）をしてそのサンプルから対象の母集団の分布、要は何らかの規則がないかを推測する訳である。どの部分をサンプリングするかによって、解析のためのサンプルは確率的に揺らぐ値（確率変数）になっている。
よって事後分布などもサンプルによって確率的に揺らぐ値なので確率変数になる。これは頻度論と呼ばれる？最尤法などで予測するときも同様である。
サンプルが確率的に揺れてる値なのでそれによって決まるものも確率的に揺らぐ。

またベイズを導入する際に自分の信念や確信度を表すとして主観確率なる概念を導入するが、これは必要ないと考える。
事前分布を主観的に選択するために言われていたことかもしれないが、いわゆる頻度論ですら確率モデルを選ぶときには主観的に選びモデルをAICなどで比較したりしてるはずである。単に確率は確率で良いと思われる。

またベイズ統計に置いて事前分布は部品の一つくらいの認識が良いと思う。確率モデル全体としての良し悪しを判断する方が健全である。今は渡辺先生によって予測の観点ではWAICが、確率モデルとして真の確率分布に対する良し悪しはWBICなどがあるようである。今までよりも適用範囲の広い情報量基準であるが万能ではないので注意は必要である。

統計的推論を行う状況は、全数調査ができないような状況になるが一般的なので真の確率分布は不明で分析する。つまり不良設定問題ということを常に意識したい。

### 仮説検定という枠組み

仮説検定は対象のデータに対して分析者が確率モデルを用意し、その中で観測したサンプルに対して帰無仮説が偶然発生したものなのか、それとも起こり得るとは到底言えないものなのかをはじめに水準（有意差）を決めておき、そのサンプルが発生する確率（の近似値=p値)を計算して棄却するかしないのかを決めるものである。

仮説検定という枠組みは、帰無仮説を棄却することに信頼性を置いてる。これは帰無仮説が棄却できなかったからといって帰無仮説が採択されるわけではないことを言っている。つまりこれは帰無仮説は棄却されなかった時は、帰無仮説は肯定も否定もできない。。くらいのニュアンスでしか捉えることはできない。さらにはサンプルサイズが増えるほどにp値は低くなりやすい。これはサンプルサイズが大きくなることで情報が増え、解像度が上がるため仮説検定で使われるような確率分布モデルとの差がよりはっきりするためと考えることができる。


