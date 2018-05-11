---
title: 現代化雲端最佳化應用程式現有的.NET 應用程式的原因
description: 現代化現有的.NET 應用程式與 Azure 雲端和 Windows 容器 |現代化雲端最佳化應用程式現有的.NET 應用程式的原因
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/28/2018
ms.openlocfilehash: a874a742f6a5b32e15040ad0a237f0e0fa7908dc
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/10/2018
---
# <a name="reasons-to-modernize-existing-net-apps-to-cloud-optimized-applications"></a>現代化雲端最佳化應用程式現有的.NET 應用程式的原因

與雲端最佳化應用程式，您可以快速且重複地傳遞給您的客戶可靠的應用程式。 您可以基本靈活度和可靠性，延後的操作的複雜性，平台應用程式。

如果您無法取得應用程式，以便您寄送您的應用程式的時間快，行銷已逐漸發展已為目標的市場。 您可能會太晚，無論程度架構或工程應用程式。 您可能會失敗或未到達您可能會完整，因為無法同步處理應用程式傳遞市場的需求。

連續商務創新的需要將開發和作業團隊推送限制。 您需要在連續商務創新的靈活度的唯一方式是種技術，例如容器和特定的雲端最佳化應用程式原則的應用程式。

營收是當組織能夠建置並管理是雲端最佳化的應用程式，它可以更快地將解決方案放在客戶手中，使上市時，它們相關的新概念。

## <a name="cloud-optimized-application-principles-and-tenets"></a>雲端最佳化應用程式原則和原則 

在雲端中的增強功能主要是將焦點放在符合兩個目標： 降低成本，並透過改善靈活度，改善商務成長。 以簡化程序並減少摩擦，當您發行及提供應用程式時，可達到這些目標。

如果您可以在敏捷式軟體開發的方式開發應用程式、 從其他內部部署應用程式，並再放開，部署時，自動調整規模雲端最佳化的應用程式是監視和疑難排解您的應用程式在雲端中。

索引鍵是*靈活度*。 您就無法出貨與敏捷性除非絕對最小值減少到生產任何部署和開發/測試環境問題。 容器 (具體而言，Docker 既定的標準) 和受管理的服務是專用於此用途而設計。

若要達到靈活度，您也需要自動發行至雲端中的可擴充平台的 CI/CD 管線為基礎的 DevOps 程序。 CI/CD 平台 （例如 Visual Studio Team Services 或 Jenkins） 部署至可擴充且具恢復功能雲端平台 （例如 Azure 應用程式服務、 Azure Service Fabric 或 Azure Kubernetes 服務） 是針對達到雲端中的靈活度的關鍵技術。

下列清單描述主要的要件或雲端最佳化應用程式的作法。 請注意，您可以採用的全部或僅部分這些原則，以漸進式或累加式方法：

-   **容器**。 容器可讓您包含應用程式本身的應用程式相依性。 得以大幅減少當您部署到生產環境或預備環境中測試時，可能會遇到的問題數目。 最後，容器會改善應用程式傳遞的靈活度。

-   **有彈性且可擴充的雲端**。 雲端提供受管理、 彈性、 可擴充且彈性的平台。 這些特性是取得成本增強功能，並在持續傳遞提供高度可用且可靠的應用程式的基礎。 受管理的服務受管理與資料庫一樣，受管理快取服務 (CaaS)，以及受管理存放裝置是減緩您的應用程式的維護成本的基本部分。

-   **監視**。 您不能有可靠的應用程式，而不需要偵測及診斷例外狀況和應用程式的效能問題的好方法。 您必須取得透過應用程式效能管理和即時分析的可執行的洞察力。

-   **DevOps 文化特性和持續傳遞**。 採用 DevOps 作法需要文化特性變更所在小組不再適用於獨立定址接收器。 CI/CD 管線可能會開發和 IT 營運團隊之間，支援容器及 CI/CD 的工具所增加的共同作業時。

圖 4-2 顯示主要的選擇性功能的雲端最佳化應用程式。 實作多個核心，readier 您的應用程式將會成功滿足客戶的期望。

> ![主要的方針建置雲端最佳化應用程式](./media/image2.png)
>
> **圖 4-2.** 主要的方針建置雲端最佳化應用程式

若要簡而言之，雲端最佳化應用程式是建置和管理應用程式一種方法採用雲端運算時使用的容器、 受管理的雲端基礎結構、 恢復功能的應用程式技術，組合的模型，監視、 持續傳遞和 DevOps，完全不需要 rearchitect 及重新設定現有的應用程式。

您的組織可以採用這些技術和方法逐漸增加。 您不需要對所有項目，一次。 您可以採用它們以累加的方式，取決於企業優先順序與使用者需求。

## <a name="benefits-of-a-cloud-optimized-application"></a>雲端最佳化應用程式的優點

您可以轉換現有的應用程式的雲端最佳化應用程式 （而不需要重新架構或程式碼撰寫），以取得下列優點：

-   **成本的降低，因為受管理的基礎結構由雲端提供者處理**。 雲端最佳化應用程式使用雲端的方塊外彈性、 自動調整和高可用性，以取得的雲端優點。 優點不只與計算功能 （Vm 和容器），但也會取決於在雲端中，資源 DBaaS、 CaaS 和任何基礎結構等應用程式可能需要進行。

-   **具有恢復功能的應用程式和基礎結構**。 當您移轉至雲端時，您需要採用暫時性失敗;在雲端中，將會失敗。 此外，雲端基礎結構和硬體都"取代，「 可增加暫時性的停機時間的機會。 同時，內部的雲端功能，會實作恢復功能，以及自動復原某些應用程式開發技術讓它更容易從雲端中未預期的失敗中復原。

-   **應用程式效能的深入解析**。 雲端監視工具，像是 Azure Application Insights 提供健康情況管理、 記錄和通知的視覺效果。 稽核記錄檔會讓您輕鬆地偵錯及稽核，可靠的雲端應用程式的基本應用程式。

-   **應用程式可攜性，敏捷式軟體開發部署**。 容器 （根據 Docker 引擎 Linux 或 Windows 容器） 可提供最佳的解決方案，以避免雲端鎖定應用程式。 使用容器、 Docker 主機，以及多雲端 orchestrators，您可以輕鬆地從一個環境移動，或到另一個雲端。 容器會消除通常會部署到任何環境 （階段/測試/生產環境） 中發生的摩擦。

所有這些優點最終提供端對端應用程式生命週期的索引鍵的成本大幅降低。

在下列章節中，這些優點的詳細資料，說明，且已連結到特定技術。

>[!div class="step-by-step"]
[上一頁](index.md)
[下一頁](microsoft-technologies-in-cloud-optimized-applications.md)