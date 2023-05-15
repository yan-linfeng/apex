# アプリケーションを再生します

## 紹介

このラボでは、アプリケーションを再生成して、開発の出発点をより良いものにします。

マイルストーンのレポートとフォームを確認すると、4つの項目しかないことがわかります。次に、エンドユーザーと話したところ、あるプロジェクトで多くのマイルストーンを一度に入力したいことがよくあることがわかりました。

![](images/milestones.png " ")

そのため、現在のレポートやフォームをインタラクティブグリッドに置き換えることが望ましいと考えられます。インタラクティブグリッドは、スプレッドシートに似ていて、1つのページで複数のレコードを管理することができます。

今回生成したアプリケーションでは、追加の開発が行われていないため、現在のアプリケーションを削除し、新しいアプリケーションを再生成するのが最も迅速かつ簡単です。

*{注：アプリケーションで開発が行われていた場合、再生成時に変更内容が失われます。これを避けるには、ページの作成ウィザードを使用して新しいインタラクティブグリッドページを作成し、既存のレポートとフォームを削除して、新しいページを指すようにナビゲーションリストを変更します。}*

推定時間：5分

### 目的

- 開発者に優しい環境のアプリケーションを再生します
- アプリケーションのステップを更新します

### 前提条件

- Oracle Cloudの有料アカウント、Livelabsアカウント、または無料トライアル。
- 一つのAPEXアプリケーション

## タスク1: 既存のアプリケーションの削除
同じ名前の2つのアプリケーションが存在するのを避けるために、たった今生成したアプリケーションを削除することが重要です。

1. アプリケーションのホームページに戻ります。  

    APEX App Builderを使用してこのアプリを実行した場合、画面下部にDeveloper Toolbarが表示されます。     
    *{注意:アプリに直接ログインするエンドユーザーはこのツールバーを表示しません。*

    Developer Toolbarで**Application xxxxx**をクリックします。

    ![](images/dev-toolbar.png " ")

    または、適切なブラウザータブやウィンドウを選択することにより、手動でブラウザのAPEX App Builderタブに戻ることもできます。

2. 開発環境から、アプリケーションのホームページで、右パネルのTasksの下にある**Delete Application**をクリックします。

    ![](images/delete-app.png " ")  

3.**Permanently Delete Now** をクリックします。

    ![](images/perm-delete-now.png " ")


## タスク2: ブループリントの読み込み 
Create Application Wizardを使用すると、開発者は以前に生成されたアプリケーション定義である_Blueprints_を読み込むことができます。この機能を利用すると、前のProjectsアプリケーションブループリントを読み込み、マイルストーンページを修正してからアプリを再生成できます。

1. App Builderのホームページから、**App Builder**メニューを開き、**Create**をクリックします。

    ![](images/go-create-app.png " ")  

2. Create an Applicationページで、**New Application** をクリックします。  

3. Create App Wizardで、**Load Blueprint**をクリックします。

    Quick Projectsの場合は、**Load**をクリックします。

    ![](images/load-blueprint.png " ")

## タスク3: マイルストーンページの更新
元のページを再読み込みしたので、今度は古いマイルストーンページを削除し、新しいページタイプを追加し、新しいページを並べ替えるだけのことです。

1. Create an Applicationページで、Pagesの下のMilestonesの横にある**Edit**をクリックします。  

    Add Report Pageで、**Delete**をクリックします。

    ![](images/delete-page.png " ")  

2. **Add Page**をクリックします。  

    Add Pageダイアログで、**Interactive Grid**をクリックします。

    ![](images/select-ig.png " ")

3. Add Interactive Grid Pageダイアログで、以下を入力します。
    - Page Name - **Milestones**と入力します。
    - Table or View - **HOL_MILESTONES**を選択します。  

    **Add Page**をクリックします。

    ![](images/add-page.png " ")

4. **Milestones – Interactive Grid**ページのハンバーガーをマウスオーバーしているときにマウスをクリックして押し続けます。  
    Projectsの下までドラッグします。マウスを離します。

    ![](images/drag-page.png " ")  

5. 新しいアプリケーションを生成するには、**Create Application**をクリックします。  

## タスク4: 新しいアプリケーションの実行

1. Page Designerで、**Run Application**をクリックします。

2. 新しいアプリケーションでMilestonesに移動し、ページを確認します。

    既存のレコードをダブルクリックするか、Add Rowをクリックして新しいレコードを挿入します。

    ![](images/new-page.png " ")

    *{注意:レコードはInteractive Grid内で直接挿入、更新、削除できます。ウィザードはProjectsの値のリストを生成し、期日はポップアップカレンダーを使用し、他の2つのフィールドはページに直接データを維持するためのテキスト領域を使用します。}*
    
## **まとめ**

ここで、青写真を利用して以前のアプリケーション定義を作成アプリケーションウィザードにロードする方法を知っています。

## **謝辞**

  - **著者** - Salim Hlayel, Principle Product Manager
  - **寄稿者** - LiveLabs QA Team (Arabella Yao, Product Manager Intern | Dylan McLeod, QA Intern)
  - **最終更新者/日付** - Salim Hlayel, Principle Product Manager, November 2020
