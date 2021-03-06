---
title: 'チュートリアル: Azure Active Directory と Palo Alto Networks - Admin UI の統合 | Microsoft Docs'
description: Azure Active Directory と Palo Alto Networks - Admin UI の間でシングル サインオンを構成する方法について説明します。
services: active-directory
documentationCenter: na
author: jeevansd
manager: mtillman
ms.reviewer: joflore
ms.assetid: a826eaec-15af-4c85-8855-8a3374d1efb9
ms.service: active-directory
ms.workload: identity
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: article
ms.date: 11/01/2017
ms.author: jeedes
ms.openlocfilehash: aa3366810a40b004fe510cb2909f8da0f3513ddb
ms.sourcegitcommit: b6319f1a87d9316122f96769aab0d92b46a6879a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/20/2018
ms.locfileid: "34350340"
---
# <a name="integrate-azure-active-directory-with-palo-alto-networks---admin-ui"></a>Azure Active Directory と Palo Alto Networks - Admin UI の統合

このチュートリアルでは、Azure Active Directory (Azure AD) を Palo Alto Networks - Admin UI と 統合する方法について説明します。

Azure AD を Palo Alto Networks - Admin UI と 統合すると、次のメリットが得られます。

- Palo Alto Networks - Admin UI にアクセスする Azure AD ユーザーを制御できます。
- ユーザーが自分の Azure AD アカウントで自動的に Palo Alto Networks - Admin UI にサインオン (シングル サインオンすなわち SSO) できるようにします。
- 1 つの中央サイト (Azure Portal) でアカウントを管理できます。

SaaS アプリと Azure AD の統合の詳細については、「[Azure Active Directory のアプリケーション アクセスとシングル サインオンとは](manage-apps/what-is-single-sign-on.md)」をご覧ください。

## <a name="prerequisites"></a>前提条件

Azure AD と Palo Alto Networks - Admin UI の統合を構成するには、次のアイテムが必要です。

- Azure AD サブスクリプション
- Palo Alto Networks 次世代ファイアウォールまたは Panorama (ファイアウォールの一元管理システム)

> [!NOTE]
> このチュートリアルの手順をテストする場合、運用環境を*使用しない*ことをお勧めします。

このチュートリアルの手順をテストするには、次の推奨事項に従います。

