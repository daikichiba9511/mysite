@def title = "statistics"
@def tags = ["syntax", "code"]

# statistics

ここでは主に統計についてまとめていく。

## ベイズ推論

### 統計的推測

---

データを支配している、未知で観測不可能な確率分布を真の確率分布と呼ぶ。サンプルはこの真の確率分布に従って生成されていると考え、このときのサンプルを $x^n = (x_1, x_2, \dots, x_i, \dots , x_n)$とする。

標本抽出などで得られたサンプルを元に確率分布モデルを組み合わせて、真の確率分布の推測を行うことを**統計的推測**と呼ぶ。

ベイズ推論は統計的推測の手法の一つである。

分析者は確率モデルを組み合わせることで、分析対象のサンプルを生成するような真の確率分布は$p^{*}(x)$だろうと推測を行う。この$p^{*}(x)$を**予測分布**と呼ぶ。

統計的推測では予測分布によって推論を行うので、以下ではまず予測分布を構成する。

また、生成されたサンプルは標本抽出などでのデータの取られ方によって確率的に揺らぐ。そのためサンプルによって結果は変動することが分かる。従って、サンプルを確率変数の実現値として考える。


![bayes_outline](https://daikichiba9511.github.io/mysite/statistics/images/statistics01_images/bayes_outline.png)

### 予測分布

---

予測分布を構成するために、まずパラメータの事後分布について定義する。その後定義した事後分布を用いて予測分布を定義する。

\definition{事後分布}{\
\
確率分布モデルを$p(x | w)$、この時、パラメータwの事前分布を$\varphi(w)$とおく。

定数$\beta$を$0 < \beta < \infty$を満たす実数であるとする。これを**逆温度**と呼ぶ。

このとき、パラメータ$w$、逆温度$\beta$の**事後分布**を

$$
p(w|X^n) = \frac{1}{Z_{n}(\beta)}\phi(w)\prod_{i=1}^{n}p(X_{i})|w)^{\beta}
$$

と定義する。ここで$Z_{n}(\beta)$は**分配関数**と呼ばれるもので

$$
Z_n(\beta) = \int_W \phi(w) \prod_{i=1}^n p(X_{i}|w)^{\beta}dw
$$

である。特に$\beta=1$のときの$Z_n(1)$を**周辺尤度**と呼ぶ。

また事後分布、分配関数は共にサンプルによって確率的に変動するので確率変数である。

}



## 参考文献

- [1] [ベイズ統計の理論と方法](https://www.coronasha.co.jp/np/isbn/9784339024623/)　渡辺澄夫　(2012) コロナ社
- [2] [代数幾何と学習理論](https://www.morikita.co.jp/books/book/1905)　渡辺澄夫　(2006) 森北出版

- [3] [渡辺澄夫先生のHP](http://watanabe-www.math.dis.titech.ac.jp/users/swatanab/index-j.html)

- [4] [入門数理統計学](https://www.amazon.co.jp/dp/4563008281/ref=cm_sw_em_r_mt_dp_U_oj8bFbTJJN7YY)　P.G.ホーエル　(1978) 培風館

- [5] [現代数理統計学の基礎](https://www.kyoritsu-pub.co.jp/bookdetail/9784320111660)　久保川達也　(2017) 共立出版
 
- [6] [確率の基礎から統計へ](http://www2.odn.ne.jp/yuseisha/oyohoka/toukei-c.htm)　吉田伸生　(2012) 遊星社