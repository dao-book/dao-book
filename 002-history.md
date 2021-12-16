
- サービスの概要
- DAO化の背景
- トークン配布方法
- ENS憲法とガバナンスの仕組み
- 今後の課題


## サービスの概要

ENS（Ethereum Name Service）は１６進数の羅列であるイーサリアムアドレスにmatoken.ethといった分かりやすい名前を紐付けることができるサービスです。イーサや他の暗号通貨を送るためだけでなく、Dweb（Decentralised Web。IPFSなどを使った分散サイト）の名前に使ったり、異なったマーケットプレースなどでも表示可能なWeb3ユーザーネームとしても使われています。

サービスの沿革は以下の通り

- ２０１６年 Ethereum Foundation のコア開発者でエアルNick Johnson により開発を開始
- ２０１７年５月 サービスを立ち上げ
- ２０１８年 Ethereum Foundationより百万ドルの助成金を受け True Names Limitedというシンガポールの会社として独立
- ２０１９年５月　ENSをERC721互換のNFTにアップグレード
- ２０１９年９月　OpenSeaにてショートネーム（３〜６文字）のオークションを行い、百万ドル相当を調達
- ２０２１年の１１月のDAO化をアナウンス

イーサリアム上で現存する最古のプロジェクトの一つであり、ERC721といったNFT規格が立ち上がる以前から存在した最古のNFTプロジェクトの一つでもあります（最古のNFTプロジェクトとして有名なクリプトキティより１ヶ月ほど早くサービスを開始しました。）

DAO化アナウンス前の時点で４０万件程度の名前が１３万アドレスに所有されていました。また３００近いウォレットや取引所、Dapps（Decentralised App）に統合されていました。

コードは全てオープンソース化されており、誰もがコピー、改変可能であり、実際２〜３のコピープロジェクトが存在していますが、コピープロジェクトは３００近く統合されたDappsからは使えないため、極めてネットワーク効果が高いプロジェクトです。コアなユーザーは自分のSNSのプロファイル名を.ethにするなどイーサリアムのエコシステムとっも密接に関わっています。

## DAO化の背景

ENSは階層的に所有権が定義されており、matoken.ethの所有者がartist.matoken.ethといいったように新たにサブドメインを作成し、アドレスの紐付けをすることができます。サブドメインの所有権は親ドメインに属します。そのため皆さんが登録できる.eth名はルートドメインの管理下におかれます。そしてENSがスタートした時からルートドメインは七人の有識者（ENS開発チームからはNick Johnsonのみ）によって管理されており、過半数の同意によってアップグレード可能な作りになっています。以前はこの７名の過半数同意があれば任意のドメインの所有権の上書きが可能でしたが、それは現在不可逆的に不可能なようにスマートコントラクトを変更しています。

１０人未満にプロトコルのアップグレード権を委ねる方法は他の多くのプロジェクトでも取り入れられている手法で、TheDAOのようなセキュリティの微弱性（TODO：前章で説明予定）が発見したときに素早くプロトコルのアップグレードを可能にする一方、中央集権的という批判も受けてきました。

プロジェクト開始当時からいずれはDAOのような分散組織への議論が、年次に開催されていた開発者会議「ENSワークショップ」で毎年のように議題にはあがっていました。しかしながらDAO化のためのツールが未発達であった上、「トークンの敵対的買収などからどうやって防衛するか」という懸念があり、常に早急な分散化には慎重な姿勢でした。

しかしながら２０２０年のDefiSummer（Decentralised Govenance）プロジェクトのDAO化（TODO：前章で説明予定）に伴い関連ツールやサービスが充実するとともに、２０２１年のJpeg Summer（TODO：前章で説明予定）によるNFTの人気かに伴い、NFTの老舗であり、Web3ユーザーネームとしてENSの人気が２０２１年の春頃から再燃しました。これにより主な収益である.ethドメインの年間登録料（年五ドル相当のイーサ）により月間収入がDAO化前の月で２００万ドル(登録数２〜3万)をうわまるまで成長し、ENSのスマートコントラクト自身に２０００万ドル相当のイーサが蓄積するまでになり、この収益の配分に関しても小さなチーム（当時フルタイムで働いていたチームメンバーは４名程度）で決断するには重荷になってきました。ENS立ち上げに受け取ったのと同規模の７０万ドル相当のイーサを２０２１年５月にGitcoinというクラウドドネーションプラットフォームに寄付はしたのですが、もっとENSエコシステムの発展に有意義に登録料収入を割り振る必要が出てきました。

同年５月にGitcoinがトークンを立ち上げたのはENS自身のトークン立ち上げにも非常に参考になりました。GitcoinはDefiレンディングプラットフォームであるCompound（TODO：前章で説明予定）の「Delegation」という仕組みを使っています。Delegationは一般のトークンホルダーが、自分が信用する第三者に投票権を委譲する仕組みで、多くのDefiプロジェクトでも採用されているのですがDelegateすること自体にガス代がかかるためDelegationの利用率自体が低くなりがちです。Gitcoinではこの問題を解決するために事前に「Steward」という制度を設け、コミュニティで活躍する４０〜50名程度の人々に勧誘を呼びかけていました（筆者もGitcoin上でドネーションを受けたり、仕事の依頼を昔からしていた経緯からSteward依頼を受けました）。そしてトークンをクレームする時点で投票権を委任するDelegateをしなければトークンをもらえないような設計になっていました。そのことによりDelegate率を最初から高くすることにし、プロポーザルに対する高い投票率を実現しています（TODO:実際の投票率確認する必要あり）。

Gitcoinプロジェクトの共同創業者であるScott Moorと著名DefiプロジェクトであるAave, YarnやソーシャルトークンプロジェクトであるFriends With Benefits, Forefront, コレクターDAOであるPleasrDAOのDAOアドバイザーとして活躍するFireEyesDAOをアドバイザーに迎え、２０２１年に入ってから具体的にDAO化とトークン配布の計画を立てました。

## 法人格

ENSの開発チーム自体はイギリス、台湾、米国、ニュージーランドなど世界中に散らばっています。開発チームはシンガポールにある「True Names Ltd」に帰属しています。

法人格のないDAOというのは多く存在するのですが、どの国に帰属するかが明確でないDAOはどの国からも「そのDAOは我が国に属する」といわれる可能性があります。そのためENSのDAO自体はケイマン諸島に法人格を設立しています（TODO: リンクを明記）。なおケイマン諸島は法人の所得税、キャピタルゲイン税に関して非課税になっています（TODO: もうちょっと詳しく調べるべき）。

## トークン配布方法

## ENS憲法とガバナンスの仕組み

## 今後の課題