- 必要な場合を除き、運用環境は使用しないでください。
- Azure AD の評価環境がない場合は、[1 か月の評価版を入手できます](https://azure.microsoft.com/pricing/free-trial/)。

## <a name="scenario-description"></a>シナリオの説明
このチュートリアルでは、テスト環境で Azure AD のシングル サインオンをテストします。 

このチュートリアルで説明するシナリオは、主に次の 2 つの要素で構成されています。

* ギャラリーからの Palo Alto Networks - Admin UI の追加
* Azure AD シングル サインオンの構成とテスト

## <a name="add-palo-alto-networks---admin-ui-from-the-gallery"></a>ギャラリーからの Palo Alto Networks - Admin UI の追加
Azure AD と Palo Alto Networks - Admin UI の統合を構成するには、次の手順を実行してギャラリーから管理対象 SaaS アプリの一覧に Palo Alto Networks - Admin UI を追加します。

1. [Azure Portal](https://portal.azure.com) の左側のウィンドウで、**[Azure Active Directory]** を選択します。 

    ![Azure Active Directory のボタン][1]

2. **[エンタープライズ アプリケーション]** > **[すべてのアプリケーション]** の順に選択します。

    ![[エンタープライズ アプリケーション] ウィンドウ][2]
    
3. 新しいアプリケーションを追加するには、ウィンドウの上部にある **[新しいアプリケーション]** ボタンを選びます。

    ![[新しいアプリケーション] ボタン][3]

4. 検索ボックスに「**Palo Alto Networks - Admin UI**」と入力し、結果リストで **[Palo Alto Networks - Admin UI]** を選択してから、**[追加]** を選択します。

    ![結果一覧の Palo Alto Networks - Admin UI](./media/active-directory-saas-paloaltoadmin-tutorial/tutorial_step4-add-from-the-gallery.png)

## <a name="configure-and-test-azure-ad-single-sign-on"></a>Azure AD シングル サインオンの構成とテスト

このセクションでは、"Britta Simon" というテスト ユーザーに基づいて、Palo Alto Networks - Admin UI で Azure AD のシングル サインオンを構成し、テストします。

シングル サインオンを機能させるには、Azure AD ユーザーに対応する Palo Alto Networks - Admin UI ユーザーが Azure AD で識別される必要があります。 言い換えると、Azure AD ユーザーと Palo Alto Networks - Admin UI の同一ユーザーの間で、リンク関係が確立されている必要があります。

リンク関係を確立するには、Azure AD の "*ユーザー名*" の値を Palo Alto Networks - Admin UI の *Username* として割り当ててします。

Palo Alto Networks - Admin UI で Azure AD のシングル サインオンを構成してテストするには、次の 5 つのセクションで構成要素を完成させます。

### <a name="configure-azure-ad-single-sign-on"></a>Azure AD シングル サインオンの構成

次の手順を実行し、Azure Portal で Azure AD のシングル サインオンを有効にして、Palo Alto Networks - Admin UI アプリケーションでシングル サインオンを構成します。

1. Azure Portal の **Palo Alto Networks - Admin UI** アプリケーション統合ページで、**[シングル サインオン]** を選択します。

    ![[シングル サインオン] リンク][4]

2. **[シングル サインオン]** ウィンドウの **[シングル サインオン モード]** ボックスで、**[SAML ベースのサインオン]** を選択します。
 
    ![[シングル サインオン] ウィンドウ](./media/active-directory-saas-paloaltoadmin-tutorial/tutorial_paloaltoadmin_samlbase.png)

3. **[Palo Alto Networks - Admin UI のドメインと URL]** の下で、次の手順を実行します。

    ![[Palo Alto Networks - Admin UI のドメインと URL] のシングル サインオン情報](./media/active-directory-saas-paloaltoadmin-tutorial/tutorial_general_show_advanced_url.png)
    
    a.[サインオン URL] ボックスに、次のパターンを使用して、ユーザーが RightScale アプリケーションへのサインオンに使用する URL を入力します。 **[サインオン URL]** ボックスに、*https://\<Customer Firewall FQDN>/php/login.php* の形式で URL を入力します。

    b. **[識別子]** ボックスに、*https://\<Customer Firewall FQDN>:443/SAML20/SP* の形式で URL を入力します。
    
    c. **[応答 URL]** ボックスに、*https://\<Customer Firewall FQDN>:443/SAML20/SP/ACS* の形式で Assertion Consumer Service (ACS) URL を入力します。
    
    > [!NOTE] 
    > 上記の値は、実際の値ではありません。 実際のサインオン URL と識別子で値を更新してください。 これらの値を取得するには、[Palo Alto Networks - Admin UI クライアント サポート チーム](https://support.paloaltonetworks.com/support)に連絡してください。 
 
4. Palo Alto Networks - Admin UI アプリケーションは、特定の形式での SAML アサーションを予期しているため、次の図に示すように要求を構成します。 以下の手順を実行して、**[アプリケーション統合]** ページの **[ユーザー属性]** セクションで属性値を管理します。
    
    ![[SAML トークン属性] リスト](./media/active-directory-saas-paloaltoadmin-tutorial/tutorial_paloaltoadmin_attribute.png)
    
   > [!NOTE]
   > 属性の値はサンプルです。*username* と *adminrole* には適切な値をマップしてください。 さらにもう 1 つオプションの属性 *accessdomain* があります。この属性は、ファイアウォールで特定の仮想システムに管理アクセスを制限する目的で使用します。
   >
        
    | 属性名 | 属性名 |
    | --- | --- |    
    | username | user.userprincipalname |
    | adminrole | customadmin |

    a.[サインオン URL] ボックスに、次のパターンを使用して、ユーザーが RightScale アプリケーションへのサインオンに使用する URL を入力します。 **[属性の追加]** を選択します。  
    
    ![[属性の追加] ボタン](./media/active-directory-saas-paloaltoadmin-tutorial/tutorial_attribute_04.png)

    **[属性の追加]** ウィンドウが開きます。

    ![[属性の追加] ウィンドウ](./media/active-directory-saas-paloaltoadmin-tutorial/tutorial_attribute_05.png)
    
    b. **[名前]** ボックスに、その行に対して表示される属性名を入力します。
    
    c. **[値]** ボックスに、その行に対して表示される属性値を入力します。
    
    d. **[OK]** を選択します。

    > [!NOTE]
    > これらの属性の詳細については、次の記事を参照してください。
    > * [Admin UI の 管理ロール プロファイル (adminrole)](https://www.paloaltonetworks.com/documentation/80/pan-os/pan-os/firewall-administration/manage-firewall-administrators/configure-an-admin-role-profile)
    > * [Admin UI の デバイス アクセス ドメイン (accessdomain)](https://www.paloaltonetworks.com/documentation/80/pan-os/web-interface-help/device/device-access-domain)
    >

5. **[SAML 署名証明書]** で、**[メタデータ XML]** を選択し、**[保存]** を選択します。

    ![[メタデータ XML] ダウンロード リンク](./media/active-directory-saas-paloaltoadmin-tutorial/tutorial_paloaltoadmin_certificate.png) 

    ![[保存] ボタン](./media/active-directory-saas-paloaltoadmin-tutorial/tutorial_general_400.png)

6. 新しいウィンドウで Palo Alto ネットワーク ファイアウォール管理 UI を管理者として開きます。

7. **[デバイス]** タブを選択します。

    ![[デバイス] タブ](./media/active-directory-saas-paloaltoadmin-tutorial/tutorial_paloaltoadmin_admin1.png)

8. 左側のウィンドウで **[SAML Identity Provider]\(SAML ID プロバイダー\)** を選択し、**[インポート]** を選択してメタデータ ファイルをインポートします。

    ![メタデータ ファイルの [インポート] ボタン](./media/active-directory-saas-paloaltoadmin-tutorial/tutorial_paloaltoadmin_admin2.png)

9. **[SAML Identify Provider Server Profile Import]\(SAML ID プロバイダー サーバー プロファイル インポート\)** ウィンドウで、次の手順を実行します。

    ![[SAML Identify Provider Server Profile Import]\(SAML ID プロバイダー サーバー プロファイル インポート\) ウィンドウ](./media/active-directory-saas-paloaltoadmin-tutorial/tutorial_paloaltoadmin_idp.png)

    a.[サインオン URL] ボックスに、次のパターンを使用して、ユーザーが RightScale アプリケーションへのサインオンに使用する URL を入力します。 **[プロファイル名]** ボックスに名前 (「**AzureAD Admin UI**」など) を入力します。
    
    b. **[Identity Provider Metadata]\(ID プロバイダー メタデータ\)** の下で **[参照]** を選択して、前の手順で Azure Portal からダウンロードした metadata.xml ファイルを選択ます。
    
    c. **[Validate Identity Provider Certificate]\(ID プロバイダー証明書の検証\)** チェック ボックスをオフにします。
    
    d. **[OK]** を選択します。
    
    e. ファイアウォールの構成を確定するには **[コミット]** を選択します。

10. 左側のウィンドウで、**[SAML Identity Provider]\(SAML ID プロバイダー\)** を選択し、前の手順で作成した SAML ID プロバイダー プロファイル (たとえば、**[AzureAD Admin UI]**) を選択します。 

    ![SAML ID プロバイダー プロファイル](./media/active-directory-saas-paloaltoadmin-tutorial/tutorial_paloaltoadmin_idp_select.png)

11. **[SAML Identify Provider Server Profile]\(SAML ID プロバイダー サーバー プロファイル\)** ウィンドウで、次の手順を実行します。

    ![[SAML Identify Provider Server Profile]\(SAML ID プロバイダー サーバー プロファイル\) ウィンドウ](./media/active-directory-saas-paloaltoadmin-tutorial/tutorial_paloaltoadmin_slo.png)
  
    a.[サインオン URL] ボックスに、次のパターンを使用して、ユーザーが RightScale アプリケーションへのサインオンに使用する URL を入力します。 **[Identity Provider SLO URL]\(ID プロバイダー SLO URL\)** ボックスで、前の手順でインポートした SLO URL を **https://login.microsoftonline.com/common/wsfederation?wa=wsignout1.0** で置き換えます。
  
    b. **[OK]** を選択します。

12. Palo Alto Networks Firewall の Admin UI で、**[デバイス]** をクリックし、**[管理者ロール]** を選択します

13. **[追加]** ボタンを選びます。 

14. **[Admin Role Profile]\(管理者ロール プロファイル\)** ウィンドウの **[名前]** ボックスに管理者ロールの名前 (たとえば **fwadmin**) を入力します。  
    この管理者ロール名は、ID プロバイダーから送信された SAML 管理者ロール属性名と一致する必要があります。 管理者ロールの名前と値は手順 4 で作成されています。

    ![Palo Alto Networks の管理者ロールの構成](./media/active-directory-saas-paloaltoadmin-tutorial/tutorial_paloaltoadmin_adminrole.png)
  
15. Firewall の Admin UI で、**[デバイス]** をクリックし、**[Authentication Profile]\(認証プロファイル\)** を選択します

16. **[追加]** ボタンを選びます。 

17. **[Authentication Profile]\(認証プロファイル\)** ウィンドウで、次の手順を実行します。 

    ![[Authentication Profile]\(認証プロファイル\) ウィンドウ](./media/active-directory-saas-paloaltoadmin-tutorial/tutorial_paloaltoadmin_authentication_profile.png)

    a.[サインオン URL] ボックスに、次のパターンを使用して、ユーザーが RightScale アプリケーションへのサインオンに使用する URL を入力します。 **[名前]** ボックスに名前 (「**AzureSAML_Admin_AuthProfile**」など) を入力します。
    
    b. **[種類]** ドロップダウン リストで、**[SAML]** を選択します。 
   
    c. **[IdP Server Profile]\(IdP サーバー プロファイル\)** ドロップダウン リストで適切な SAML ID プロバイダー サーバーのプロファイル (**[AzureAD Admin UI]** など) を選択します。
   
    c. **[Enable Single Logout]\(シングル ログアウトを有効にする\)** チェック ボックスをオンにします
    
    d. **[Admin Role Attribute]\(管理者ロール属性\)** ボックスに属性名 (「**adminrole**」など) を入力します。 
    
    e. **[詳細]** タブを選択してから、**[許可リスト]** で **[追加]** を選択します。 
    
    ![[詳細設定] タブの [追加] ボタン](./media/active-directory-saas-paloaltoadmin-tutorial/tutorial_paloaltoadmin_allowlist.png)
    
    f. **[すべて]** チェック ボックスをオンにするか、このプロファイルで認証できるユーザーとグループを選択します。  
    ユーザーが認証すると、ファイアウォールは関連するユーザー名またはグループをこの一覧のエントリと照合します。 エントリを追加しないと、ユーザーは認証できません。

    g. **[OK]** を選択します。

18. 管理者が Azure で SAML SSO を使用できるようにするには、**[デバイス]** > **[セットアップ]** を選択します。 **[セットアップ]** ウィンドウで **[管理]** タブを選択してから、**[認証の設定]** で **[設定]** ("歯車") ボタンを選択します。 

 ![[設定] ボタン](./media/active-directory-saas-paloaltoadmin-tutorial/tutorial_paloaltoadmin_authsetup.png)

19. 手順 17 で作成した SAML 認証プロファイル (たとえば、**AzureSAML_Admin_AuthProfile**) を選択します。

 ![[Authentication Profile]\(認証プロファイル\) フィールド](./media/active-directory-saas-paloaltoadmin-tutorial/tutorial_paloaltoadmin_authsettings.png)

20. **[OK]** を選択します。

21. 構成をコミットするには **[コミット]** を選択します。


> [!TIP]
> アプリのセットアップ中、上記手順の簡易版を [Azure Portal](https://portal.azure.com) でご覧いただけます。 **[Active Directory]** > **[エンタープライズ アプリケーション]** セクションにこのアプリを追加した後、**[シングル サインオン]** タブを選択し、下部にある **[構成]** セクションの組み込みドキュメントにアクセスします。 組み込みドキュメント機能の詳細については、[Azure AD の組み込みドキュメント]( https://go.microsoft.com/fwlink/?linkid=845985)に関する記事をご覧ください。
> 

### <a name="create-an-azure-ad-test-user"></a>Azure AD のテスト ユーザーの作成

このセクションでは、Azure Portal で次の手順に従って Britta Simon というテスト ユーザーを作成します。

![Azure AD のテスト ユーザーの作成][100]

1. Azure Portal の左側のウィンドウで、**[Azure Active Directory]** を選択します。

    ![[Azure Active Directory] リンク](./media/active-directory-saas-paloaltoadmin-tutorial/create_aaduser_01.png)

2. 現在のユーザーの一覧を表示するには、**[ユーザーとグループ]** > **[すべてのユーザー]** の順に選択します。

    ![[ユーザーとグループ] と [すべてのユーザー] リンク](./media/active-directory-saas-paloaltoadmin-tutorial/create_aaduser_02.png)

3. **[すべてのユーザー]** の上部にある **[追加]** を選択します。

    ![[追加] ボタン](./media/active-directory-saas-paloaltoadmin-tutorial/create_aaduser_03.png)
    
    **[ユーザー]** ウィンドウが開きます。

4. **[ユーザー]** ウィンドウで、次の手順を実行します。

    ![[ユーザー] ウィンドウ](./media/active-directory-saas-paloaltoadmin-tutorial/create_aaduser_04.png)

    a. **[名前]** ボックスに「**BrittaSimon**」と入力します。

    b. **[ユーザー名]** ボックスに、ユーザーである Britta Simon の電子メール アドレスを入力します。

    c. **[パスワードを表示]** チェック ボックスをオンにし、**[パスワード]** ボックスに表示された値を書き留めます。

    d. **[作成]** を選択します。
 
### <a name="create-a-palo-alto-networks---admin-ui-test-user"></a>Palo Alto Networks - Admin UI テスト ユーザーの作成

Palo Alto Networks - Admin UI では、Just-In-Time ユーザー プロビジョニングがサポートされます。 ユーザーが既に存在していない場合、認証の成功後に自動的にシステム内に作成されます。 ユーザーを作成する操作は不要です。

### <a name="assign-the-azure-ad-test-user"></a>Azure AD テスト ユーザーの割り当て

このセクションでは、ユーザー Britta Simon に Palo Alto Networks - Admin UI へのアクセスを許可することで、このユーザーが Azure シングル サインオンを使用できるようにします。 そのためには、次の手順を実行します。

![ユーザー ロールを割り当てる][200] 

1. Azure Portal で **[アプリケーション]** ビューを開いて**ディレクトリ** ビューに移動してから、**[エンタープライズ アプリケーション]** > **[すべてのアプリケーション]** の順に選択します。

    ![[エンタープライズ アプリケーション] と [すべてのアプリケーション] のリンク][201] 

2. **[アプリケーション]** リストで **[Palo Alto Networks - Admin UI]** を選択します。

    ![[Palo Alto Networks - Admin UI] リンク](./media/active-directory-saas-paloaltoadmin-tutorial/tutorial_paloaltoadmin_app.png)  

3. 左側のウィンドウで **[ユーザーとグループ]** を選択します。

    ![[ユーザーとグループ] リンク][202]

4. **[追加]** を選択し、**[割り当ての追加]** ウィンドウで **[ユーザーとグループ]** を選択します。

    ![[割り当ての追加] ウィンドウ][203]

5. **[ユーザーとグループ]** ウィンドウの **[ユーザー]** 一覧で、**Britta Simon** を選択します。

6. **[Select]\(選択\)** ボタンをクリックします。

7. **[割り当ての追加]** ウィンドウで **[割り当て]** を選択します。
    
### <a name="test-single-sign-on"></a>シングル サインオンのテスト

このセクションでは、アクセス パネルを使用して Azure AD のシングル サインオン構成をテストします。

アクセス パネルで Palo Alto Networks - Admin UI のタイルを選択すると、Palo Alto Networks - Admin UI アプリケーションに自動的にサインオンします。

アクセス パネルの詳細については、[アクセス パネルの概要](active-directory-saas-access-panel-introduction.md)に関する記事を参照してください。 

## <a name="additional-resources"></a>その他のリソース

* [SaaS アプリと Azure Active Directory の統合に関するチュートリアルの一覧](active-directory-saas-tutorial-list.md)
* [Azure Active Directory のアプリケーション アクセスとシングル サインオンとは](manage-apps/what-is-single-sign-on.md)



<!--Image references-->

[1]: ./media/active-directory-saas-paloaltoadmin-tutorial/tutorial_general_01.png
[2]: ./media/active-directory-saas-paloaltoadmin-tutorial/tutorial_general_02.png
[3]: ./media/active-directory-saas-paloaltoadmin-tutorial/tutorial_general_03.png
[4]: ./media/active-directory-saas-paloaltoadmin-tutorial/tutorial_general_04.png

[100]: ./media/active-directory-saas-paloaltoadmin-tutorial/tutorial_general_100.png

[200]: ./media/active-directory-saas-paloaltoadmin-tutorial/tutorial_general_200.png
[201]: ./media/active-directory-saas-paloaltoadmin-tutorial/tutorial_general_201.png
[202]: ./media/active-directory-saas-paloaltoadmin-tutorial/tutorial_general_202.png
[203]: ./media/active-directory-saas-paloaltoadmin-tutorial/tutorial_general_203.png

