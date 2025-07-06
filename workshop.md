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

Positive
: **ヒント**: Codespacesを使用すると、ブラウザ上でVS Codeと同じ環境が立ち上がり、すぐに開発を始められます。

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

Positive
: **ヒント**: `Tab`キーで提案を受け入れ、`Alt+]`で次の提案を見ることができます。

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

Positive
: **重要**: Next Edit Suggestionの提案が表示されるまでに、少し時間がかかることがあります。焦らず待ってみてください。

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

- この機能は GitHub Copilot の有料サブスクリプションが必要です
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

Positive
: **ヒント**: ファイル名の前に `#` を付けることで、そのファイル全体をコンテキストとして含めることができます。

### 特定の機能について聞く

```
このコードのイベントシステムの仕組みを詳しく説明してください。
```

## コードの改善箇所を尋ねる
Duration: 15

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

### エージェントとは

GitHub Copilot のエージェント機能は、特定のタスクに特化したAIアシスタントです。

### 利用可能なエージェント

- `@workspace` - ワークスペース全体の理解
- `@vscode` - VS Code の操作
- `@terminal` - ターミナルコマンドの支援

### エージェントを使ってみる

Chatで以下のコマンドを試してみましょう：

```
@workspace このプロジェクトの構成を教えてください
```

```
@vscode Python用の便利な拡張機能を教えてください
```

## ポモドーロタイマーを作ってみよう
Duration: 30

### プロジェクトの概要

ポモドーロテクニック用のタイマーアプリケーションを作成します。

### 必要な機能
- 25分の作業タイマー
- 5分の休憩タイマー
- タイマーの開始・停止・リセット
- 音声通知

## ポモドーロタイマーの設計を考える
Duration: 10

### 設計をCopilotと一緒に考える

Chatで以下のように質問してみましょう：

```
ポモドーロタイマーアプリを作りたいです。どのような設計にすればよいでしょうか？PythonとTkinterを使用したいと思います。
```

### 技術選定

```
Pythonでタイマーアプリを作る場合、どのライブラリがおすすめですか？GUI、音声再生、設定保存の観点から教えてください。
```

## やることを洗い出そう
Duration: 10

### タスクの整理

Copilot Chatで以下のように依頼してみましょう：

```
ポモドーロタイマーアプリの開発において、必要なタスクを整理してください。優先順位も含めて教えてください。
```

### ファイル構成の検討

```
このアプリケーションのファイル構成はどうすればよいでしょうか？保守性を考慮した構成を提案してください。
```

## 実装しよう
Duration: 30

### メインアプリケーションの作成

Copilot Chatで以下のように依頼：

```
ポモドーロタイマーのメインアプリケーションを作成してください。Tkinterを使用し、以下の機能を含めてください：
- タイマー表示
- スタート/ストップボタン
- リセットボタン
- 作業時間と休憩時間の切り替え
```

### 段階的な実装

1. まず基本的なGUIを作成
2. タイマー機能を追加
3. 音声通知機能を追加
4. 設定保存機能を追加

### コードの生成と改良

各機能について、Copilotに実装を依頼し、提案されたコードを確認・改良していきます。

## テストを書こう
Duration: 20

### テストの重要性

Copilot Chatでテストについて質問：

```
作成したポモドーロタイマーアプリのテストを書きたいです。どのようなテストが必要でしょうか？Pythonのunittestを使用したいと思います。
```

### テストコードの生成

```
タイマークラスの単体テストを作成してください。時間の計算、状態の管理、イベントの発火などをテストしたいです。
```

### テストの実行

生成されたテストコードを実行して、アプリケーションが正しく動作することを確認します。

## 残りの機能を実装しよう
Duration: 20

### 追加機能の実装

基本機能が完成したら、以下の追加機能を実装してみましょう：

```
ポモドーロタイマーに以下の機能を追加したいです：
- 設定ファイルでタイマー時間をカスタマイズ
- 統計機能（完了したポモドーロ数の記録）
- システムトレイ対応
- 通知音のカスタマイズ
```

### 機能の優先順位付け

```
これらの機能の実装優先順位を決めたいです。ユーザー体験の向上と開発工数を考慮して提案してください。
```

### 段階的な実装

優先度の高い機能から順番に実装していきます。

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