# クイックSQLを使用して新しいデータ構造を定義します

## 序章

データベース・オブジェクトを作成し、維持するためのSQLを記憶することは難しいかもしれません。しかし、省略記法やグラフィカル・ユーザー・インターフェースに基づいてコードを生成してくれるツールが存在します。このラボでは、Quick SQL でデータ構造を定義してテーブルとビューを作成する方法を学びます。

推定時間：15分

### 問題の定義

ほとんどの組織で、スプレッドシートが盛んに使われています。スプレッドシートは、簡単なデータの確認や個人的なデータの追跡には適していますが、例えば、チームメンバー間のデータを収集するには非常に不向きです。

よくある使用例として、マネージャーが自分のチームが取り組んでいるさまざまなプロジェクトを追跡する必要がある場合があります。マネージャーは、重要なデータ要素を含むスプレッドシートを作成しました。しかし、チームが成長した現在、スプレッドシートの更新を管理することは不可能になりつつあり、単一の真実のソースを得ることはほとんど不可能になっています。

以下は、マネージャーがチームに送信しているスプレッドシートからの抜粋です：

![](images/spreadsheet.png " ")

### Napkin Design-プロジェクトのデータモデルの改善

スプレッドシートに基づいて単一のプロジェクト・タスク・テーブルを作成するのではなく、データ構造のコレクションを定義することで、関係をよりよくモデル化し、価値のある追加情報を収集することができます。

以下は、プロジェクト情報を収集するためのナプキンデザインです：

![](images/napkin.png " ")

新しいモデルでは、チームメンバーをプロジェクトに割り当てられるだけでなく、オプションでタスクやToDoに割り当てることができることにお気づきでしょうか。プロジェクトはマイルストーンを持つという概念が導入されましたが、タスクがマイルストーンに関連付けられるかどうかは任意です。さらに、ToDoとリンクがタスクに追加されました。

### 目的

- Oracle APEX Workspaceにテーブルを追加し、データを挿入する。

### あなたは何が必要ですか？

- Oracle Cloudの有料アカウント、Livelabsアカウント、または無料トライアル。
- APEXワークスペース

## タスク1：クイックSQLを開きます

1. ワークスペースにログインします。
2. **SQLワークショップ**をクリックします。
3. **SQLスクリプト**をクリックします。

   ![](images/go-sql-scripts.png " ")

4. **Quick SQL**をクリックします

   ![](images/go-quick-sql.png " ")

## タスク2：表には速記を入力します

Quick SQLは、インデントされたテキスト文書からリレーショナルデータモデルを作成するために必要なSQLを簡単に生成する方法を提供します。このツールは、SQLテーブル、トリガー、インデックス構造の作成に必要な時間と労力を削減するように設計されています。

*{注意：入力するのは、テーブルの一部と各テーブルのカラムの一部だけです。この演習は、Quick SQL の概念を学ぶためのものであり、入力の練習ではありません。完成したスクリプトは、このラボの後半で提供されます。}*

1. 最初のテーブルといくつかの列を入力します。

   クイックSQL（左ペイン）で、テーブル名を入力してください。  
   <code>Team Members</code>

   2つ以上のスペースをインデントし、いくつかの列名を入力します。  
   <code>  username</code>     
   <code>  full name</code>    
   <code>  email</code>

   ![](images/enter-team-members.png " ")

   *{注：各行を入力すると、SQL（右ペイン）は定義しているテーブルを作成するために必要なSQLで更新されます。出力が画像のようにならない場合は、ユーザー名などのカラムを正しくインデントしているかどうかを確認してください。}*

2. 2番目のテーブルといくつかの列を入力します。

   クイックSQL（左ペイン）で、最初の列にテーブル名を入力します。  
   <code>Projects</code>

   2つ以上のスペースをインデントして、列名を入力します。  
   <code>  name</code>     
   <code>  project lead</code>     
   <code>  budget</code>   
   <code>  status</code>

   ![](images/enter-projects.png " ")

## タスク3：速記を改善します

これまでのところ、いくつかの基本的なテーブルを定義し、デフォルトを使用していますが、速記に追加できる多くのディレクティブとデータ型があり、生成されたSQLを改善できます。

1. **ヘルプ**をクリックします**

   ![](images/table-directives.png " ")

2. **列のディレクティブ**をクリックします。  
   **テーブルディレクティブ**をクリックします。

   ![](images/column-directives.png " ")

3. **データ型**をクリックします。

   ![](images/data-types.png " ")

4. **ヘルプ**を閉じる。
5. クイックSQL（左ペイン）で、チームメンバーのテーブルを次のもので更新します。
    - 表：team members - **/insert 10** を追加する。 *{これは10のサンプルレコードを挿入します}*
    - 列：username - **/nn /upper** を追加する。 *{これにより、列が大文字と必須になります}*
    - 列：email -  **/nn** を追加する。

   以下のプロジェクトテーブルを更新してください。
    - 表: projects - **/insert 20** を追加する。 *{Tこれにより、20個のサンプルレコードが挿入されます。}*   
    - 列: name - **/nn** を追加する。   
    - 列: project lead -  **/references team_members** を追加する。      
    *{これにより、Team Members テーブルに外部キー関係が追加されます。}*  
    - 列: budget - **num** を追加する。 *{This will make the column numeric}*    
    - 列: status - **vc30 /nn /check ASSIGNED,IN_PROGRESS,COMPLETED** を追加する。   *{これは、必須カラムの長さを定義し、与えられた3つの値を使ってチェック制約を追加します。}*

   ![](images/set-directives.png " ")

   *{注： _username_に_/upper_を実装するためのチームメンバートリガーを確認するには、SQL（右ペイン）内で下にスクロールする必要があります。さらにスクロールダウンすると、すべての挿入ステートメントが表示されます。}*

