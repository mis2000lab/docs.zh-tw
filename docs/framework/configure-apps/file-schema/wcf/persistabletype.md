---
title: '&lt;persistableType&gt;'
ms.date: 03/30/2017
ms.assetid: e5425fe6-523a-4076-aab4-2c2515b1d830
ms.openlocfilehash: 23724957398ed1ade2c81a3932e9773d7cf4c642
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="ltpersistabletypegt"></a>&lt;persistableType&gt;
指定所有永久性型別。  
  
 \<system.ServiceModel>  
\<comContracts>  
\<comContract >  
  
## <a name="syntax"></a>語法  
  
```xml  
<comContracts>  
  <comContract>  
      <persistableTypes>  
         <persistableType id="string"  
            name="string">  
         </persistableType>  
      </persistableTypes>  
  </comContract>  
</comContracts>  
```  
  
## <a name="type"></a>類型  
 `Type`  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|id|必要屬性，其中包含的字串可指定永久性類別的唯一識別碼。|  
|name|選擇性屬性，其中包含的字串可指定永久性類別的名稱。|  
  
### <a name="child-elements"></a>子項目  
 無  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<persistableTypes>](../../../../../docs/framework/configure-apps/file-schema/wcf/persistabletypes.md)|`persistableType` 項目的集合。|  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ServiceModel.Configuration.ComPersistableTypeElementCollection>  
 <xref:System.ServiceModel.Configuration.ComPersistableTypeElement>  
 [\<comContracts>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)  
 [整合 COM 應用程式](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)  
 [如何：設定 COM+ 服務設定](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)
