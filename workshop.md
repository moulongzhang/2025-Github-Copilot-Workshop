author: Your Name
summary: GitHub Copilot ワークショップ
id: github-copilot-workshop
categories: AI, Development
environments: Web
status: Published
feedback link: https://example.com/feedback

# GitHub Copilot ワークショップ

## ワークショップについて
Duration: 5

GitHub Copilotワークショップへようこそ！このワークショップでは、GitHub Copilot を使ってコードの解説や改善を行う方法を学びます。
GitHub Copilot Chat は Chat 体験を通じて AI との対話を行うことができます。 ぜひ、このワークショップを通じて GitHub Copilot の使い方を学んでみましょう。

![GitHub Copilot Logo](github-copilot-workshop/img/octocat_copilot.png)

### 本日のゴール
- GitHub Copilotの各種機能を理解する
- エージェントモードを使って、新規にアプリケーションを開発する

### 前提条件
- Visual Studio Code がインストールされていること
- GitHub Copilotのライセンスがあること
- GitHubアカウントを持っていること

## プロジェクトのセットアップ
Duration: 15

このワークショップでは、以下のGitHubリポジトリを使用します：

**プロジェクトURL**: https://github.com/moulongzhang/20250708-Python-Project

### セットアップ方法

以下のいずれかの方法でプロジェクトを開始できます：

### 方法1: GitHub Codespacesを使用する（推奨）

1. 上記のプロジェクトURLをブラウザで開く
2. 緑色の **Code** ボタンをクリック
3. **Codespaces** タブを選択
4. **Create codespace on main** をクリック

![Codespaces Setup](github-copilot-workshop/img/github-codespaces.png)

> aside positive
>
> **ヒント**: Codespacesを使用すると、ブラウザ上でVS Codeと同じ環境が立ち上がり、すぐに開発を始められます。


### 方法2: ローカル環境でクローンする

ローカルにVS Codeがインストールされている場合：

1. ターミナルまたはコマンドプロンプトを開く
2. 以下のコマンドでリポジトリをクローン：

```bash
git clone https://github.com/moulongzhang/20250708-Python-Project.git
```

3. クローンしたディレクトリに移動：

```bash
cd 20250708-Python-Project
```

4. VS Codeでプロジェクトを開く：

```bash
code .
```

### 必要な拡張機能のインストール

プロジェクトを開いたら、以下の拡張機能をインストールしてください：

1. **GitHub Copilot** 拡張機能をインストール
2. **GitHub Copilot Chat** 拡張機能をインストール
3. **Python** 拡張機能をインストール

### 設定確認

1. VS CodeでGitHubアカウントにサインインが完了していることを確認
2. Copilot機能が有効になっていることを確認
3. Pythonインタープリターが正しく設定されていることを確認

## コード補完を使ってみる
Duration: 10

GitHub Copilotの基本的なコード補完機能を体験してみましょう。

### Copilot拡張機能のインストール

1. **GitHub Copilot** 拡張機能をインストール
2. **GitHub Copilot Chat** 拡張機能をインストール

### 設定確認
VS Codeでサインインが完了していることを確認してください。

### コード補完を試してみる

新しいPythonファイルを作成して、以下のコメントを入力してみましょう：

```python
# Fibonacci数列を計算する関数
def fibonacci(n):
```

Copilotが自動的にコードを提案してくれることを確認してください。

> aside positive
>
> **ヒント**: `Tab`キーで提案を受け入れ、`Alt+]`で次の提案を見ることができます。

## GitHub Copilot Next Edit Suggestions 有効化手順
Duration: 10

