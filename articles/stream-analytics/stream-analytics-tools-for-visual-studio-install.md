---
title: Visual Studio の Azure Stream Analytics ツールの設定
description: この記事では、Visual Studio の Azure Stream Analytics ツールのインストールの要件と設定方法について説明します。
services: stream-analytics
author: su-jie
ms.author: sujie
manager: kfile
ms.reviewer: jasonh
ms.service: stream-analytics
ms.topic: conceptual
ms.date: 09/19/2017
ms.openlocfilehash: 511658fc0e2b480987455007dac5f55cd7850feb
ms.sourcegitcommit: 5b2ac9e6d8539c11ab0891b686b8afa12441a8f3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2018
---
# <a name="install-azure-stream-analytics-tools-for-visual-studio"></a>Visual Studio の Azure Stream Analytics ツールのインストール
Azure Stream Analytics ツールでは、Visual Studio 2017、2015、2013 がサポートされるようになりました。 このドキュメントでは、ツールのインストールとアンインストールの方法を説明します。

ツールの使用について詳しくは、[Visual Studio の Azure Stream Analytics ツール](https://docs.microsoft.com/azure/stream-analytics/stream-analytics-tools-for-visual-studio)に関する記事をご覧ください。

## <a name="install"></a>Install
### <a name="visual-studio-2017"></a>Visual Studio 2017
* [Visual Studio 2017 (15.3 以降)](https://www.visualstudio.com/) をダウンロードします。 Enterprise (Ultimate/Premium)、Professional、Community の各エディションがサポートされています。 Express エディションはサポートされていません。 
* Stream Analytics ツールは、Visual Studio 2017 の **[Azure の開発]** および **[データの保存と処理]** ワークロードの一部です。 Visual Studio のインストールの一環として、この 2 つのワークロードのいずれかを有効にします。

次のように **[データの保存と処理]** ワークロードを有効にします。

![[データの保存と処理] ワークロード](./media/stream-analytics-tools-for-vs/stream-analytics-tools-for-vs-2017-install-01.png)

次のように **[Azure の開発]** ワークロードを有効にします。

![[Azure の開発] ワークロード](./media/stream-analytics-tools-for-vs/stream-analytics-tools-for-vs-2017-install-02.png)


### <a name="visual-studio-2013-2015"></a>Visual Studio 2013、2015
* Visual Studio 2015 または Visual Studio 2013 Update 4 をインストールします。 Enterprise (Ultimate/Premium)、Professional、Community の各エディションがサポートされています。 Express エディションはサポートされていません。 
* [Web Platform Installer](http://www.microsoft.com/web/downloads/platform.aspx) を使用して、Microsoft Azure SDK for .NET バージョン 2.7.1 以上をインストールします。
* [Visual Studio の Azure Stream Analytics ツール](http://aka.ms/asatoolsvs)をインストールします。



## <a name="update"></a>プライマリの

### <a name="visual-studio-2017"></a>Visual Studio 2017
新しいバージョンの通知が Visual Studio の通知に表示されます。 

### <a name="visual-studio-2013-2015"></a>Visual Studio 2013、2015
インストールされている Visual Studio の Stream Analytics ツールによって、新しいバージョンが自動的に確認されます。 最新バージョンをインストールするにはポップアップ ウィンドウの指示に従います。 


## <a name="uninstall"></a>アンインストール

### <a name="visual-studio-2017"></a>Visual Studio 2017
Visual Studio インストーラーをダブルクリックし、**[変更]** を選択します。 **[データの保存と処理]** ワークロードまたは **[Azure の開発]** ワークロードから、**[Azure Data Lake および Stream Analytics ツール]** チェック ボックスをオフにします。

### <a name="visual-studio-2013-2015"></a>Visual Studio 2013、2015
コントロール パネルに移動し、**Microsoft Azure Data Lake and Stream Analytics tools for Visual Studio** をアンインストールします。





