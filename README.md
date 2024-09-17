# 洪 成雨<br>
ホン ソンウ<br>
Hong Seongwoo<br>

## 作品一覧
<ul>
  <li><a href="#crystal_ascendant">Crystal Ascendant(ゲームクライアント)</a></li>
  <li><a href="#lamoom">Lamoon(ゲームサーバー)</a></li>
  <li><a href="#blog">Blog(Webアプリケーション)</a></li>
</ul>

## <p id="crystal_ascendant">Crystal Ascendant(ゲームクライアント)</p>

<img src="https://github.com/user-attachments/assets/5c6b7128-020d-4fdd-a3d7-998d5efc1306" style="width:500px">

### 開発環境
Windwos, Unity, C#, Git

### 開発期間

2023.07-2023.11, 2024.07-2024.09 (8ヶ月間)

### 関連リンク

<ul>
  <li>
    <a href="https://h-ame.itch.io/crystal-ascendant">ゲームプレイ(ブラウザ上起動)</a>
  </li>
  <li>
    <a href="https://github.com/SeongUHong/project_fg">GitHub</a>
  </li>
</ul>

### プロジェクト詳細

Unityを利用して開発した3Dディフェンスゲームです。右側からスポーンされるモンスターを倒し、クリスタルを破壊するとステージクリアになります。各ステージが開始する前には準備画面でキャラとスキルをアップグレードすることができます。

<img src="https://github.com/user-attachments/assets/6cf5cf0c-e067-4ea1-8bb7-36751adb1f95" style="width:330px"><img src="https://github.com/user-attachments/assets/2c3f68ee-6e20-46fa-a3b5-82fdb63f7dbe" style="width:330px"><img src="https://github.com/user-attachments/assets/f86e1d1e-be49-4e0e-99fe-0ed20bbc1ff9" style="width:330px">

<details>
  <summary>世界観</summary>
  突然現れた謎のクリスタルは、その登場と同時に強大なエネルギーを放ち、モンスターを召喚して人間社会を破壊し始めた。その瞬間に巻き込まれた主人公は魔法の力を得たことに気づく。崩壊した世界の中で、主人公はその魔法の力を仲間たちに分け与え、人類の最後の希望としてモンスターに立ち向かう。
</details>

### 機能

<details>
  <summary>スキル・ユニットアップグレード</summary>
    <img src="https://github.com/user-attachments/assets/24f3ea15-ce62-44d6-b8f6-1c3641b88737" style="width:330px"><br>
    ステージに挑戦する前に準備画面があり、プレイヤー、ユニット、スキルのレベルを上げることができます。レベルを上げることには1ポイントが必要であり、ポイントはステージをクリアすると1ポイントずつ付与されます。
</details>

<details>
  <summary>ユニット召喚</summary>
    <img src="https://github.com/user-attachments/assets/dfd2aa8f-ba3b-42ec-8596-e036907b907c" style="width:330px"><br>
    時間経過に伴い、召喚ゲージがチャージされていきます。そして、一定の召喚ゲージを消費し、ユニットを召喚することができます。召喚されたユニットはクリスタル破壊を目的に進行し、モンスターがいる場合は、近くのモンスターを優先して攻撃します。
</details>

<details>
  <summary>スキル</summary>
    <img src="https://github.com/user-attachments/assets/325f5c66-fa3b-4eab-9c47-826af714c72f" style="width:330px"><br>
    スキルを使用すると、前方にいる多数のモンスターにダメージを与えることと、周りの敵に持続的なダメージを与えることができます。ただし、スキルにはクールタイムがあり、クリスタルにはダメージを与えられません。
</details>

<details>
  <summary>モンスタースポーン</summary>
  <img src="https://github.com/user-attachments/assets/e8706891-3c47-4dd9-9b78-2fcbe0c913fb" style="width:330px"><br>
  クリスタルの周囲からは一定間隔で次々とモンスターが出現します。設定された上限に達するまでモンスターの出現は続きます。モンスターはプレイヤーを倒すことを目的に進行し、ユニットがいる場合は、最も近くのユニットを優先して攻撃します。
</details>

<details>
  <summary>データの拡張性</summary>
  ゲーム内の各種設定値はJSON形式のファイルで管理されています。スキルやユニットのレベル別ステータス、ステージに出現するモンスターの種類や数などを、設定ファイルの修正で簡単に調整可能です。設定ファイルを編集・追加するだけで、新しいスキルレベルやステージを無限に拡張できます。
  
  #### Datas/Stages/7.json
  
```json
{
	"spawn_monsters": [
		{
			"monster_id": "2",
			"level": "1",
			"limit_num": "2"
		},
		{
			"monster_id": "3",
			"level": "1",
			"limit_num": "2"
		},
		{
			"monster_id": "5",
			"level": "1",
			"limit_num": "3"
		}

	],
	"map_id": 2
}
```

</details>

