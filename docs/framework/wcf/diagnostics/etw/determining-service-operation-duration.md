---
title: 判斷服務作業持續時間
ms.date: 03/30/2017
ms.assetid: e8a93a2c-2c20-48b3-8986-57e90e9aa908
ms.openlocfilehash: 8c86ccc09979071e0678be792f4937d526e23fa7
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
---
# <a name="determining-service-operation-duration"></a>判斷服務作業持續時間
如果分析追蹤已啟用 Windows Communication Foundation (WCF) 應用程式中，服務作業執行期間可以輕鬆地檢查事件記錄檔來判斷。  本主題示範如何判斷服務作業完成所需的時間。  
  
### <a name="determining-service-operation-execution-duration"></a>判斷服務作業執行持續時間  
  
1.  開啟事件檢視器，依序按一下**啟動**，**執行**，並輸入`eventvwr.exe`。  
  
2.  如果您尚未啟用分析追蹤，展開**Applications and Services Logs**， **Microsoft**， **Windows**，**應用程式伺服器-應用程式**. 選取**檢視**，**顯示分析與偵錯記錄檔**。 以滑鼠右鍵按一下**分析**選取**啟用記錄**。 讓 [事件檢視器] 保持開啟狀態，如此在服務作業執行之後就能檢視追蹤。  
  
3.  接下來，開啟包含服務專案，以及與該服務互動的用戶端專案的 WCF 應用程式。  您可以建立這類應用程式遵循[入門教學課程](../../../../../docs/framework/wcf/getting-started-tutorial.md)。  如果您有安裝 WCF 範例，您可以開啟[入門](../../../../../docs/framework/wcf/samples/getting-started-sample.md)，其中包含已完成本教學課程中建立的專案。  
  
4.  執行伺服器應用程式按**F5**。 執行用戶端應用程式，以滑鼠右鍵按一下**用戶端**專案，並選取**偵錯**，**開始新執行個體**。  
  
5.  在 [事件檢視器] 中，重新整理分析記錄檔並依照 [事件 ID] 排序事件。  尋找事件識別碼[214-operationcompleted，接續](../../../../../docs/framework/wcf/diagnostics/etw/214-operationcompleted.md)。  這些事件將顯示已完成的作業，以及作業的持續時間。  下列事件會顯示 Add 作業的持續時間。  
  
    ```Output  
    An OperationInvoker completed the call to the 'Add' method.  The method call duration was '3' ms.  
    ```