### 概要
⚙️ [`github.copilot.nextEditSuggestions.enabled`](vscode://settings/github.copilot.nextEditSuggestions.enabled) は、GitHub Copilotの次世代編集提案機能を有効にする設定です。この機能により、より高度なコード編集の提案を受け取ることができます。

### 1. VS Codeを開く

### 2. 設定画面にアクセス
以下のいずれかの方法で設定画面を開きます：

#### 方法A: メニューから
- **Windows/Linux**: `File` → `Preferences` → `Settings`
- **macOS**: `Code` → `Settings...` → `Settings`

#### 方法B: キーボードショートカット
- **Windows/Linux**: `Ctrl + ,`
- **macOS**: `Cmd + ,`

#### 方法C: コマンドパレット
- `Ctrl + Shift + P` (Windows/Linux) または `Cmd + Shift + P` (macOS)
- `Preferences: Open Settings (UI)` を選択

### 3. 設定を検索
設定画面の検索ボックスに以下を入力：
```
github.copilot.nextEditSuggestions.enabled
```

### 4. 設定を有効化
- 検索結果に表示される設定項目のチェックボックスをオンにする
- または、`false` を `true` に変更する

### 5. 設定の確認
設定が正しく適用されているか確認：
- VS Codeを再起動（推奨）
- エディタでコードを編集して、新しい提案機能が動作するか確認

### 代替方法: settings.jsonで直接編集

#### 1. settings.jsonファイルを開く
- `Ctrl + Shift + P` (Windows/Linux) または `Cmd + Shift + P` (macOS)
- `Preferences: Open User Settings (JSON)` を選択

#### 2. 設定を追加
```json
{
    "github.copilot.nextEditSuggestions.enabled": true
}
```

#### 3. ファイルを保存
- `Ctrl + S` (Windows/Linux) または `Cmd + S` (macOS)

### 実際に試してみよう

プロジェクトに含まれている `point.py` ファイルを開いてください。このファイルには、二次元空間の点を表すクラスが含まれています：

```python
import math

class Point2D:
    def __init__(self, x, y):
        self.x = x
        self.y = y
    
    def distance_to(self, other):
        dx = self.x - other.x
        dy = self.y - other.y
        return math.sqrt(dx * dx + dy * dy)
    
    def __str__(self):
        return f"Point2D({self.x}, {self.y})"
```

今、このクラスを三次元空間の点を表すクラスに拡張したいと考えています。まずは、クラス名を手動で `Point3D` に変更してみましょう。すると、GitHub Copilotが次の編集候補を提案してくれます。

> aside positive
>
> **重要**: Next Edit Suggestionの提案が表示されるまでに、少し時間がかかることがあります。焦らず待ってみてください。

提案では以下のような変更が示されるはずです：
- `__init__`メソッドに `z` パラメータの追加
- `self.z = z` の追加
- `distance_to`メソッドでの三次元距離計算への拡張
- `__str__`メソッドでのz座標の表示

この状態で `Tab` キーを押すと、GitHub Copilotが提案をしている箇所にカーソルが移動します。そこで、提案を受け入れるには、再度 `Tab` キーを押します。

すると、GitHub Copilotは次の編集候補を提案してくれるはずです。この提案も、`Tab` キーを押すことで受け入れることができます。このように、Next Edit Suggestionを使うことで、コードの編集を効率的に行うことができます。

### 結果を見てみよう

Point2DクラスをPoint3Dに拡張する作業を続けてみましょう。すべてのメソッドを三次元空間に対応させることができるはずです。

期待される最終的なコードの例：

```python
import math

class Point3D:
    def __init__(self, x, y, z):
        self.x = x
        self.y = y
        self.z = z
    
    def distance_to(self, other):
        dx = self.x - other.x
        dy = self.y - other.y
        dz = self.z - other.z
        return math.sqrt(dx * dx + dy * dy + dz * dz)
    
    def __str__(self):
        return f"Point3D({self.x}, {self.y}, {self.z})"
```

### TODOコメント付きのコードでも試してみましょう

１行目でコメントアウトされている`二次元`を `三次元`に置き換えてください。

```python
# 二次元空間の点を表すクラス
class Point2D:
    def __init__(self, x, y):
        self.x = x
        self.y = y
    
    def distance_to(self, other):
        # TODO: ここに距離計算のコードを追加
        pass
    
    def __str__(self):
        # TODO: 文字列表現を返す
        pass
```

TODOコメントの後にカーソルを置いて、Copilotの提案を確認してみてください。

### 注意事項

- VS Code の GitHub Copilot 拡張機能が最新版にアップデートされていることを確認してください
- 設定変更後は VS Code の再起動を推奨します

### トラブルシューティング

#### 設定が見つからない場合
1. GitHub Copilot 拡張機能がインストールされているか確認
2. 拡張機能が最新版にアップデートされているか確認
3. VS Code を再起動してから再度試行

#### 機能が動作しない場合
1. GitHub Copilot にログインしているか確認
2. インターネット接続を確認
3. VS Code のコンソールでエラーメッセージを確認

## Copilot Chat ハンズオンの準備
Duration: 5

### ファイルを作成

下記のファイルを `delivery_manager.py` として保存してください。

```python
import time
import random
from typing import List, Callable, Optional
from dataclasses import dataclass, field
from enum import Enum


class EventArgs:
    """イベント引数の基底クラス"""
    pass


class Event:
    """C#のeventに相当するクラス"""
    
    def __init__(self):
        self._handlers: List[Callable] = []
    
    def add_handler(self, handler: Callable):
        """イベントハンドラーを追加"""
        if handler not in self._handlers:
            self._handlers.append(handler)
    
    def remove_handler(self, handler: Callable):
        """イベントハンドラーを削除"""
        if handler in self._handlers:
            self._handlers.remove(handler)
    
    def invoke(self, sender, args: EventArgs = None):
        """イベントを発火"""
        for handler in self._handlers:
            handler(sender, args or EventArgs())


@dataclass
class KitchenObjectSO:
    """キッチンオブジェクトのデータクラス"""
    name: str
    object_id: int


@dataclass
class RecipeSO:
    """レシピのデータクラス"""
    name: str
    kitchen_object_so_list: List[KitchenObjectSO] = field(default_factory=list)


@dataclass
class RecipeListSO:
    """レシピリストのデータクラス"""
    recipe_so_list: List[RecipeSO] = field(default_factory=list)


class PlateKitchenObject:
    """皿のキッチンオブジェクト"""
    
    def __init__(self):
        self._kitchen_object_so_list: List[KitchenObjectSO] = []
    
    def add_kitchen_object(self, kitchen_object: KitchenObjectSO):
        """キッチンオブジェクトを追加"""
        self._kitchen_object_so_list.append(kitchen_object)
    
    def get_kitchen_object_so_list(self) -> List[KitchenObjectSO]:
        """キッチンオブジェクトリストを取得"""
        return self._kitchen_object_so_list.copy()


class KitchenGameManager:
    """キッチンゲームマネージャー（Singleton）"""
    
    _instance: Optional['KitchenGameManager'] = None
    
    def __init__(self):
        self._is_game_playing = False
    
    @classmethod
    def get_instance(cls) -> 'KitchenGameManager':
        """Singletonインスタンスを取得"""
        if cls._instance is None:
            cls._instance = cls()
        return cls._instance
    
    def is_game_playing(self) -> bool:
        """ゲームが進行中かどうか"""
        return self._is_game_playing
    
    def start_game(self):
        """ゲーム開始"""
        self._is_game_playing = True
    
    def stop_game(self):
        """ゲーム停止"""
        self._is_game_playing = False


class DeliveryManager:
    """配達管理クラス（Python版）"""
    
    _instance: Optional['DeliveryManager'] = None
    
    def __init__(self, recipe_list_so: RecipeListSO):
        # イベント定義
        self.on_recipe_spawned = Event()
        self.on_recipe_completed = Event()
        self.on_recipe_success = Event()
        self.on_recipe_failed = Event()
        
        # プライベート変数
        self._recipe_list_so = recipe_list_so
        self._waiting_recipe_so_list: List[RecipeSO] = []
        self._spawn_recipe_timer = 0.0
        self._spawn_recipe_timer_max = 4.0
        self._waiting_recipes_max = 4
        self._successful_recipes_amount = 0
        self._last_update_time = time.time()
    
    @classmethod
    def get_instance(cls, recipe_list_so: RecipeListSO = None) -> 'DeliveryManager':
        """Singletonインスタンスを取得"""
        if cls._instance is None:
            if recipe_list_so is None:
                raise ValueError("初回作成時にはrecipe_list_soが必要です")
            cls._instance = cls(recipe_list_so)
        return cls._instance
    
    def update(self):
        """フレーム更新処理（UnityのUpdate相当）"""
        current_time = time.time()
        delta_time = current_time - self._last_update_time
        self._last_update_time = current_time
        
        self._spawn_recipe_timer -= delta_time
        
        if self._spawn_recipe_timer <= 0.0:
            self._spawn_recipe_timer = self._spawn_recipe_timer_max
            
            kitchen_game_manager = KitchenGameManager.get_instance()
            if (kitchen_game_manager.is_game_playing() and 
                len(self._waiting_recipe_so_list) < self._waiting_recipes_max):
                
                # ランダムにレシピを選択
                waiting_recipe_so = random.choice(self._recipe_list_so.recipe_so_list)
                self._waiting_recipe_so_list.append(waiting_recipe_so)
                
                # イベント発火
                self.on_recipe_spawned.invoke(self)
    
    def deliver_recipe(self, plate_kitchen_object: PlateKitchenObject):
        """レシピの材料と皿の材料が一致しているかどうかを確認する"""
        
        for i, waiting_recipe_so in enumerate(self._waiting_recipe_so_list):
            plate_ingredients = plate_kitchen_object.get_kitchen_object_so_list()
            
            # 材料数が一致するかチェック
            if len(waiting_recipe_so.kitchen_object_so_list) == len(plate_ingredients):
                plate_contents_matches_recipe = True
                
                # レシピの各材料をチェック
                for recipe_kitchen_object_so in waiting_recipe_so.kitchen_object_so_list:
                    ingredient_found = False
                    
                    # 皿の材料と照合
                    for plate_kitchen_object_so in plate_ingredients:
                        if plate_kitchen_object_so == recipe_kitchen_object_so:
                            ingredient_found = True
                            break
                    
                    if not ingredient_found:
                        plate_contents_matches_recipe = False
                        break
                
                # 材料が完全に一致した場合
                if plate_contents_matches_recipe:
                    self._successful_recipes_amount += 1
                    self._waiting_recipe_so_list.pop(i)
                    
                    # 成功イベント発火
                    self.on_recipe_completed.invoke(self)
                    self.on_recipe_success.invoke(self)
                    return
        
        # 一致するレシピが見つからなかった場合
        self.on_recipe_failed.invoke(self)
    
    def get_waiting_recipe_so_list(self) -> List[RecipeSO]:
        """待機中のレシピリストを取得"""
        return self._waiting_recipe_so_list.copy()
    
    def get_successful_recipes_amount(self) -> int:
        """成功したレシピ数を取得"""
        return self._successful_recipes_amount


# 使用例
if __name__ == "__main__":
    # サンプルデータ作成
    tomato = KitchenObjectSO("Tomato", 1)
    lettuce = KitchenObjectSO("Lettuce", 2)
    bread = KitchenObjectSO("Bread", 3)
    
    # サンプルレシピ
    sandwich_recipe = RecipeSO("Sandwich", [bread, lettuce, tomato])
    salad_recipe = RecipeSO("Salad", [lettuce, tomato])
    
    recipe_list = RecipeListSO([sandwich_recipe, salad_recipe])
    
    # ゲームマネージャーとデリバリーマネージャーを初期化
    game_manager = KitchenGameManager.get_instance()
    game_manager.start_game()
    
    delivery_manager = DeliveryManager.get_instance(recipe_list)
    
    # イベントハンドラーの設定
    def on_recipe_spawned(sender, args):
        print("新しいレシピが生成されました！")
    
    def on_recipe_success(sender, args):
        print("レシピ配達成功！")
    
    def on_recipe_failed(sender, args):
        print("レシピ配達失敗...")
    
    delivery_manager.on_recipe_spawned.add_handler(on_recipe_spawned)
    delivery_manager.on_recipe_success.add_handler(on_recipe_success)
    delivery_manager.on_recipe_failed.add_handler(on_recipe_failed)
    
    # サンプル実行
    print("ゲーム開始...")
    
    # 5秒間更新処理を実行
    start_time = time.time()
    while time.time() - start_time < 5:
        delivery_manager.update()
        time.sleep(0.1)  # 100ms間隔で更新
    
    print(f"待機中のレシピ数: {len(delivery_manager.get_waiting_recipe_so_list())}")
    
    # サンプル配達テスト
    plate = PlateKitchenObject()
    plate.add_kitchen_object(bread)
    plate.add_kitchen_object(lettuce)
    plate.add_kitchen_object(tomato)
    
    print("サンドイッチを配達...")
    delivery_manager.deliver_recipe(plate)
    
    print(f"成功したレシピ数: {delivery_manager.get_successful_recipes_amount()}")
```

## コードを解説してもらう
Duration: 15

Copilot Chat にこのコードを解説させてみましょう。

### Copilot Chat を開く

1. VS Codeのサイドバーで **Chat** アイコン（チャットバブルのアイコン）をクリックして、Copilot Chat を開きます
2. または `Ctrl+Alt+I` (macOSでは `Cmd+Alt+I`) でChatパネルを開く

### チャットモードの確認

チャットのモードが「質問」になっていることを確認します（「エージェント」モードは後ほど紹介します）。

### /explain コマンドを使用

1. チャット欄に `/explain` と入力します
2. そうすると、チャット欄に `/explain` コマンドが展開され、候補として **@workspace /explain** と **@termianl /explain** が表示されます
3. **@workspace /explain** を選択し、`#delivery_manager.py` と入力します。
4. Enterを押すと、Copilot Chat が `delivery_manager.py` ファイル全体を解説してくれます

> aside positive
>
> **ヒント**: ファイル名の前に `#` を付けることで、そのファイル全体をコンテキストとして含めることができます。

## コードの改善箇所を尋ねる
Duration: 15

### エクササイズ

Copilot Chat にこのコードの悪い部分を尋ねてみましょう。

### 1. クラス全体の問題を聞く

まずは、クラス全体としてこのコードはどのような問題を抱えているか聞いてみましょう。

Copilot Chatに以下のように質問してみてください：

```
このDeliveryManagerクラス全体を見て、どのような問題や改善点がありますか？設計パターン、コードの品質、保守性の観点から教えてください。
```

### 2. 具体的なメソッドに絞って改善点を聞く

その後、`deliver_recipe()` メソッドに絞って、このメソッドを改善するためにはどのような方法があるか聞いてみましょう。

#### 手順：
1. チャット欄に `#deliver_recipe` と入力します
2. コードの要素（関数、クラス、変数など）の候補が表示されます
3. `deliver_recipe` メソッドを選択します
4. 以下の質問を入力してください：

```
このdeliver_recipeメソッドを改善するためにはどのような方法がありますか？可読性、パフォーマンス、エラーハンドリングの観点から提案してください。
```

> aside positive
>
> **ヒント**: `#` を使うことで、特定のコードの要素に対してピンポイントで質問することができます。これにより、より具体的で有用な改善提案を得ることができます。

### コードレビュー機能

現在のコードを改善するために、Copilot Chatに以下のように質問してみましょう：

```
このPythonコードを改善してください。パフォーマンス、可読性、エラーハンドリングの観点から提案をお願いします。
```

### セキュリティの観点から確認

```
このコードにセキュリティ上の問題はありますか？
```

### ベストプラクティスの確認

```
Pythonのベストプラクティスに従っているか確認してください。
```

## エージェントモードを使ってみよう
Duration: 10

ここまでは「質問」モードでCopilot Chatを使ってきましたが、次は「エージェント」モードを使ってみましょう。エージェントは、ユーザーの意図を理解し、より自律的にタスクを実行することができます。実例を通して、エージェントがどのように機能するかを学びます。

### エージェントモードへの切り替え

まず `delivery_manager.py` ファイルを開いている状態で、Copilot Chatのモード選択から「エージェント」を選択します。

<div align="center">
  <img src="github-copilot-workshop/img/agent_mode2.png" alt="エージェントモード選択2" width="600" />
  
  <div style="height: 24;"></div>
  
  <img src="github-copilot-workshop/img/agent_mode.png" alt="エージェントモード選択" width="600" />
</div>

### 問題点の洗い出し

その後、以下のプロンプトを入力してみましょう。

```
DeliveryManagerクラスに存在する問題点を列挙してください。そして、それぞれの問題点を解決するための改善案を提示してください。
```

![GPT-4.1による問題点分析](github-copilot-workshop/img/agent_GPT4.1.png)

すると、複数の改善点を提案してくれるはずです。

### モデルを変えて試してみてください

同じ質問を異なるモデルで試すことで、各モデルの特徴を比較できます。

![Claude 4.0による問題点分析](github-copilot-workshop/img/agent_Calude4.0.png)

### 改善案の実装

では、実際に提案してもらった改善案を実装してもらいましょう。

```
提示してくれたすべての改善案を実装してください。
```

すると、Copilotはエディタで開かれているコードに対して直接コードの変更を行います。しかし、これはまだ提案の段階であり、この変更を受け入れるかどうかはユーザーが決定します。受け入れるかどうかは、チャット欄の上にある「保持」もしくは「元に戻す」ボタンをクリックすることで行います。

### エージェントの自律性

ここで、エージェントが返してくれたコメントを確認してみましょう。エージェントは単に指示に従ってコードを変更しただけでなく、コードを変更後にエラーが発生していることを確認し、そのエラーも修正しようとする場合があります。適切な環境下では、エージェントはコードの変更後に発生したエラーを自動的に検出し、修正を試みます。このように、エージェントはユーザーの意図を理解し、より自律的にタスクを実行することができます。

### コマンド実行の確認

エージェントモードを使っていると、Copilotがコマンドを実行して良いかどうかを尋ねてくることがあります。これは、Copilotが何かのコマンドを実行する前に、必ずユーザーに確認を求めるためです。コマンドの内容を確認し、実行しても問題ない場合は「Allow this time」をクリックします。これにより、Copilotはそのコマンドを実行し、必要な変更を行います。

> aside positive
>
> **重要**: エージェントモードでは、Copilotがより自律的に動作するため、提案される変更内容をよく確認してから受け入れるようにしましょう。

## ポモドーロタイマーを作ってみよう
Duration: 30

ここまでで、VS Code上で利用できるGitHub Copilotの基本的な使い方を学びました。次は、実際にアプリケーションを開発してみましょう。

今回のハンズオンでは、ポモドーロタイマーアプリケーションを開発します。このアプリケーションは、作業時間と休憩時間を設定し、タイマーを管理する機能を持っています。

以下のようなUIを持つアプリケーションを作成することを目指します。

![ポモドーロタイマーUI](github-copilot-workshop/img/pomodoro.png)

では、まずVS Code上で、新しいPythonファイルを作成しましょう。今回はWebアプリケーションとして作成したいので、Flaskを使用します。メインファイル名は「app.py」としましょう。

### プロジェクトの概要

ポモドーロテクニック用のWebタイマーアプリケーションを作成します。

### 必要な機能
- 25分の作業タイマー
- 5分の休憩タイマー
- タイマーの開始・停止・リセット
- 進捗表示と統計機能
- ブラウザ通知とサウンド通知
- レスポンシブなWebUI

## ポモドーロタイマーの設計を考える
Duration: 10

まず、いきなり実装を始めるのではなく、どういった方針・設計で進めるかをCopilotに相談してみましょう。ここから先は、すべてエージェントモードで進めていきます。

今回のようにUIを持ったWebアプリケーションを作成するにあたって役に立つのが、Copilot Chatに画像をアップロードする機能です。これを使うことで、アプリケーションのUIイメージをCopilotに理解させることができます。

前ページのUIイメージをまずはプロジェクトのルートに `pomodoro.png` として保存してください。その後、チャット欄の `Add Context` をクリックし、「Image from Clipboard」または「Files & Folders...」を選択します。そして、UIイメージの画像を選択します。

![VS Code Copilot Chat Context Menu](github-copilot-workshop/img/add_context2.png)

![VS Code Copilot Chat Context Menu](github-copilot-workshop/img/add_context3.png)

画像のアップロードができたら、Copilot Chatに画像が表示されます。

その上で、次のプロンプトを入力してみましょう。

```
このプロジェクトでポモドーロタイマーのWebアプリを作成する予定です。添付の画像はそのアプリのUIモックです。FlaskとHTML/CSS/JavaScriptを使用してこのアプリを作成するにあたって、どのような設計で進めるべきか、アーキテクチャの提案をしてください。
```

すると、推奨のWebアプリケーションアーキテクチャを提案してくれます。

このアーキテクチャに対して、もっとこうした方が良いという点や考慮不足の点があれば、それを指摘してみましょう。例えば次のような指摘です。

```
ユニットテストのしやすさという点を考慮して、今のアーキテクチャにもし改善や追加が必要な点があればそれも書き出してください。
```

このやり取りを経て、アーキテクチャの設計が固まったら、一度その内容をファイルに保存してもらいましょう。そうすることで、別のチャットセッションを開いても、同じアーキテクチャの内容を参照することができます。

```
ここまでの会話でアーキテクチャについては固まったので、これまでの会話の内容を踏まえて、プロジェクトのルートにarchitecture.mdというファイルに、Webアプリケーションアーキテクチャ案をまとめてください。
```

> aside positive
>
> Copilot Chatでのやりとりに一区切りがついたら、新しい会話を始めることで、よりCopilotに対して明確な指示を与えることができます。新しい会話を始めるには、チャットウィンドウの上部にある「新しい会話」ボタンをクリックします。その際、今回のアーキテクチャの内容のように、今後のチャットでも参照したい内容は、今回のようにファイルに書き出して保存しておくと便利です。



## やることを洗い出そう
Duration: 10

ここまでで、UIモックとアーキテクチャの設計が固まりました。具体的にどのような機能を実装する必要があるかを検討していきましょう。これもCopilot Chatに相談してみます。その際、pomodoro.pngとarchitecture.mdを添付しましょう。

```
このポモドーロタイマーアプリケーションを作成するにあたって、実装する必要のある機能を洗い出してください。
```

<img src="github-copilot-workshop/img/pomodoro.png" alt="機能一覧の検討" width="400" />

![機能洗い出しの例](github-copilot-workshop/img/10-2.list_features.png)

この内容もCopilotとのチャットを通して、改善していきましょう。内容が固まったら、アーキテクチャの時と同様にこの内容もfeatures.mdというファイルにまとめて保存しておきましょう。

```
ありがとうございます。その内容で良さそうなので、実装する必要のある機能一覧をfeatures.mdというファイルに書いてください。
```

では、ここから実装を始めるわけですが、Copilotを使いこなすコツとしては、一度に大きな機能を実装しようとするのではなく、まずは小さな機能から実装していくことです。これにより、Copilotが提案するコードの精度が上がり、よりスムーズに開発を進めることができます。

今回のアプリケーション開発を、どのような粒度で細分化して実装していくかについても、Copilotに相談してみましょう。ここでは、pomodoro.png、architecture.md、features.mdを添付しましょう。

```
このポモドーロタイマーアプリケーションを段階的に実装していきたいと考えています。添付の画像とアーキテクチャ、機能一覧を踏まえて、どのような粒度で機能を実装していくべきか、段階的な実装計画を提案してください。
```

私が試したところ、6つのステップからなる計画を提案してくれました。この点についても、もっとこうしてほしいなどがあれば、Copilotに指摘してみましょう。そして、この内容も後で参照できるように、plan.mdというファイルにまとめて保存しておきましょう。その際、どういうプロンプトで指示するべきかは、みなさん自身で考えてみてください。

## 実装しよう
Duration: 30

ここまでの準備が整ったので、いよいよ実装に取り掛かりましょう。前のステップで提案された実装計画に従って、段階的に機能を実装していきます。

### プロジェクト構成の準備

まずは、今回のアーキテクチャに従ったプロジェクトのディレクトリ構成を作成しましょう。

まずは、`architecture.md` のようなアーキテクチャを実現するにあたって、現在のプロジェクトのフォルダ構成を修正してください。必要に応じてファイルの移動や、設定ファイルの変更も行ってください。

その後、`pomodoro.png`, `architecture.md`, `plan.md` を添付した上で、次のようにCopilotに指示を出してみましょう。

```
plan.mdのステップ１を実装してください。その際、すでにこのプロジェクトにあるファイルを別のディレクトリに移動する必要があれば、その作業も実行してください。もし追加で考慮が必要なことがあれば、私に質問してください。
```

すると、私のケースでは以下のように検討が必要な質問をしてきました。こういった場合には、必要な情報を提供しましょう。

![Copilotからの質問例](github-copilot-workshop/img/12-0.question_from_copilot.png)

その後、Copilotは、ステップ1の実装を行います。実装が完了したら、Copilotは自らの判断でプロジェクトのビルドを行い、エラーがないかを確認します。エラーが発生した場合は、そのエラーを解決するために追加で修正を行います。このような自律的な動作が、エージェントモードの特徴です。

実装が完了したら、以下の点を確認してみましょう：

1. **ディレクトリ構造**：推奨されたアーキテクチャに沿った構成になっているか
2. **基本ファイル**：必要な基本ファイル（app.py、HTML テンプレート、CSS ファイルなど）が作成されているか
3. **動作確認**：簡単な動作テストを行って、エラーが発生していないか


以下が、私の場合のステップ1の実装結果です。この段階でどのようなアプリケーションになっているかは人によって異なるでしょう。


![ステップ1実装結果例](github-copilot-workshop/img/12-1.completed_timer.png)




## テストを書こう
Duration: 20

このまま実装を続ける前に、実装した機能に対してユニットテストを書いておきましょう。ユニットテストを書くことで、後のステップでの変更が既存の機能に影響を与えないことを確認できます。

もし前ページの段階でユニットテストも実装されている場合は、このページは読み飛ばしてください。

### テストの実装

次のようなプロンプトを実行してみましょう。

```
現在の実装に対して、ユニットテストが全くないので、ユニットテストを実装してください。
```

すると、Copilotエージェントはユニットテスト用の依存関係をインストールするために、コマンドを使って良いかどうかを尋ねてきます。このように、エージェントが何かのコマンドを実行する前には、必ずユーザーに確認を求めます。ここでは、必要なコマンドを実行することを許可するために、「Continue」をクリックします。

![Copilotによるテスト実装確認](github-copilot-workshop/img/13-0.test_for_step1.png)

すると、CopilotはVS Code内のターミナル内で、先ほどのコマンドを実行し、必要な依存関係をインストールします。それ以降も同様に、Copilotが何かのコマンドを実行する前には、必ずユーザーに確認を求めます。もし、そのコマンドを実行してエラーが発生した場合は、そのエラーを解決するために、エージェントは追加の修正を行います。


## 残りの機能を実装しよう
Duration: 20

ここからは、自由課題として、残りの機能を段階的に実装していきましょう。

いくつか役に立つであろうポイントをここでは紹介します。

### UIに対して指示をしたい場合

UI上の特定の要素に対して指示を出したい場合は、UIのスクリーンショットをCopilotにアップロードすることで、その要素を認識させることができます。その際、スクリーンショットの上に特に指摘したい箇所を丸で囲むなり、矢印を引くなりして、どの要素に対して指示を出したいのかを明確にすると良いでしょう。

または、現状のスクリーンショットと、期待するスクリーンショットを2枚アップロードすることで、その差分を確認してもらい、期待するUIにできるだけ近づくように指示を出すこともできます。

### 毎回同じような指示を出している場合

プロンプトを書いたり、文脈を指定する際に、頻繁に同じような指示を出している場合は、Copilotにその指示を覚えさせることができます。具体的には、プロジェクト内に `.github/copilot-instructions.md` というファイルを作成し、その中に指示を書いておきます。このファイルがあると、Copilotはその指示を自動的に読み込み、以降のチャットでその指示を参照することができます。

以下にカスタム指示のサンプルを示します。

```markdown
このプロジェクトは、ポモドーロタイマーをFlaskで実装するものです。

以下はプロジェクトの重要なファイルです。ユーザーの指示に対して、必要に応じてこれらのファイルを参照してください。
 - `pomodoro.png`: アプリケーションのUIモックです。
 - `architecture.md`: アプリケーションのアーキテクチャドキュメントです。
 - `features.md`: 実装する機能の一覧です。
 - `plan.md`: 段階的な実装計画です。
```

そのほかにも、プロジェクトをビルドするコマンドやテストを実行するコマンドなど、プロジェクトに特有のコマンドを記載しておくと、Copilotはそのコマンドを自動的に使用するようになります。

### なかなか実装が進まなかったり、バグを解決できない場合

このような場合には、以下のアプローチを試してみましょう。

- デバッグ情報を出力するように指示し、その出力をCopilotに分析させる。
- 他のモデルを試してみる。

## おめでとうございます 🎉
Duration: 5

### 今日学んだこと

このワークショップでは以下のことを学びました：

- GitHub Copilotの基本的な使い方
- Copilot Chatでのコード解説・改善
- エージェント機能の活用
- 実際のアプリケーション開発でのCopilot活用

### 次のステップ

- 実際のプロジェクトでCopilotを活用してみる
- より複雑なアプリケーション開発に挑戦する
- Copilotの新機能をキャッチアップする

### リソース

- [GitHub Copilot Documentation](https://docs.github.com/copilot)
- [GitHub Copilot ベストプラクティス](https://docs.github.com/copilot/using-github-copilot/best-practices-for-using-github-copilot)

お疲れさまでした！