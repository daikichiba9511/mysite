# A study about Explainable Articial Intelligence: using decision tree to explain SVM

## References

* [1] [A study about Explainable Articial Intelligence: using decision tree to explain SVM](https://www.researchgate.net/publication/341643347_A_study_about_Explainable_Articial_Intelligence_using_decision_tree_to_explain_SVM)

## どんなことをしたか

決定木を使ってsvmの出力ラベルを学習してどの特徴量が効いてるのか解釈する

## 先行研究と比べてどこがすごいか

説明性の信頼度がより高く、意味のある技術である

## 技術や手法のキーポイントは何か

* 手軽
* svmの予測ラベルを正解ラベルとして学習した決定木とそのままのデータを学習した決定木を比較してることで間接的にsvmにとって重要だと判断した特徴量なんかを評価してる。（やや精度の欠落はありそう）

## どうやって有効だと検証してるか

* kaggleのデータセットを２つとってきて上で述べたように比較して、svmのラベルを学習した方の決定木を可視化してる
* さらにラベルを学習した決定木はsvmと同程度の精度を出した

## 議論はあるか

汎化性能をみたいわけではないので過学習させてるのが良いらしい

* あるペアを取ってきて一方がpositiveと予測されたときにもう一方がnegativeと予想されるのはなぜか

* なぜpositiveあるいはnegativeと予測されるのか

## 次に読むべき論文は？

* [Why Should I Trust You?": Explaining the Predictions of Any Classifier](https://arxiv.org/abs/1602.04938)

LIMEやSHAPについて知りたいから

## 検証実験をしたか

https://github.com/daikichiba9511/mathematical/blob/master/math/ml/XAI/intepretability_svm.py