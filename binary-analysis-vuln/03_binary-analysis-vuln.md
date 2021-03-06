# バイナリファイル解析によるアプリ脆弱性検知システムについての考察
## 概要
あるソフトウェアに脆弱性が発見されると他のソフトウェアでも類似した脆弱性が見つかることがあり、そのような類似した脆弱性にも対応する必要がある。
そこで既知の脆弱性の共通項を見つけ、同じような脆弱性を持っているかどうかを検知するフレームワークについて考えている。

このフレームワークはあるソフトウェアの既知の攻撃手法がある未知の脆弱性を検知を自動化、支援できる。

## 関連技術、関連研究と課題
プログラムバイナリ解析の関連研究として、[4][5]などがある。
既知脆弱性を含むバイナリコードと検知対象のバイナリコードを正規化、比較して類似度やハッシュの一致を検査することで同じ脆弱性を持っているか検知する。
攻撃傾向に合わせて迅速に対応する必要があるので、脆弱性を含むバイナリコードを収集する必要がある点に課題がある。

### 検知システム概要
この論文で、攻撃手法は既に判明しているが検知対象のソフトウェアがそれに対する脆弱性を持っているかどうかが未知の場合の検知フレームワークを提案している。
攻撃トレンドを考慮した優先付けをする。
脆弱性のあるコード自体も抽出する。

JVNなどで公開される脆弱性情報をグループにして、報告数が多いものの優先度を上げる。
ただし、IDやCWEなどはおおざっぱ過ぎるので概要やタイトルの情報をテキスト解析して攻撃トレンドとして決定する。

攻撃トレンドを決定したあとは、該当するソフトウェアのプログラムバイナリを収集して脆弱性のあるコードを特定する。
共通部分を利用することで複数ソフトウェアから脆弱性コードを特定する。

=> 提案だけだった。次のを探す。

# 参考文献
[1] IPA, 脆弱性検査と脆弱性対策に関するレポート,2013
[2] nessus, https://www.tenable.com/products/nessus/nessus-professional
[3] BlackDuck Hub, https://www.blackducksoftware.com//products/hub
[4]中島明日香,岩村誠,矢田健,機械語命令の類似度算出による複製された脆弱性の発見手法の提案,CSS2015
[5]Yaniv David,Nimrod Partush,Eran Yahav,Similarity of Binaries through re-Optimization,PLDI2017
[6] JVN, http://jvn.jp/
[7] IPA JPCERT, 脆弱性対策情報データベースJVN iPedia に関する活動報告レポート[2017 年第 2四半期(4 月~6 月)],2017/07
