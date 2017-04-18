---
title: "&lt;webSocketSettings&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bbf97e02-8dd1-4922-acac-3cd33397b249
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# &lt;webSocketSettings&gt;
用來指定 Web 通訊端設定的組態元素。  
  
## 語法  
  
```  
  
<netHttpBinding>  
   <binding>   
       <webSocketSettings createNotificationOnConnection="boolean"  
                              disablePayloadMasking="boolean"  
                              keepAliveInterval="TimeSpan"  
                              maxPendingConnections="Integer"  
                              receiveBufferSize="Integer"  
                              sendBufferSize="Integer"  
                              subProtocol="String"  
                              transportUsage="WhenDuplex/Always/Never"/>  
   </binding>  
</netHttpBinding>  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|createNotificationOnConnection|指定是否在連接時傳送通知。|  
|disablePayloadMasking|指定是否停用 Web 通訊端遮罩。|  
|keepAliveInterval|指定保持運作的間隔。|  
|maxPendingConnections|指定服務上等待分派的連線數目上限。|  
|receiveBufferSize|指定接收緩衝區的大小。|  
|sendBufferSize|指定傳送緩衝區的大小。|  
|subProtocol|指定 Web 通訊端子通訊協定。|  
|transportUsage|指定何時要使用 Web 通訊端。|  
  
## transportUsage 屬性  
  
|值|描述|  
|-------|--------|  
|WhenDuplex|當合約為雙工合約時，使用 Web 通訊端通訊協定。|  
|永遠|不論合約為何，永遠使用 Web 通訊端通訊協定。|  
|永不|永遠不使用 Web 通訊端通訊協定。|  
  
### 子項目  
 無  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|\<netHttpBinding\>|指定 NetHttpBinding|  
  
## 範例  
 下列範例示範如何使用 \<webSocketSettings\> 項目。  
  
```xml  
<netHttpBinding>  
        <binding>  
          <webSocketSettings createNotificationOnConnection="true"  
                              disablePayloadMasking="false  
                              keepAliveInterval="00:10:00"  
                              maxPendingConnections="100"  
                              receiveBufferSize="1000"  
                              sendBufferSize="1000"  
                              subProtocol="Soap"  
                              transportUsage="WhenDuplex/Always/Never"/>  
  
        </binding>  
      </netHttpBinding>  
```  
  
## 請參閱  
 <xref:System.ServiceModel.Channels.Binding>   
 <xref:System.ServiceModel.Channels.BindingElement>   
 <xref:System.ServiceModel.BasicHttpBinding>   
 <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>   
 [繫結](../../../../../docs/framework/wcf/bindings.md)   
 [設定系統提供的繫結](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)   
 [Using Bindings to Configure Windows Communication Foundation Services and Clients](http://msdn.microsoft.com/zh-tw/bd8b277b-932f-472f-a42a-b02bb5257dfb)   
 [\<繫結\>](../../../../../docs/framework/misc/binding.md)