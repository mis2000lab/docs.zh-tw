---
title: "DataSet、DataTable 及 DataView | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6d4c4b69-8919-4224-8a65-6cca1c61b48f
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# DataSet、DataTable 及 DataView
ADO.NET <xref:System.Data.DataSet> 是以常駐記憶體表示的資料，不論內含資料來源為何，都可提供一致的關聯式程式設計模型。  <xref:System.Data.DataSet> 表示一組完整的資料，包括內含、排序和約束資料的資料表，以及資料表間的關聯性。  
  
 <xref:System.Data.DataSet> 的使用方式有幾種，可以獨立或組合套用。  您可以：  
  
-   以程式設計方式在 <xref:System.Data.DataSet> 內建立 <xref:System.Data.DataTable>、<xref:System.Data.DataRelation> 和 <xref:System.Data.Constraint>，並填入資料表的資料。  
  
-   使用 `DataAdapter`，將來自現有關聯式資料來源之資料的資料表填入 <xref:System.Data.DataSet>。  
  
-   使用 XML 載入並保存 <xref:System.Data.DataSet> 內容。  如需詳細資訊，請參閱[在 DataSet 中使用 XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)。  
  
 也可以使用 XML Web Service 傳輸強型別的 <xref:System.Data.DataSet>。  <xref:System.Data.DataSet> 的設計非常適合使用 XML Web Service 來傳輸資料。  如需 XML Web Service 的概觀，請參閱 [XML Web Services Overview](http://msdn.microsoft.com/zh-tw/9db0c7b8-bca6-462b-9be5-f5f9a7f05a4d)。  如需使用來自 XML Web Service 之 <xref:System.Data.DataSet> 的範例，請參閱 [從 XML Web Service 使用 DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/consuming-a-dataset-from-an-xml-web-service.md)。  
  
## 在本節中  
 [建立 DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-a-dataset.md)  
 說明建立 <xref:System.Data.DataSet> 執行個體的語法。  
  
 [將 DataTable 加入 DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-a-datatable-to-a-dataset.md)  
 說明如何建立資料表和資料行，並將它們加入 <xref:System.Data.DataSet>。  
  
 [加入 DataRelations](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-datarelations.md)  
 說明如何在 <xref:System.Data.DataSet> 的資料表之間建立關聯性。  
  
 [瀏覽 DataRelation](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/navigating-datarelations.md)  
 說明如何使用 <xref:System.Data.DataSet> 之資料表間的關聯性，傳回父子關係的子資料列或父資料列。  
  
 [合併 DataSet 內容](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/merging-dataset-contents.md)  
 說明如何將一個 <xref:System.Data.DataSet>、<xref:System.Data.DataTable> 或 <xref:System.Data.DataRow> 陣列的內容合併到另一個 <xref:System.Data.DataSet>。  
  
 [複製 DataSet 內容](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/copying-dataset-contents.md)  
 說明如何建立 <xref:System.Data.DataSet> 的複本，而此複本包含結構描述和指定的資料。  
  
 [處理 DataSet 的事件](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-dataset-events.md)  
 說明 <xref:System.Data.DataSet> 的事件和使用方式。  
  
 [具型別的 DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md)  
 說明何謂具型別的 <xref:System.Data.DataSet> 以及它們的建立和使用方式。  
  
 [DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 說明如何建立 <xref:System.Data.DataTable>、定義結構描述，以及管理資料。  
  
 [DataTableReader](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatablereaders.md)  
 說明如何建立及使用 <xref:System.Data.DataTableReader>。  
  
 [DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)  
 說明如何建立並使用 `DataViews`，以及使用 <xref:System.Data.DataView> 事件。  
  
 [在 DataSet 中使用 XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 說明 <xref:System.Data.DataSet> 如何將 XML 當成資料來源進行互動，包括將 <xref:System.Data.DataSet> 的內容載入和保存為 XML 資料。  
  
 [從 XML Web Service 使用 DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/consuming-a-dataset-from-an-xml-web-service.md)  
 說明如何建立可透過 <xref:System.Data.DataSet> 傳輸資料的 XML Web Service。  
  
## 相關章節  
 [ADO.NET 的新功能](../../../../../docs/framework/data/adonet/whats-new.md)  
 簡介 ADO.NET 的新功能。  
  
 [ADO.NET 概觀](../../../../../docs/framework/data/adonet/ado-net-overview.md)  
 提供 ADO.NET 的設計和元件的簡介。  
  
 [從 DataAdapter 填入資料集](../../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md)  
 明如何自資料來源載入具有資料的 **DataSet**。  
  
 [以 DataAdapter 更新資料來源](../../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)  
 說明如何將 **DataSet** 中的資料變更解析回資料來源。  
  
 [將現有條件約束加入 DataSet](../../../../../docs/framework/data/adonet/adding-existing-constraints-to-a-dataset.md)  
 說明如何將來自資料來源的主索引鍵資訊填入 **DataSet**。  
  
## 請參閱  
 [ADO.NET](../../../../../docs/framework/data/adonet/index.md)   
 [ADO.NET Managed 提供者和資料集開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)