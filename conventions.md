\mainmatter
\let\thesection\thesectionorig
\let\thesubsection\thesubsectionorig

# コーディング規約

![コーディング規約](./images/conventions.png)

Pythonコミュニティにはコードを記述するための幾つかの規約があります。
あなたが既にPythonプログラマである場合は既にこの規約について知っているかもしれませんが、規約にまだ慣れていない方のために、要点の説明と幾つかの参考URLを記載しておきます。

## PEPを読もう!
**PEP**はPythonの拡張提案文書です。これらの提案文書は幾つかのカテゴリに分類され、python.orgで公開されています。
PEPは付加的な仕様を定義したメタPEPとPython内部の技術的な改善を記述した技術PEPに分けられています。

コードを書くためのガイドラインの役目を持った文書としては、PEP 8やPEP257があります。
PEP 8はコーディングスタイルのガイドラインであり、PEP 257はメソッドのドキュメントを記述するdocstringsのためのガイドラインです。

### PEP 8: Pythonコードのスタイルガイド
PEP 8は公式なPythonコードのスタイルガイドガイドです。
Flaskアプリケーションを開発する際(に限りませんが)、このガイドをよく読んで準拠することを推奨します。
これにより、コードが数百行、数千行と膨れ上がり、多くのファイルに分割した場合でも読みやすさを維持することができます。
PEP 8の目的はコードの可読性を高めることです。
さらにプロジェクトがオープンソースソフトウェアである場合、PEP 8準拠することで貢献者がより快適にプロジェクトに参加できるようになります。

特に重要なのは、インデントに4スペースを利用することです。
タブを挿入してはいけません。
この規約に違反すると、あなたや他の開発者がプロジェクトを切り替える際に
面倒なことになるでしょう。
これはどのプログラミング言語にもある悩みの種ですが、Pythonではタブとスペースを混ぜるとエラーが発生してしまうので特に重要です。

### PEP 257: Docstring規約
PEP 257は**docstrings**について記述しています。
PEPを読んで頂いても構いませんが、以下の例を見ればdocstringがどの様なものか理解できるはずです。

~~~ {language="Python"}
def launch_rocket():
   """ロケット発射関数

   シートベルトを締めて、エンジンを起動します。
   """
   # [...]
~~~

docstringsはSphinxなどのソフトウェアを利用してHTMLやPDFフォーマットのドキュメントを生成出来ます。
このようなドキュメントはコードを理解するのに役立ちます。

**注記**

-   [PEP 8](http://legacy.python.org/dev/peps/pep-0008/)
-   [PEP 257](http://legacy.python.org/dev/peps/pep-0257/)
-   [Sphinx](http://sphinx-doc.org/)

## 相対インポート
相対インポートを利用すると、Flaskアプリの開発が少し楽になります。
単純な例として、モジュール*myapp/models.py*から`User`モデルをimportする
としましょう。
ここで、アプリケーションのパッケージ名を含めた`myapp.models`をimportす
る必要があると思うかもしれません。
相対インポートを利用すると、ソースディレクトリへの相対的な場所を示すこ
とが出来ます。

ドットは現在のディレクトリを表し、ドットが続く場合は親ディレクトリを表
します。
以下に例を示します。

~~~ {language="Python"}
# myapp/views.py

# An absolute import gives us the User model
from myapp.models import User

# A relative import does the same thing
from .models import User
~~~

この方法は、パッケージのモジュール性を高める利点があります。
例えば、他のプロジェクトのモジュールを再利用する際にパッケージ名を変更
する場合でも各import文を更新する必要はありません。

調べてみると、以下のtweetが見つかりました。

> パッケージの相対インポートを使ったら、1秒でパッケージ名を変更できたぜ
> 
> --- David Beazley (https://twitter.com/dabeaz/status/372059407711887360)

**注記**

相対インポートの詳しい構文が知りたい場合は以下の項目を参照して下さい。
[PEP328](http://www.python.org/dev/peps/pep-0328/#guido-s-decision).

## まとめ
- なるべくPEP 8のコーディングスタイルガイドに従いましょう。
- なるべくPEP 257に定義されたdocstringsでドキュメントを書きましょう。
- アプリケーション内部のモジュールでは相対インポートを利用しましょう。

