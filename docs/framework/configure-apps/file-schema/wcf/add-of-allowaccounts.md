---
title: '&lt;allowAccounts&gt; 的 &lt;add&gt;'
ms.date: 03/30/2017
ms.assetid: 763c7b1f-e7b0-4d99-a42c-4506fcb8da00
ms.openlocfilehash: 2230b8d22a14c3df5eb3aa10872246febce015e9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="ltaddgt-of-ltallowaccountsgt"></a>&lt;allowAccounts&gt; 的 &lt;add&gt;
指定裝載 WCF 服務，且已授權可連線共用服務之處理序的使用者帳戶。  
  
 \<system.serviceModel.activation>  
  
## <a name="syntax"></a>語法  
  
```xml  
<allowAccounts>  
   <add securityIdentifier="String"/>  
</allowAccounts>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|securityIdentifier|字串，指定用於識別使用者帳戶的唯一識別碼。 預設值為 LocalSystem、Administrators、NS、LS 和 IIS_USRS。|  
  
### <a name="child-elements"></a>子項目  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<allowAccounts>](../../../../../docs/framework/configure-apps/file-schema/wcf/allowaccounts.md)|包含組態項目的集合`securityIdentifier`屬性來指定裝載 WCF 服務，且已授權可連線共用服務之處理序的使用者帳戶。|  
  
## <a name="example"></a>範例  
 下列組態範例會新增使用者帳戶的五個預設識別項到此集合中。  
  
```xml  
<allowAccounts>  
   // LocalSystem account  
   <add securityIdentifier="S-1-5-18"/>  
   // LocalService account  
   <add securityIdentifier="S-1-5-19"/>  
   // Administrators account  
   <add securityIdentifier="S-1-5-20"/>  
   // Network Service account  
   <add securityIdentifier="S-1-5-32-544" />  
   // IIS_IUSRS account (Vista only)  
   <add securityIdentifier="S-1-5-32-568"/>  
</allowAccounts>  
```  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ServiceModel.Activation.Configuration.NetTcpSection.AllowAccounts%2A>  
 <xref:System.ServiceModel.Activation.Configuration.NetPipeSection.AllowAccounts%2A>  
 <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElementCollection>  
 <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElement>
