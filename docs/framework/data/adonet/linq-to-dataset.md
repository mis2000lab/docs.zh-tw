---
title: LINQ to DataSet
ms.date: 03/30/2017
ms.assetid: 743e3755-3ecb-45a2-8d9b-9ed41f0dcf17
ms.openlocfilehash: 8a16e3fe0cea04813be50a83f906170199e78e3e
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="linq-to-dataset"></a>LINQ to DataSet
[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 可讓您更方便且更快速地查詢在 <xref:System.Data.DataSet> 物件中快取的資料。 具體來說，[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]簡化查詢，讓開發人員從程式語言本身撰寫查詢而不是使用不同的查詢語言。 這是特別適用於 Visual Studio 開發人員可以立即利用編譯時期語法檢查、 靜態型別和 IntelliSense 支援在查詢中的 Visual Studio 所提供。  
  
 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 也可用來查詢已經從一個或多個資料來源合併的資料。 這點可以實現許多資料表示和處理方式需要彈性的案例，例如本機查詢彙總的資料和在 Web 應用程式中進行中介層 (Middle Tier) 快取。 尤其，一般報表、分析和商務智慧應用程式都需要這種管理方法。  
  
 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]功能中的擴充方法主要是透過公開<xref:System.Data.DataRowExtensions>和<xref:System.Data.DataTableExtensions>類別。 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 為基礎，並使用現有[!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)]架構，而不是取代[!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)]應用程式程式碼中。 現有的 ADO.NET 2.0 程式碼將繼續在 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 應用程式中運作。 下圖將說明 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 與 [!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)] 的關聯性以及資料存放區。  
  
 ![LINQ to DataSet 根據 ADO.NET 提供者](../../../../docs/framework/data/adonet/media/linqtodataset.gif "LINQtoDataSet")  
  
## <a name="in-this-section"></a>本節內容  
 [快速入門](../../../../docs/framework/data/adonet/getting-started-linq-to-dataset.md)  
  
 [程式設計手冊](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)  
  
## <a name="reference"></a>參考資料  
 <xref:System.Data.DataTableExtensions>  
  
 <xref:System.Data.DataRowExtensions>  
  
 <xref:System.Data.DataRowComparer>  
  
## <a name="see-also"></a>另請參閱  
 [LINQ (Language-Integrated Query)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)  
 [LINQ 和 ADO.NET](../../../../docs/framework/data/adonet/linq-and-ado-net.md)  
 [ADO.NET](../../../../docs/framework/data/adonet/index.md)