<details>
  <summary>他職種を考慮した設計</summary>
  <img src="https://github.com/user-attachments/assets/26e38b72-b115-45ed-be31-2e5f4908c852" style="width:330px"><br>
  ユニットやモンスターの出現位置は、SpawnSpotオブジェクトのポジションを参照するため、新しいマップを作成するデザイナーは、SpawnSpotの位置を調整するだけでモンスターの出現場所を自由に設定できます。これにより、いちいちエンジニアに共有する手間が省けます。<br>
  また、スキルのレベル別ステータスやステージごとのモンスター設定は、JSON形式の設定ファイルで管理されています。プログラミングをしない企画職の方でも、設定ファイルを修正するだけで簡単にステータスや出現モンスターを調整できるため、エンジニアのサポートを必要とせず、効率よくゲームバランスを調整可能です。
</details>

## <p id="lamoom">Lamoon(ゲームサーバー)</p>

<img src="https://github.com/user-attachments/assets/c02018a2-923b-475f-8cb4-bace4c1fc65c" style="width:500px"><br>

### 開発環境
Windwos, Unity, .NET Framework, C#, Git

### 開発期間

2024.03-2024.06 (4ヶ月間)

### 関連リンク

<ul>
  <li>
    <a href="https://h-ame.itch.io/ramoon">ゲームダウンロード(android)</a>
  </li>
  <li>
    <a href="https://github.com/SeongUHong/project-sg">GitHub</a>
  </li>
</ul>

### プロジェクト詳細

.NET FrameworkとC#利用して開発したリアルタイム対戦ゲームサーバーです。プレイヤーはニックネームを入力してマッチングを開始し、マッチングした相手と対戦します。戦闘機を操作してミサイルを発射し、先に相手のHPをゼロにした方が勝者となり、制限時間内に決着がつかない場合は引き分けとなります。

<img src="https://github.com/user-attachments/assets/ab37b404-49f1-4dac-807a-12af464e2632" style="width:330px"><img src="https://github.com/user-attachments/assets/59276552-ee07-4b52-93c0-bbefd66d25d9" style="width:330px"><img src="https://github.com/user-attachments/assets/29f92d79-b18d-4738-9dc1-0394349c8155" style="width:330px">

<details>
  <summary>世界観</summary>
	資源が枯渇した未来の人類。宇宙を探索していた彼らは、ラムネでできた惑星「Ramoon」を発見する。地球から遥かに離れた宇宙では、守るべき法など存在しなかった。ただ、いち早くこの惑星を占領した者がRamoonの資源を支配できるという事実だけが存在する。
</details>

### 機能

<details>
  <summary>ニックネームの設定</summary>
	<img src="https://github.com/user-attachments/assets/aba9c53b-8d26-4e16-ab93-0a0ab74ebc85" style="width:330px"><br>
	マッチングごとにニックネームを設定し、そのニックネームは対戦画面に表示されます。これにより、プレイヤーのステータスが視覚的に区別しやすくなります。
</details>

<details>
  <summary>マッチング</summary>
	<img src="https://github.com/user-attachments/assets/33987178-fa51-4ecc-8746-106106f87e50" style="width:330px"><br>
	待機中のプレイヤー同士をマッチングし、マッチング後はどちらのプレイヤーもゲーム開始ボタンを押すまでゲームが開始されません。
</details>

<details>
  <summary>ミサイルゲージ</summary>
	<img src="https://github.com/user-attachments/assets/30aec94f-5109-484f-b5a7-6a67d529e837" style="width:330px"><br>
	ミサイルの発射には一定量のミサイルゲージを消費します。ミサイルゲージは時間とともに徐々にチャージされていきます。
</details>

<details>
  <summary>時間切れと強制終了</summary>
	<img src="https://github.com/user-attachments/assets/ab03e679-e518-4a24-ac28-f2834de6d690" style="width:330px"><br>
	対戦は制限時間があり、残り時間が対戦画面の上部に表示されます。時間内に決着がつかない場合は引き分けとなります。もしもプレイヤーが強制終了や通信切断で離脱した場合は、残っているプレイヤーの勝利となります。
</details>

<details>
  <summary>パケットクラス自動生成</summary>
	XMLファイルでパケットを定義し、PacketGeneratorプログラムを実行すると、そのXMLファイルの内容に基づいてパケットクラスが自動的に生成されます。このプロセスにより、パケットの修正があっても、パケットクラスを手動で修正する必要がなくなります。また、サーバーとクライアント間でパケットクラスの不一致を防ぎ、一貫した通信プロトコルを維持することができます。

```xml
<packet name="S_Gameover">
	<int name="status"/>
</packet>
<packet name="S_CountTime">
	<int name="remainSec"/>
</packet>
<packet name="C_Move">
	<float name="posX"/>
	<float name="posY"/>
	<float name="angle"/>
</packet>
```
 
</details>

## <p id="blog">Blog(Webアプリケーション)</p>
<img src="https://github.com/user-attachments/assets/634163ca-d40e-4778-a0e4-4fa7f8a7be18" style="width:500px">

### 開発環境
Linux, PHP, Laravel, Aapache, MySQL, Javascript, CSS, HTML, Git

### 開発期間

2023.11-2024.03 (5ヶ月間)