## タスク4：子テーブルを入力します

テーブル名をインデントすることにより、新しいテーブルを上のテーブルの子テーブルとして定義でき、SQLは2つのテーブル間に外部キー関係を生成します。

1. プロジェクトに関連する子テーブルを入力します。

   クイックSQL（左ペイン）で、テーブル名と指令を入力してください。

   2つ以上のスペースをインデントして、列名とディレクティブを入力します。

   ![](images/enter-milestones.png " ")

   *{注：MilestonesテーブルのSQLには、Project_id列と、親テーブルとの外部キー関係が含まれます。プロジェクト。}*

2. プロジェクトに関連する別のチャイルドテーブルを入力します。

   クイックSQL（左ペイン）で、テーブル名と指令を入力してください。

   2つ以上のスペースをインデントして、列名とディレクティブを入力します。

   ![](images/enter-tasks.png " ")

## タスク5：設定を更新します

生成されたSQLをさらに改善するために、多数の設定を定義できます。

1. Projectsに関連する子テーブルを入力します。

    Quick SQL（左ペイン）で、Table NameとDirectiveを入力します：  
    <code>Milestones /insert 30</code>
    *{Projectsテーブルの列と同じインデントを使用します。}*

    2つ以上のスペースをインデントし、Column Namesとディレクティブを入力します：  
    <code>name /nn</code>   
    <code>due_date /nn</code> *{アンダースコアを含めない場合、カラムは_due_date_の代わりに_due_と呼ばれます。}*   
    <code>description</code>    

    ![](images/enter-milestones.png " ")

    *{注：MilestonesテーブルのSQLには、project_idカラムと親テーブルであるProjectsとの外部キー関係が含まれています。}*

2. Projectsに関連する別の子テーブルを入力します。

    Quick SQL（左ペイン）で、Table NameとDirectiveを入力します：  
    <code>Tasks /insert 100</code>  
    *{この新しいテーブルが、上のテーブルの親ではなく、Projectsの親になるように、インデントはMilestonesテーブルで使用したものと同じにする必要があります。}*

    2つ以上のスペースをインデントし、Column Namesとディレクティブを入力します：  
    <code>name /nn</code>   
    <code>assignee /references team_members</code>   
    <code>milestone id /references milestones</code>   

    ![](images/enter-tasks.png " ")

## タスク6：完全な速記でコピーします

1. クイックSQL（左ペイン）で、既存の速記のすべてを以下に置き換えます。


   ```
   <copy>
   # settings = { prefix: "hol", ondelete: "restrict", pk: "identity" }
   # date: "timestamp with local time zone"
   # auditcols: true
   # rowVersion: true

   team_members /insert 10
     username /nn /upper
     full name
     email /nn
     phone_number
     profile
     photo file
   projects /insert 20
     name /nn
     project_lead /nn /references team_members
     budget num
     status vc30 /nn /check ASSIGNED, IN-PROGRESS, COMPLETED
     completed_date
     description
     milestones /insert 30
       name /nn
       due_date /nn
       description
     tasks /insert 100
       name /nn
       assignee /references team_members
       milestone_id /references milestones
       start_date /nn
       end_date
       cost num
       description
       is_complete_yn /check Y, N
       to dos /insert 20
         todo vc(255) /nn
         assingee /references team_members
         due_date
         details
       links /insert 10
         url vc(255) /nn /lower
         name
         description

   view project_tasks projects tasks
   </copy>
   ```

   **SQLの生成** をクリックします

   ![](images/copy-paste.png " ")

   *{注：完全な省略形は、必要な設定をすべて定義しています。また、多くのテーブルでカラムが追加され、ディレクティブやデータ型も追加されます。また、ビューも定義されています。}*

## タスク7：スクリプトを実装します

この段階で、あなたはSQL文のリストを作成しました。ただし、最初にステートメントをスクリプト ファイルとして保存し、スクリプトを実行する必要があります。これにより、データベース・オブジェクトが作成され、データが挿入されます。

1. SQL（右ペイン）ツールバーで、**Save SQL Script**をクリックします。
2. [スクリプトの保存]ダイアログで、スクリプト名については、 **hol** を入力します。

   ![](images/save-script.png " ")

3. SQL（右ペイン）ツールバーで、**レビューと実行**をクリックします。

   **実行**  をクリックします。

   ![](images/run-script.png " ")

4. 実行ページで、**今すぐ実行** をクリックします。

   ![](images/lcdlab2step7part4.png " ")
5. スクリプト結果ページが表示され、処理され、成功したステートメント、エラーが表示されます。

   ![](images/results.png " ")

   *{注：217個のステートメントが処理されない場合は、Quick SQLに戻り、_Generate SQL_をクリックし、スクリプトを再保存して再度実行します。217の成功が表示されない場合は、結果内のフィードバックに表示されるエラーを確認してください。}*

## **まとめ**

これで、クイックSQLを使用して複雑なデータ構造を構築し、サンプルデータを完成させる方法を知っています。

## **謝辞**

  - **著者** - Salim Hlayel, Principle Product Manager
  - **寄稿者** - LiveLabs QA Team (Arabella Yao, Product Manager Intern | Dylan McLeod, QA Intern)
  - **最終更新者/日付** - Salim Hlayel, Principle Product Manager, November 2020
