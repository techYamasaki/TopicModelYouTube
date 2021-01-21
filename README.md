# LDAによるTopicModel

## Overview
トピックモデルの代表的な手法であるLatent Dirichlet Allocation(LDA)を利用して，livedoorのニュース記事から生成されるbag-of-wordsを次元削減し，トピックモデルを作成します．また簡易的な検証のために，記事をトピックを利用して，各ジャンルに分類します．

## Description
それぞれのnotebookの内容を説明する．
### `save_livedoor_corpus.ipynb`
livedoorの記事をダウンロードし，それぞれの記事を，形態素解析する．動詞，名詞，形容詞のみを抽出し，記事のタイトルとジャンルと併せて格納する．全ての記事に処理を行い，コーパスを作成する．
### `topicmodel_with_lda.ipynb`
コーパスを学習データと評価データに分け，学習データに対してbag-of-wordsを経由してトピックモデルを作成する．トピック数はcoherenceとperplexityから9に設定した．例として，ジャンルpeachyの全ての記事に対して算出したトピック分布を以下に示す．  
各トピックの意味を理解するために，pyLDAvisを利用した．pyLDAvisは，PCoA，MMDS，t-SNE等の次元削減手法を用いて，トピック間の距離を2次元上で可視化できる．PCoAによる可視化を以下に示す．   
最後に，評価データの記事にも構築したトピックモデルからトピック分布を取得する．トピック分布を記事の特徴量として，各記事をPCAによって二次元上にプロットした．また，記事のジャンルごとに色分けした．
### `classification_using_topic.ipynb`
構築したトピックモデルの有用性を簡単に検証するために，RandomForestによって記事を各ジャンルに分類した．正答率は3２%程度でやや低めであったが，ジャンル数が9つであった事を考えると，トピックモデルが有効であったことがわかる．

<img src="https://user-images.githubusercontent.com/55009777/105167211-c7f7f600-5b5b-11eb-8cfe-50a712c4edb3.png" width="500px">

![pyLDAvis](https://user-images.githubusercontent.com/55009777/105167114-a434b000-5b5b-11eb-8b09-da6322eecd68.png)
