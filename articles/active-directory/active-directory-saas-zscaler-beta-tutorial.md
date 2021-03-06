---
title: 'チュートリアル: Azure Active Directory と Zscaler Beta の統合 | Microsoft Docs'
description: Azure Active Directory と Zscaler Beta の間でシングル サインオンを構成する方法について説明します。
services: active-directory
documentationCenter: na
author: jeevansd
manager: mtillman
ms.assetid: 56b846ae-a1e7-45ae-a79d-992a87f075ba
ms.service: active-directory
ms.workload: identity
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: article
ms.date: 07/12/2017
ms.author: jeedes
ms.openlocfilehash: cd53b00726681571a04356303607915a127a2e9e
ms.sourcegitcommit: b6319f1a87d9316122f96769aab0d92b46a6879a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/20/2018
ms.locfileid: "34354032"
---
# <a name="tutorial-azure-active-directory-integration-with-zscaler-beta"></a>チュートリアル: Azure Active Directory と Zscaler Beta の統合

このチュートリアルでは、Zscaler Beta と Azure Active Directory (Azure AD) を統合する方法について説明します。

Zscaler Beta と Azure AD の統合には、次の利点があります。

- Zscaler Beta にアクセスするユーザーを Azure AD で管理できます
- ユーザーが Azure AD アカウントで Zscaler Beta に自動的にサインオン (シングル サインオン) できるように設定することが可能です
- 1 つの中央サイト (Azure Portal) でアカウントを管理できます

SaaS アプリと Azure AD の統合の詳細については、「[Azure Active Directory のアプリケーション アクセスとシングル サインオンとは](manage-apps/what-is-single-sign-on.md)」をご覧ください。

## <a name="prerequisites"></a>前提条件

Zscaler Beta と Azure AD の統合を構成するには、次の項目が必要です。

- Azure AD サブスクリプション
- ZScaler Beta でのシングル サインオンが有効なサブスクリプション

> [!NOTE]
> このチュートリアルの手順をテストする場合、運用環境を使用しないことをお勧めします。

このチュートリアルの手順をテストするには、次の推奨事項に従ってください。