### 関連リンク

<ul>
  <li>
    <a href="https://surviveinjapan.com/">ウェブページ</a>
  </li>
  <li>
    <a href="https://github.com/SeongUHong/survive-in-japan">GitHub</a>
  </li>
</ul>

### プロジェクト詳細
Laravel Frameworkと利用して開発したWebアプリケーションです。日本での生活に関する記事を日本語と韓国語で投稿するブログ運営を目的としています。HTMLやCSSの知識がなくても、スタイル付きの記事を簡単に投稿できます。端末の画面サイズに応じてレイアウトが自動的に調整され、どのデバイスでも快適に閲覧できます。

<img src="https://github.com/user-attachments/assets/c6a3e1a0-3000-413d-a77f-6cb9f14b8482" style="width:200px"><img src="https://github.com/user-attachments/assets/40cc7f67-f5e5-4225-9a53-34552578e08d" style="width:320px"><img src="https://github.com/user-attachments/assets/04bada4a-b4a9-4e5f-bfd2-b2df244ad418" style="width:320px">

### 機能

<details>
	<summary>レスポンシブデザイン</summary>
	<img src="https://github.com/user-attachments/assets/c6a3e1a0-3000-413d-a77f-6cb9f14b8482" style="width:200px">
	<img src="https://github.com/user-attachments/assets/89f32d7d-7378-47bc-bc9b-9c1e96eaf029" style="width:200px"><br>	
	端末のサイズに応じてレイアウトが自動的に調整されます。幅が狭いスマホなどの端末では、モバイル専用の画面レイアウトに切り替わり、快適な表示が提供されます。
</details>
<details>
	<summary>記事の絞り込み</summary>
	<img src="https://github.com/user-attachments/assets/2b70f348-e4cc-46f1-9382-a1ef935f4d9d" style="width:420px"><br>
 	記事はカテゴリーごとに絞り込んで表示することができます。
</details>
<details>
	<summary>記事管理</summary>
	<img src="https://github.com/user-attachments/assets/a350fa0a-2441-4860-b3b4-7aa60e66189f" style="width:420px"><br>
	記事一覧を表示し、記事のステータスを確認でいます。編集や削除のボタンを押すと、それぞれの専用画面に移動します。
</details>
<details>
	<summary>カテゴリー管理</summary>
	<img src="https://github.com/user-attachments/assets/cfe6b318-e8dd-49cf-a0b2-b551b0777c78" style="width:420px"><br>
	記事を作成する際に設定するカテゴリーは、この画面で追加や削除できます。
</details>
<details>
	<summary>目次自動作成</summary>
	<img src="https://github.com/user-attachments/assets/f31d3944-de94-4175-89c8-db326afe52af" style="width:330px"><br>
	記事内のHタグを基に、自動で目次が作成されます。目次の項目を押すと、該当セクションに画面がスクロールします。
</details>

<details>
<summary>記事作成</summary>
<img src="https://github.com/user-attachments/assets/fe9c6a1d-a700-4422-96da-a6e9e0260317" style="width:420px">
<img src="https://github.com/user-attachments/assets/7b92ee5e-b2b8-496c-89b6-c98a182dac28" style="width:420px"><br>
記事作成画面には各種ツールが用意されており、それを活用することで簡単に記事を作成できます。
	
#### メタデータ追加

<img src="https://github.com/user-attachments/assets/ec311043-17af-4006-88c9-d7b946fdb95b" style="width:200px"><br>
`+`ボタンを押すと、入力欄がどんどん追加されます。その後、メタデータ追加ボタンを押すと、入力欄に記入したメタデータ情報が全て保存されます。また、各メタデータの右側にある`-`ボタンを押すことで、不要なメタデータを削除することもできます。

#### 画像挿入

<img src="https://github.com/user-attachments/assets/40cc7f67-f5e5-4225-9a53-34552578e08d" style="width:420px"><br>
画像追加タブで画像を追加すると、その画像は画像リストタブに表示されます。そして、画像リストから画像を選択し、画像タグ追加ボタンを押すと、選択した画像が本文に追加されます。

#### スタイル付き文章挿入

<img src="https://github.com/user-attachments/assets/cd768497-8ce1-4737-a479-856740c172b6" style="width:420px">
<img src="https://github.com/user-attachments/assets/94966325-9597-40ff-93ae-ce876a950d11" style="width:420px"><br>
スタイルを選んで文を入力すると、スタイルプレビューエリアにその文がどのように表示されるかがリアルタイムで確認できます。入力ボタンを押すと、プレビューエリアのスタイルが適用された文が本文に追加されます。

#### 記事プレビュー

<img src="https://github.com/user-attachments/assets/39c4b771-d0e0-4f09-9426-de8a1c0786a8" style="width:420px">
<img src="https://github.com/user-attachments/assets/04bada4a-b4a9-4e5f-bfd2-b2df244ad418" style="width:420px"><br>
公開される記事の実際の形をプレビューで確認できます。また、Editタブでは本文のHTMLコードを確認でき、直接コードを修正することも可能です。

</details>
