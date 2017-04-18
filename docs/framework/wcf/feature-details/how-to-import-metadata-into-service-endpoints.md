---
title: "HOW TO：將中繼資料匯入服務端點 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b69dbe20-92a1-4911-89d8-ffbc3dad4663
caps.latest.revision: 13
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 13
---
# HOW TO：將中繼資料匯入服務端點
本主題將說明如何將中繼資料匯入服務端點的集合中，以及使用在 [使用者入門](../../../../docs/framework/wcf/samples/getting-started-sample.md) 中定義的服務。  本主題將示範如何建立用戶端應用程式，從服務匯入中繼資料，然後在服務上呼叫 `Add` 方法。  
  
### 將中繼資料匯入服務端點  
  
1.  請宣告 <xref:System.ServiceModel.EndpointAddress> 物件，並使用服務之中繼資料交換 \(MEX\) 位址的統一資源識別元 \(URI\) 來初始化該物件。  
  
     [!code-csharp[UE_ImportMetadata#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#0)]  
  
2.  建立 <xref:System.ServiceModel.Description.MetadataExchangeClient>，在 MEX 位址中傳遞，然後呼叫 <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A>。  這會從服務擷取中繼資料。  
  
     [!code-csharp[UE_ImportMetadata#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#1)]  
  
3.  建立 <xref:System.ServiceModel.Description.WsdlImporter>，在先前擷取的中繼資料中傳遞，然後呼叫 <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A>。  這會產生 <xref:System.ServiceModel.Description.ContractDescription> 物件的集合。  您也可以呼叫 <xref:System.ServiceModel.Description.WsdlImporter.ImportAllEndpoints%2A> 或 <xref:System.ServiceModel.Description.WsdlImporter.ImportAllBindings%2A>，視您的需要而定。  
  
     [!code-csharp[UE_ImportMetadata#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#2)]  
  
    > [!NOTE]
    >  在您匯入中繼資料之後，將無法建立用戶端通道或匯出中繼資料。  這是因為此時沒有可用的型別資訊。  實際與服務互動或匯出中繼資料需要型別資訊。  如果要產生型別資訊，您需要產生程式碼，如步驟 4 和 5 中所示。  或者，您可以使用 <xref:System.ServiceModel.Description.MetadataResolver> 協助程式類別。  [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [HOW TO：使用 MetadataResolver 來動態取得繫結中繼資料](../../../../docs/framework/wcf/feature-details/how-to-use-metadataresolver-to-obtain-binding-metadata-dynamically.md).  
  
4.  產生各個合約的型別資訊。  
  
     [!code-csharp[UE_ImportMetadata#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#3)]  
  
5.  現在您可以使用此資訊。  下列範例會產生 C\# 原始程式碼。  
  
     [!code-csharp[UE_ImportMetadata#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#4)]  
  
## 請參閱  
 [中繼資料](../../../../docs/framework/wcf/feature-details/metadata.md)   
 [使用者入門](../../../../docs/framework/wcf/samples/getting-started-sample.md)