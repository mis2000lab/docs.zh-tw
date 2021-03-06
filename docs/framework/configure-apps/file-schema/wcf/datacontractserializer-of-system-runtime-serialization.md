---
title: '&lt;system.runtime.serialization&gt; 的 &lt;dataContractSerializer&gt;'
ms.date: 03/30/2017
ms.assetid: d9b3d625-be3f-4768-8e0d-1b7e6929f6a8
ms.openlocfilehash: 96802100fe1b91d3e375363d2c36e239b1a1d330
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="ltdatacontractserializergt-of-ltsystemruntimeserializationgt"></a>&lt;system.runtime.serialization&gt; 的 &lt;dataContractSerializer&gt;
包含 <xref:System.Runtime.Serialization.DataContractSerializer> 的組態資料。  
  
 \<system.runtime.serialization >  
\<dataContractSerializer >  
  
## <a name="syntax"></a>語法  
  
```xml  
<configuration>  
  <system.runtime.serialization>  
    <dataContractSerializer ignoreExtensionDataObject="Boolean"  
            maxItemsInObjectGraph="Integer">  
      <declaredTypes>  
        <add type="String">  
          <knownType type="String">  
             <parameter index="Integer"  
                        type="String" />  
          </knownType>  
        </add>  
      </declaredTypes>  
    <dataContractSerializer>  
  </system.runtime.serialization>  
</configuration>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|項目|描述|  
|-------------|-----------------|  
|ignoreExtensionDataObject|布林值，該值會指定當端點序列化或還原序列化時，是否略過端點所提供的資料。 此屬性只能在 `<dataContractSerializer>` 項目下的 `<behavior>` 設定。|  
|maxItemsInObjectGraph|整數，指定要序列化或還原序列化的項目數上限。 此屬性為 65536。|  
  
### <a name="child-elements"></a>子項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<p >](../../../../../docs/framework/configure-apps/file-schema/wcf/declaredtypes.md)|包含還原序列化時，<xref:System.Runtime.Serialization.DataContractSerializer> 使用的已知型別。<br /><br /> 如需資料合約和已知型別的詳細資訊，請參閱[資料合約已知型別](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<system.runtime.serialization>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-runtime-serialization.md)|代表 <xref:System.Runtime.Serialization> 命名空間區段的根項目，而且包含用來設定 <xref:System.Runtime.Serialization.DataContractSerializer> 選項的項目。|  
  
## <a name="remarks"></a>備註  
 如需已知型別的詳細資訊，請參閱<xref:System.Runtime.Serialization.DataContractSerializer>和[資料合約已知型別](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>  
 [資料合約已知類型](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