- 必要な場合を除き、運用環境は使用しないでください。
- Azure AD の評価環境がない場合は、[こちら](https://azure.microsoft.com/pricing/free-trial/)から 1 か月の評価版を入手できます。

## <a name="scenario-description"></a>シナリオの説明
このチュートリアルでは、テスト環境で Azure AD のシングル サインオンをテストします。 このチュートリアルで説明するシナリオは、主に次の 2 つの要素で構成されています。

1. ギャラリーからの Zscaler Beta の追加
2. Azure AD シングル サインオンの構成とテスト

## <a name="adding-zscaler-beta-from-the-gallery"></a>ギャラリーからの Zscaler Beta の追加
Azure AD への Zscaler Beta の統合を構成するには、管理対象の SaaS アプリ一覧に Zscaler Beta をギャラリーから追加する必要があります。

**ギャラリーから Zscaler Beta を追加するには、次の手順に従います。**

1. **[Azure Portal](https://portal.azure.com)** の左側のナビゲーション ウィンドウで、**[Azure Active Directory]** アイコンをクリックします。 

    ![Active Directory][1]

2. **[エンタープライズ アプリケーション]** に移動します。 次に、**[すべてのアプリケーション]** に移動します。

    ![[アプリケーション]][2]
    
3. 新しいアプリケーションを追加するには、ダイアログの上部にある **[新しいアプリケーション]** をクリックします。

    ![[アプリケーション]][3]

4. 検索ボックスに、「**Zscaler Beta**」と入力します。

    ![Azure AD のテスト ユーザーの作成](./media/active-directory-saas-zscaler-beta-tutorial/tutorial_zscalerbeta_search.png)

5. 結果ウィンドウで **Zscaler Beta** を選択し、**[追加]** をクリックして、アプリケーションを追加します。

    ![Azure AD のテスト ユーザーの作成](./media/active-directory-saas-zscaler-beta-tutorial/tutorial_zscalerbeta_addfromgallery.png)

##  <a name="configuring-and-testing-azure-ad-single-sign-on"></a>Azure AD シングル サインオンの構成とテスト
このセクションでは、"Britta Simon" というテスト ユーザーに基づいて、Zscaler Beta で Azure AD のシングル サインオンを構成し、テストします。

シングル サインオンを機能させるには、Azure AD ユーザーに対応する Zscaler Beta ユーザーが Azure AD で認識されている必要があります。 言い換えると、Azure AD ユーザーと Zscaler Beta の関連ユーザーの間で、リンク関係が確立されている必要があります。

Zscaler Beta で、Azure AD の **[ユーザー名]** の値を **[Username]\(ユーザー名\)** の値として割り当ててリンク関係を確立します。

Zscaler Beta で Azure AD のシングル サインオンを構成してテストするには、次の構成要素を完了する必要があります。

1. **[Configuring Azure AD Single Sign-On](#configuring-azure-ad-single-sign-on)** - ユーザーがこの機能を使用できるようにします。
2. **[プロキシ設定の構成](#configuring-proxy-settings)** - Internet Explorer でプロキシ設定を構成します
3. **[Azure AD のテスト ユーザーの作成](#creating-an-azure-ad-test-user)** - Britta Simon で Azure AD のシングル サインオンをテストします。
4. **[Zscaler Beta のテスト ユーザーの作成](#creating-a-zscaler-beta-test-user)** - Zscaler Beta で Britta Simon に対応するユーザーを作成し、Azure AD の Britta Simon にリンクさせます。
5. **[Azure AD テスト ユーザーの割り当て](#assigning-the-azure-ad-test-user)** - Britta Simon が Azure AD のシングル サインオンを使用できるようにします。
6. **[シングル サインオンのテスト](#testing-single-sign-on)** - 構成が機能するかどうかを確認します。

### <a name="configuring-azure-ad-single-sign-on"></a>Azure AD シングル サインオンの構成

このセクションでは、Azure Portal で Azure AD のシングル サインオンを有効にして、Zscaler Beta アプリケーションでシングル サインオンを構成します。

**Zscaler Beta で Azure AD シングル サインオンを構成するには、次の手順に従います。**

1. Azure Portal の **Zscaler Beta** アプリケーション統合ページで、**[シングル サインオン]** をクリックします。

    ![[Configure Single Sign-On]][4]

2. **[シングル サインオン]** ダイアログで、**[モード]** として **[SAML ベースのサインオン]** を選択し、シングル サインオンを有効にします。
 
    ![[Configure Single Sign-On]](./media/active-directory-saas-zscaler-beta-tutorial/tutorial_zscalerbeta_samlbase.png)

3. **[Zscaler Beta のドメインと URL]** セクションで、次の手順に従います。

    ![[Configure Single Sign-On]](./media/active-directory-saas-zscaler-beta-tutorial/tutorial_zscalerbeta_url.png)

    [サインオン URL] ボックスに、ユーザーが Zscaler Beta アプリケーションへのサインオンに使用する URL を入力します。

    > [!NOTE] 
    > この値は実際のサインオン URL で更新する必要があります。 この値を取得するには、[Zscaler Beta クライアント サポート チーム](https://www.zscaler.com/company/contact)に問い合わせてください。 

4. **[SAML 署名証明書]** セクションで、**[証明書 (Base64)]** をクリックし、コンピューターに証明書ファイルを保存します。

    ![[Configure Single Sign-On]](./media/active-directory-saas-zscaler-beta-tutorial/tutorial_zscalerbeta_certificate.png) 

5. **[保存]** ボタンをクリックします。

    ![[Configure Single Sign-On]](./media/active-directory-saas-zscaler-beta-tutorial/tutorial_general_400.png)

6. **[Zscaler Beta 構成]** セクションで、**[Zscaler Beta の構成]** をクリックして、**[サインオンの構成]** ウィンドウを開きます。 **[クイック リファレンス]** セクションから **SAML シングル サインオン サービスの URL** をコピーします。

    ![[Configure Single Sign-On]](./media/active-directory-saas-zscaler-beta-tutorial/tutorial_zscalerbeta_configure.png) 

7. 別の Web ブラウザー ウィンドウで、Zscaler Beta 企業サイトに管理者としてログインします。

8. 上部のメニューで **[管理]** をクリックします。
   
    ![Administration](./media/active-directory-saas-zscaler-beta-tutorial/ic800206.png "Administration")

9. **[管理者とロールの管理]** をクリックし、**[ユーザーと認証の管理]** をクリックします。   
            
    ![ユーザーと認証の管理](./media/active-directory-saas-zscaler-beta-tutorial/ic800207.png "Manage Users & Authentication")

10. **[組織の認証オプションの選択]** セクションで、次の手順を実行します。   
                
    ![Authentication](./media/active-directory-saas-zscaler-beta-tutorial/ic800208.png "Authentication")
   
    a.[サインオン URL] ボックスに、次のパターンを使用して、ユーザーが RightScale アプリケーションへのサインオンに使用する URL を入力します。 **[SAML シングル サインオンを使用した認証]** を選択します。

    b. **[SAML シングル サインオン パラメーターの構成]** をクリックします。

11. **[SAML シングル サインオン パラメーターの構成]** ダイアログ ページで、次の手順に従い、**[完了]** をクリックします

    ![シングル サインオン](./media/active-directory-saas-zscaler-beta-tutorial/ic800209.png "Single Sign-On")
    
    a.[サインオン URL] ボックスに、次のパターンを使用して、ユーザーが RightScale アプリケーションへのサインオンに使用する URL を入力します。 Azure Portal からコピーした **SAML シングル サインオン サービス URL** の値を、**[URL of the SAML Portal to which users are sent for authentication]\(ユーザーが認証に送られる SAML ポータルの URL\)** ボックスに貼り付けます。
    
    b. **[ログイン名を含む属性]** ボックスに「**NameID**」と入力します。
    
    c. ダウンロードした証明書をアップロードするには、 **[Zscaler pem]** をクリックします。
    
    d. **[SAML 自動プロビジョニングを有効にする]** を選択します。

12. **[ユーザー認証の構成]** ダイアログ ページで、次の手順に従います。

    ![Administration](./media/active-directory-saas-zscaler-beta-tutorial/ic800210.png "Administration")
    
    a.[サインオン URL] ボックスに、次のパターンを使用して、ユーザーが RightScale アプリケーションへのサインオンに使用する URL を入力します。 **[Save]** をクリックします。

    b. **[今すぐ認証する]** をクリックします。

## <a name="configuring-proxy-settings"></a>プロキシ設定の構成
### <a name="to-configure-the-proxy-settings-in-internet-explorer"></a>Internet Explorer でプロキシ設定を構成するには

1. **Internet Explorer**を開始します。

2. **[ツール]** メニューの **[インターネット オプション]** を選択し、**[インターネット オプション]** ダイアログを開きます。   
    
     ![インターネット オプション](./media/active-directory-saas-zscaler-beta-tutorial/ic769492.png "Internet Options")

3. **[接続]** タブをクリックします。   
  
     ![接続](./media/active-directory-saas-zscaler-beta-tutorial/ic769493.png "Connections")

4. **[LAN の設定]** をクリックして **[LAN の設定]** ダイアログを開きます。

5. [プロキシ サーバー] セクションで、次の手順を実行します。   
   
    ![プロキシ サーバー](./media/active-directory-saas-zscaler-beta-tutorial/ic769494.png "Proxy server")

    a.[サインオン URL] ボックスに、次のパターンを使用して、ユーザーが RightScale アプリケーションへのサインオンに使用する URL を入力します。 **[LAN にプロキシ サーバーを使用する]** をオンにします。

    b. [アドレス] ボックスに「**gateway.zscalerbeta.net**」と入力します。

    c. [ポート] ボックスに「 **80**」と入力します。

    d. **[ローカル アドレスにはプロキシ サーバーを使用しない]** を選択します。

    e. **[OK]** をクリックして **[ローカル エリア ネットワーク (LAN) の設定]** ダイアログを閉じます。

6. **[OK]** をクリックして **[インターネット オプション]** ダイアログを閉じます。

> [!TIP]
> アプリのセットアップ中、[Azure Portal](https://portal.azure.com) 内で上記の手順の簡易版を確認できるようになりました。  **[Active Directory] の [エンタープライズ アプリケーション]** セクションからこのアプリを追加した後、**[シングル サインオン]** タブをクリックし、一番下の **[構成]** セクションから組み込みドキュメントにアクセスするだけです。 組み込みドキュメント機能の詳細については、[Azure AD の組み込みドキュメント]( https://go.microsoft.com/fwlink/?linkid=845985)に関するページを参照してください。
> 

### <a name="creating-an-azure-ad-test-user"></a>Azure AD のテスト ユーザーの作成
このセクションの目的は、Azure Portal で Britta Simon というテスト ユーザーを作成することです。

![Azure AD ユーザーの作成][100]

**Azure AD でテスト ユーザーを作成するには、次の手順に従います。**

1. **Azure Portal** の左側のナビゲーション ウィンドウで、**[Azure Active Directory]** アイコンをクリックします。

    ![Azure AD のテスト ユーザーの作成](./media/active-directory-saas-zscaler-beta-tutorial/create_aaduser_01.png) 

2. **[ユーザーとグループ]** に移動し、**[すべてのユーザー]** をクリックして、ユーザーの一覧を表示します。
    
    ![Azure AD のテスト ユーザーの作成](./media/active-directory-saas-zscaler-beta-tutorial/create_aaduser_02.png) 

3. ダイアログの上部にある **[追加]** をクリックして、**[ユーザー]** ダイアログを開きます。
 
    ![Azure AD のテスト ユーザーの作成](./media/active-directory-saas-zscaler-beta-tutorial/create_aaduser_03.png) 

4. **[ユーザー]** ダイアログ ページで、次の手順を実行します。
 
    ![Azure AD のテスト ユーザーの作成](./media/active-directory-saas-zscaler-beta-tutorial/create_aaduser_04.png) 

    a.[サインオン URL] ボックスに、次のパターンを使用して、ユーザーが RightScale アプリケーションへのサインオンに使用する URL を入力します。 **[名前]** ボックスに「**BrittaSimon**」と入力します。

    b. **[ユーザー名]** ボックスに BrittaSimon の**電子メール アドレス**を入力します。

    c. **[パスワードを表示]** を選択し、**[パスワード]** の値をメモします。

    d. **Create** をクリックしてください。
 
### <a name="creating-a-zscaler-beta-test-user"></a>Zscaler Beta テスト ユーザーの作成

Azure AD ユーザーが Zscaler Beta にログインできるようにするには、そのユーザーを Zscaler Beta にプロビジョニングする必要があります。 Zscaler Beta の場合、プロビジョニングは手動で行います。

### <a name="to-configure-user-provisioning-perform-the-following-steps"></a>ユーザー プロビジョニングを構成するには、次の手順に従います。

1. **Zscaler Beta** テナントにログインします。

2. **[管理]** をクリックします。   
   
    ![Administration](./media/active-directory-saas-zscaler-beta-tutorial/ic781035.png "Administration")

3. **[ユーザー管理]** をクリックします。   
        
     ![Add](./media/active-directory-saas-zscaler-beta-tutorial/ic781036.png "Add")

4. **[ユーザー]** タブで、**[追加]** をクリックします。
      
    ![Add](./media/active-directory-saas-zscaler-beta-tutorial/ic781037.png "Add")

5. [ユーザーの追加] セクションで、次の手順を実行します。
        
    ![ユーザーの追加](./media/active-directory-saas-zscaler-beta-tutorial/ic781038.png "Add User")
   
    a.[サインオン URL] ボックスに、次のパターンを使用して、ユーザーが RightScale アプリケーションへのサインオンに使用する URL を入力します。 プロビジョニングする有効な Azure AD アカウントの **[UserID]\(ユーザー ID\)**、**[User Display Name]\(ユーザー表示名\)**、**[Password]\(パスワード\)**、**[Confirm Password]\(確認パスワード\)** を入力し、**[Groups]\(グループ\)** と **[Department]\(部署\)** を選びます。

    b. **[Save]** をクリックします。

> [!NOTE]
> Zscaler Beta から提供されている他の Zscaler Beta ユーザー アカウント作成ツールまたは API を使用して、Azure AD ユーザー アカウントをプロビジョニングできます。

### <a name="assigning-the-azure-ad-test-user"></a>Azure AD テスト ユーザーの割り当て

このセクションでは、Britta Simon に Zscaler Beta へのアクセスを許可することで、このユーザーが Azure シングル サインオンを使用できるようにします。

![ユーザーの割り当て][200] 

**Britta Simon を Zscaler Beta に割り当てるには、次の手順を実行します。**

1. Azure Portal でアプリケーション ビューを開き、ディレクトリ ビューに移動します。次に、**[エンタープライズ アプリケーション]** に移動し、**[すべてのアプリケーション]** をクリックします。

    ![ユーザーの割り当て][201] 

2. アプリケーションの一覧で、**[Zscaler Beta]** を選択します。

    ![[Configure Single Sign-On]](./media/active-directory-saas-zscaler-beta-tutorial/tutorial_zscalerbeta_app.png) 

3. 左側のメニューで **[ユーザーとグループ]** をクリックします。

    ![ユーザーの割り当て][202] 

4. **[追加]** ボタンをクリックします。 次に、**[割り当ての追加]** ダイアログで **[ユーザーとグループ]** を選択します。

    ![ユーザーの割り当て][203]

5. **[ユーザーとグループ]** ダイアログで、ユーザーの一覧から **[Britta Simon]** を選択します。

6. **[ユーザーとグループ]** ダイアログで **[選択]** をクリックします。

7. **[割り当ての追加]** ダイアログで **[割り当て]** ボタンをクリックします。
    
### <a name="testing-single-sign-on"></a>シングル サインオンのテスト

このセクションでは、アクセス パネルを使用して Azure AD のシングル サインオン構成をテストします。

アクセス パネルで Zscaler Beta のタイルをクリックすると、自動的に Zscaler Beta アプリケーションにサインオンします。
アクセス パネルの詳細については、[アクセス パネルの概要](active-directory-saas-access-panel-introduction.md)に関する記事を参照してください。

## <a name="additional-resources"></a>その他のリソース

* [SaaS アプリと Azure Active Directory を統合する方法に関するチュートリアルの一覧](active-directory-saas-tutorial-list.md)
* [Azure Active Directory のアプリケーション アクセスとシングル サインオンとは](manage-apps/what-is-single-sign-on.md)

<!--Image references-->

[1]: ./media/active-directory-saas-zscaler-beta-tutorial/tutorial_general_01.png
[2]: ./media/active-directory-saas-zscaler-beta-tutorial/tutorial_general_02.png
[3]: ./media/active-directory-saas-zscaler-beta-tutorial/tutorial_general_03.png
[4]: ./media/active-directory-saas-zscaler-beta-tutorial/tutorial_general_04.png

[100]: ./media/active-directory-saas-zscaler-beta-tutorial/tutorial_general_100.png

[200]: ./media/active-directory-saas-zscaler-beta-tutorial/tutorial_general_200.png
[201]: ./media/active-directory-saas-zscaler-beta-tutorial/tutorial_general_201.png
[202]: ./media/active-directory-saas-zscaler-beta-tutorial/tutorial_general_202.png
[203]: ./media/active-directory-saas-zscaler-beta-tutorial/tutorial_general_203.png

